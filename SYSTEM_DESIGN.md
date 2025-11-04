# Braystar Property Management System - System Design

## Architecture Overview

### High-Level Architecture

```
┌─────────────────────────────────────────────────────────────────┐
│                        Client Applications                       │
├──────────────────────┬──────────────────────┬───────────────────┤
│   Tenant Portal      │   Owner Portal       │   Admin Portal    │
│   (React/Next.js)    │   (React/Next.js)    │   (React/Next.js) │
└──────────────────────┴──────────────────────┴───────────────────┘
                              ▼
┌─────────────────────────────────────────────────────────────────┐
│                       API Gateway / BFF                          │
│                    (GraphQL / REST API)                          │
└─────────────────────────────────────────────────────────────────┘
                              ▼
┌──────────────────────────────────────────────────────────────┐
│                    Microservices Layer                        │
├────────────────┬────────────────┬──────────────┬─────────────┤
│ Authentication │  Property Mgmt │   Payment    │  AI Services│
│    Service     │    Service     │   Service    │   Service   │
└────────────────┴────────────────┴──────────────┴─────────────┘
                              ▼
┌──────────────────────────────────────────────────────────────┐
│                      Data Layer                               │
├──────────────────┬──────────────────┬────────────────────────┤
│   PostgreSQL     │   Redis Cache    │   S3 / Object Storage │
│   (Primary DB)   │   (Sessions)     │   (Documents/Images)  │
└──────────────────┴──────────────────┴────────────────────────┘
                              ▼
┌──────────────────────────────────────────────────────────────┐
│                    External Services                          │
├─────────────┬─────────────┬─────────────┬──────────────────┤
│   Stripe    │   SendGrid  │   Twilio    │  OpenAI/Claude   │
│  (Payment)  │   (Email)   │   (SMS)     │  (AI Features)   │
└─────────────┴─────────────┴─────────────┴──────────────────┘
```

---

## Technology Stack Recommendations

### Frontend
- **Framework:** Next.js 14+ (React with App Router)
  - Server-side rendering for SEO
  - API routes for BFF pattern
  - Built-in optimization

- **UI Components:**
  - Tailwind CSS (utility-first, highly customizable)
  - Shadcn/ui or Radix UI (accessible component primitives)
  - Framer Motion (smooth animations)

- **State Management:**
  - React Query / TanStack Query (server state)
  - Zustand or Jotai (client state - lightweight)

- **Forms:**
  - React Hook Form
  - Zod (schema validation)

### Backend
- **Runtime:** Node.js 20+ with TypeScript
- **Framework:**
  - Express.js or Fastify (REST API)
  - Apollo Server (GraphQL - recommended for complex relationships)

- **ORM:** Prisma or Drizzle
  - Type-safe database access
  - Excellent TypeScript integration
  - Migration management

### Database
- **Primary:** PostgreSQL 15+
  - JSONB for flexible property metadata
  - Full-text search capabilities
  - Strong ACID compliance for financial data

- **Caching:** Redis
  - Session management
  - Rate limiting
  - Real-time features

- **Search:** Elasticsearch (optional, later phase)
  - Advanced property search
  - Full-text search across documents

### Infrastructure
- **Hosting:**
  - Vercel (Frontend - Next.js optimized)
  - AWS / Google Cloud / Railway (Backend)
  - Supabase or Neon (Managed PostgreSQL)

- **CDN:** Cloudflare
- **File Storage:** AWS S3 or Cloudflare R2
- **Monitoring:** Sentry, DataDog, or New Relic

### AI Integration
- **LLM Providers:**
  - Anthropic Claude (for complex reasoning, form filling)
  - OpenAI GPT-4 (for embeddings, simpler tasks)

- **Vector Database:** Pinecone or Weaviate
  - Document similarity search
  - RAG (Retrieval Augmented Generation)

### Payment Processing
- **Primary:** Stripe
  - Connect for marketplace model
  - Stripe Elements for PCI compliance
  - Webhooks for payment events

- **ACH/Bank Transfers:** Plaid + Stripe
- **Alternative:** Dwolla (if building custom ACH)

---

## Database Schema Overview

### Core Entities

#### Users & Authentication
```typescript
User {
  id: uuid
  email: string (unique)
  passwordHash: string
  role: enum (TENANT, OWNER, PROPERTY_MANAGER, ADMIN)
  firstName: string
  lastName: string
  phone: string
  avatar: string
  createdAt: timestamp
  updatedAt: timestamp
}

UserSession {
  id: uuid
  userId: uuid (FK)
  token: string
  expiresAt: timestamp
  deviceInfo: jsonb
}
```

#### Property Management
```typescript
Property {
  id: uuid
  ownerId: uuid (FK -> User)
  type: enum (SINGLE_FAMILY, DUPLEX, MULTI_FAMILY, COMMERCIAL)
  address: jsonb {
    street: string
    city: string
    state: string
    zip: string
    country: string
    unit?: string
  }
  details: jsonb {
    bedrooms?: number
    bathrooms?: number
    sqft?: number
    yearBuilt?: number
    amenities?: string[]
    parking?: string
  }
  status: enum (ACTIVE, INACTIVE, MAINTENANCE)
  images: string[]
  documents: string[]
  createdAt: timestamp
  updatedAt: timestamp
}

Unit {
  id: uuid
  propertyId: uuid (FK)
  unitNumber: string
  type: enum (STUDIO, 1BR, 2BR, 3BR, 4BR_PLUS)
  sqft: number
  rent: decimal
  deposit: decimal
  status: enum (VACANT, OCCUPIED, MAINTENANCE)
  amenities: jsonb
  createdAt: timestamp
  updatedAt: timestamp
}
```

#### Leases & Tenants
```typescript
Lease {
  id: uuid
  unitId: uuid (FK)
  propertyId: uuid (FK)
  startDate: date
  endDate: date
  monthlyRent: decimal
  securityDeposit: decimal
  status: enum (ACTIVE, EXPIRED, TERMINATED, PENDING)
  terms: jsonb
  documents: string[]
  createdAt: timestamp
  updatedAt: timestamp
}

LeaseTenant {
  id: uuid
  leaseId: uuid (FK)
  tenantId: uuid (FK -> User)
  isPrimary: boolean
  createdAt: timestamp
}
```

#### Payments
```typescript
Payment {
  id: uuid
  leaseId: uuid (FK)
  tenantId: uuid (FK)
  amount: decimal
  type: enum (RENT, DEPOSIT, LATE_FEE, UTILITY, OTHER)
  status: enum (PENDING, COMPLETED, FAILED, REFUNDED)
  paymentMethod: enum (ACH, CARD, CASH, CHECK)
  stripePaymentIntentId: string
  dueDate: date
  paidDate: timestamp?
  metadata: jsonb
  createdAt: timestamp
}

PaymentSchedule {
  id: uuid
  leaseId: uuid (FK)
  amount: decimal
  frequency: enum (MONTHLY, WEEKLY, BIWEEKLY)
  dayOfMonth: number
  isAutomatic: boolean
  nextPaymentDate: date
  createdAt: timestamp
}
```

#### Maintenance
```typescript
MaintenanceRequest {
  id: uuid
  propertyId: uuid (FK)
  unitId: uuid? (FK)
  requestedBy: uuid (FK -> User)
  assignedTo: uuid? (FK -> User)
  title: string
  description: text
  priority: enum (LOW, MEDIUM, HIGH, URGENT)
  status: enum (OPEN, IN_PROGRESS, COMPLETED, CANCELLED)
  category: enum (PLUMBING, ELECTRICAL, HVAC, APPLIANCE, OTHER)
  images: string[]
  cost: decimal?
  completedAt: timestamp?
  createdAt: timestamp
  updatedAt: timestamp
}
```

#### Communications
```typescript
Message {
  id: uuid
  threadId: uuid (FK)
  senderId: uuid (FK -> User)
  content: text
  aiGenerated: boolean
  metadata: jsonb {
    sentiment?: string
    intent?: string
  }
  createdAt: timestamp
}

MessageThread {
  id: uuid
  propertyId: uuid? (FK)
  leaseId: uuid? (FK)
  subject: string
  participants: uuid[] (FK -> User)
  status: enum (OPEN, CLOSED, ARCHIVED)
  createdAt: timestamp
  updatedAt: timestamp
}
```

#### AI & Automation
```typescript
AIConversation {
  id: uuid
  userId: uuid (FK)
  type: enum (FORM_FILL, COMMUNICATION, SCHEDULING, OUTREACH)
  context: jsonb
  messages: jsonb[]
  result: jsonb?
  createdAt: timestamp
}

AutomationRule {
  id: uuid
  ownerId: uuid (FK)
  name: string
  trigger: jsonb {
    type: enum (PAYMENT_DUE, LEASE_EXPIRING, MAINTENANCE, CUSTOM)
    conditions: object
  }
  action: jsonb {
    type: enum (SEND_EMAIL, SEND_SMS, CREATE_TASK, AI_OUTREACH)
    config: object
  }
  isActive: boolean
  createdAt: timestamp
}
```

---

## API Design

### Authentication Endpoints
```
POST   /api/auth/register
POST   /api/auth/login
POST   /api/auth/logout
POST   /api/auth/refresh
POST   /api/auth/forgot-password
POST   /api/auth/reset-password
GET    /api/auth/me
```

### Property Management
```
GET    /api/properties
POST   /api/properties
GET    /api/properties/:id
PUT    /api/properties/:id
DELETE /api/properties/:id
GET    /api/properties/:id/units
POST   /api/properties/:id/units
GET    /api/properties/:id/analytics
```

### Lease Management
```
GET    /api/leases
POST   /api/leases
GET    /api/leases/:id
PUT    /api/leases/:id
DELETE /api/leases/:id
POST   /api/leases/:id/renew
POST   /api/leases/:id/terminate
```

### Payment Processing
```
GET    /api/payments
POST   /api/payments
GET    /api/payments/:id
POST   /api/payments/:id/refund
GET    /api/payments/schedule
POST   /api/payments/schedule
PUT    /api/payments/schedule/:id
POST   /api/payments/setup-autopay
```

### Maintenance
```
GET    /api/maintenance
POST   /api/maintenance
GET    /api/maintenance/:id
PUT    /api/maintenance/:id
DELETE /api/maintenance/:id
POST   /api/maintenance/:id/assign
POST   /api/maintenance/:id/complete
```

### AI Services
```
POST   /api/ai/form-fill
POST   /api/ai/draft-message
POST   /api/ai/schedule-optimization
POST   /api/ai/tenant-insights
POST   /api/ai/chat
```

---

## Security Considerations

### Authentication & Authorization
- JWT tokens with short expiration (15 min access, 7 day refresh)
- HTTP-only cookies for token storage
- Role-based access control (RBAC)
- Multi-tenant data isolation

### Data Protection
- Encryption at rest (database level)
- Encryption in transit (TLS 1.3)
- PII data anonymization in logs
- GDPR/CCPA compliance

### Payment Security
- PCI DSS compliance via Stripe
- No storage of credit card data
- Webhook signature verification
- Idempotency keys for payment operations

### API Security
- Rate limiting per user/IP
- CORS configuration
- API key rotation
- Input validation and sanitization
- SQL injection prevention (ORM)
- XSS protection

---

## Scalability Considerations

### Database
- Connection pooling
- Read replicas for analytics
- Partitioning for large tables (payments, messages)
- Archival strategy for old data

### Caching Strategy
- Redis for session data (TTL: 7 days)
- API response caching (TTL: varies by endpoint)
- CDN for static assets
- Database query result caching

### Background Jobs
- Bull/BullMQ for job queue
- Scheduled tasks:
  - Payment reminders (daily)
  - Lease expiration notices (weekly)
  - Report generation (monthly)
  - Data cleanup (weekly)

### Monitoring & Observability
- Application Performance Monitoring (APM)
- Error tracking and alerting
- Database query performance
- API endpoint metrics
- User behavior analytics

---

## Mobile Strategy

### Options:
1. **Progressive Web App (PWA)**
   - Pros: Single codebase, lower cost
   - Cons: Limited native features

2. **React Native**
   - Pros: Native performance, native features
   - Cons: Additional maintenance

3. **Hybrid Approach**
   - Start with PWA
   - Build native apps later if needed

### Recommended: PWA First
- Installable on mobile devices
- Offline support for key features
- Push notifications
- Native-like experience
- Easier to maintain

---

## Development Phases

### Phase 1: MVP (3-4 months)
**Core features only:**
- User authentication (owners, tenants)
- Basic property/unit management
- Simple lease creation
- Payment processing (Stripe)
- Basic maintenance requests
- Document upload/storage
- Email notifications

### Phase 2: Enhanced Features (2-3 months)
- Advanced analytics dashboard
- Automated payment reminders
- Lease renewal workflow
- Tenant portal improvements
- Owner portal enhancements
- SMS notifications
- Search and filtering

### Phase 3: AI Integration (2-3 months)
- AI form filling assistant
- AI communication drafting
- Intelligent scheduling
- Tenant sentiment analysis
- Predictive maintenance
- Automated outreach campaigns

### Phase 4: Scale & Optimize (Ongoing)
- Performance optimization
- Advanced reporting
- Third-party integrations
- Mobile app (if needed)
- White-label capabilities
- API for external developers

---

## Recommended Project Structure

```
braystar-pms/
├── apps/
│   ├── web/                    # Next.js frontend (tenant + owner portals)
│   ├── api/                    # Backend API service
│   └── admin/                  # Admin dashboard (optional separate app)
├── packages/
│   ├── database/               # Prisma schema & migrations
│   ├── ui/                     # Shared React components
│   ├── types/                  # Shared TypeScript types
│   ├── utils/                  # Shared utilities
│   ├── ai/                     # AI service wrappers
│   └── payments/               # Payment processing logic
├── docs/
│   ├── api/                    # API documentation
│   ├── user-guides/            # User documentation
│   └── architecture/           # Architecture diagrams
├── scripts/
│   ├── seed.ts                 # Database seeding
│   └── migrate.ts              # Custom migration scripts
├── docker/
│   ├── docker-compose.yml      # Local development setup
│   └── Dockerfile              # Production container
├── .github/
│   └── workflows/              # CI/CD pipelines
├── tests/
│   ├── e2e/                    # End-to-end tests
│   └── integration/            # Integration tests
├── MARKET_RESEARCH.md
├── SYSTEM_DESIGN.md
├── package.json
├── turbo.json                  # Monorepo configuration (if using Turborepo)
└── README.md
```

---

## Next Steps

1. **Set up monorepo structure** (Turborepo or Nx)
2. **Initialize frontend** (Next.js with TypeScript)
3. **Initialize backend** (Express/Fastify with TypeScript)
4. **Set up database** (PostgreSQL with Prisma)
5. **Configure dev environment** (Docker Compose for local dev)
6. **Set up CI/CD** (GitHub Actions)
7. **Start with authentication** (first feature to build)

---

*This design will evolve as you gather market research and user feedback. Start simple, then scale.*
