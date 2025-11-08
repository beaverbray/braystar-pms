# PRD: Product Strategy & Roadmap
## Collections OS - Phase 1-3 Development Plan

**Version:** 1.0
**Status:** Planning Phase
**Owner:** Product & Engineering Team
**Last Updated:** November 2025

---

## Overview

Define 18-month product roadmap from Collections OS MVP (Phase 1) through maintenance coordination (Phase 2) and lease revenue optimization (Phase 3), with clear path to full-stack PMS platform.

## Strategic Context

- **Vision:** Become the AI-native property management platform for multifamily 50-500 units
- **Strategy:** Wedge with collections → expand to operations → full platform
- **Approach:** Prove ROI in 30 days, land-and-expand, sidecar integration first
- **Differentiation:** Compliance-by-design, behavioral intelligence, low switching friction

## Goals & Success Metrics

### Phase 1 Goals (Months 0-6): Collections OS MVP
- Prove 15%+ improvement in on-time rent rate within 30 days
- 3 pilot customers, 2+ convert to paid
- Zero TCPA/FDCPA complaints
- 80%+ tenant opt-in rate for SMS reminders

### Phase 2 Goals (Months 6-12): Maintenance & Expansion
- 50% of collections customers adopt maintenance module
- 30% reduction in time-to-completion for routine maintenance
- 20% improvement in tenant satisfaction (CSAT)
- Expand to 20-30 total customers

### Phase 3 Goals (Months 12-18): Lease Revenue Optimization
- 30% of customers adopt lease revenue features
- 5%+ increase in rent revenue per unit
- Zero regulatory issues related to pricing
- Expand to 50+ total customers

## Phase 1: Collections OS (Months 0-6) — MVP

### Product Vision
A compliance-first, behavioral-science-powered collections automation platform that integrates alongside existing PMS without requiring migration.

### Core Features

#### 1. Data Ingestion & Sync
**User Story:** As a property manager, I want to import my tenant and rent ledger data so Collections OS knows who owes what.

**Features:**
- CSV import wizard (tenant list, lease terms, arrears balance)
- Bank feed integration (Plaid for real-time payment detection)
- Daily sync schedule (overnight batch process)
- Reconciliation dashboard ("PMS balance vs bank detected vs our ledger")

**Acceptance Criteria:**
- [ ] CSV import supports AppFolio, Yardi, Buildium export formats
- [ ] Plaid integration connects to bank accounts with OAuth flow
- [ ] Daily sync runs automatically at configurable time
- [ ] Reconciliation dashboard shows discrepancies with explanations

**Technical Requirements:**
- CSV parser handles common variations (commas, quotes, encodings)
- Plaid API integration with proper error handling
- Idempotent sync logic (no duplicate records)
- Data validation rules (required fields, format checks)

#### 2. Rent Ledger & Delinquency Tracking
**User Story:** As a property manager, I want to see which tenants are late and by how much so I can prioritize follow-up.

**Features:**
- Tenant balance calculation (rent due - payments received + late fees)
- Aging buckets (current, 1-30 days, 31-60 days, 61-90 days, 90+ days)
- Promised-to-pay tracking (tenant commits to date, system follows up)
- Payment plan management (installment schedules, auto-adjust balance)

**Acceptance Criteria:**
- [ ] Balance calculations match PMS exports (reconciliation)
- [ ] Aging buckets update in real-time as payments received
- [ ] Promised-to-pay reminders sent on committed date
- [ ] Payment plan installments tracked and updated

**Technical Requirements:**
- Accurate financial calculations (currency precision)
- Real-time updates from bank feed integration
- Reminder scheduling system
- Payment plan state machine

#### 3. Compliance-First Communications Engine
**User Story:** As a property manager, I want to send automated reminders that are TCPA and FDCPA compliant so I don't get sued.

**Features:**
- **Channels:** SMS (Twilio), Email (SendGrid), Voice drops (future)
- **Consent Management:**
  - Opt-in capture workflow (web form, SMS double opt-in)
  - STOP/HELP keyword handling
  - Consent audit trail
- **TCPA Compliance:**
  - Quiet hours enforcement (8am-9pm local time)
  - Message throttling (7 attempts per 7 days)
- **FDCPA Compliance:**
  - Required disclosures auto-inserted
  - Attempt frequency limits
  - Cease contact flags
- **Fair Housing:**
  - Equal treatment enforcement (same sequence for all tenants at same stage)
  - Audit trail per tenant

**Acceptance Criteria:**
- [ ] SMS sent via Twilio with STOP keyword instant processing
- [ ] Email sent via SendGrid with unsubscribe link
- [ ] No messages sent outside 8am-9pm local time
- [ ] Attempt counter prevents >7 messages in 7 days
- [ ] FDCPA disclosure auto-inserted in all collection messages
- [ ] Audit log captures all communications with timestamps

**Technical Requirements:**
- Twilio integration with webhook handling
- SendGrid integration with event tracking
- Time zone conversion for quiet hours
- Rate limiting and throttling logic
- Template system with variable substitution
- Immutable audit log

#### 4. Behavioral Collections Playbooks
**User Story:** As a property manager, I want pre-built message sequences that are proven to work so I don't have to figure it out myself.

**Features:**
- **Pre-defined Sequences:**
  - Pre-due reminder (2 days before rent due)
  - Due-date reminder (day of rent due)
  - Grace period nudge (3-5 days late)
  - Escalation sequence (7, 14, 21 days late)
- **Tone Variations:** Friendly, neutral, urgent (manager-controlled)
- **Personalization Tokens:** [Tenant name], [balance], [due date], [property name], [payment link]
- **A/B Testing:** Test message variants within same property

**Acceptance Criteria:**
- [ ] 4+ pre-built playbooks (residential, student housing, affordable)
- [ ] Manager can select tone for their properties
- [ ] Personalization tokens replaced correctly in all messages
- [ ] A/B test framework tracks variant performance

**Technical Requirements:**
- Template library with version control
- Playbook configuration UI
- Token replacement engine
- A/B test assignment and tracking

#### 5. Resident Self-Service Portal (Web)
**User Story:** As a tenant, I want to see my balance and make payments without calling the office.

**Features:**
- **No app required:** Responsive web accessed via unique link in messages
- **View:** Balance, payment history, lease details
- **Actions:**
  - Link bank account or card (Plaid + Stripe)
  - Set up payment plan (request installments, manager approves)
  - Update payment preferences (autopay, reminder frequency)
  - Manage consent (opt in/out of SMS, email)

**Acceptance Criteria:**
- [ ] Mobile-responsive design (works on phones, tablets, desktop)
- [ ] Secure authentication (magic link or password)
- [ ] Payment processing via Stripe with PCI compliance
- [ ] Bank linking via Plaid with OAuth flow
- [ ] Payment plan requests notify manager for approval

**Technical Requirements:**
- React frontend with responsive design
- Magic link authentication or password-based
- Stripe integration (tokenized payments)
- Plaid integration (bank account linking)
- Payment plan workflow with approval state

#### 6. Manager Dashboard & Analytics
**User Story:** As a property manager, I want to see if the system is working and prove ROI to my boss.

**Features:**
- **Collections KPIs:**
  - On-time rate (% paying by 5th)
  - DSO (days sales outstanding)
  - Bad debt ($ write-offs)
  - Collection rate ($ collected / $ billed)
- **Funnel Visualization:** Due → Reminded → Paid → Delinquent → Escalated
- **Property Scorecards:** Compare properties, identify outliers
- **Manager Performance:** Time saved, messages sent, response rates
- **ROI Calculator:** Baseline vs current on-time rate, $ impact, staff hours saved

**Acceptance Criteria:**
- [ ] Dashboard loads in <2 seconds
- [ ] KPIs update in real-time as payments received
- [ ] Funnel visualization shows conversion rates
- [ ] Property comparison highlights best/worst performers
- [ ] ROI calculator shows $ value created

**Technical Requirements:**
- Real-time data pipeline
- Efficient database queries with caching
- Data visualization library (Chart.js, D3)
- Export to CSV/PDF functionality

#### 7. Audit & Compliance Reporting
**User Story:** As a property manager, I want proof that I'm compliant if I'm ever audited or sued.

**Features:**
- **Immutable Message Log:** Who, what, when, channel, consent status
- **Fair Housing Report:** Confirm same sequence applied to all tenants
- **TCPA Compliance Report:** Consent status, opt-outs honored, quiet hours respected
- **FDCPA Attempt Tracking:** Frequency, escalation approval trail

**Acceptance Criteria:**
- [ ] All messages logged with full audit trail
- [ ] Reports exportable to PDF
- [ ] Fair Housing report flags anomalies
- [ ] TCPA report shows zero violations

**Technical Requirements:**
- Immutable log storage (append-only)
- Report generation engine
- PDF export functionality
- Anomaly detection logic

### Technical Stack (Phase 1)

**Backend:**
- **Framework:** Python (FastAPI or Django)
- **Database:** PostgreSQL (relational data)
- **Cache:** Redis (sessions, rate limiting)
- **Queue:** Celery or RQ (background jobs)
- **Hosting:** AWS or GCP (SOC 2 path)

**Frontend:**
- **Framework:** React (Next.js for SSR)
- **Styling:** Tailwind CSS
- **State Management:** React Context or Zustand
- **Forms:** React Hook Form

**Integrations:**
- **Payments:** Stripe (cards), Plaid (ACH/bank linking)
- **Communications:** Twilio (SMS), SendGrid (email)
- **Infrastructure:** CloudFlare (CDN/security)
- **Monitoring:** Datadog or New Relic, Sentry (errors)

**DevOps:**
- **CI/CD:** GitHub Actions
- **Container:** Docker
- **Orchestration:** Kubernetes (if scaling) or managed service
- **Secrets:** AWS Secrets Manager or Vault

### Success Metrics (Phase 1)
- [ ] 3 pilot customers (100-400 units each)
- [ ] 15%+ improvement in on-time rent rate vs baseline
- [ ] 10+ hours/week staff time saved per 100 units
- [ ] Zero TCPA/FDCPA complaints
- [ ] 80%+ tenant opt-in rate for SMS reminders
- [ ] 60-70% pilot-to-paid conversion rate

### Development Timeline (Phase 1)
- **Month 0-1:** Architecture design, technical stack setup, dev environment
- **Month 1-2:** Core features development (data ingestion, ledger, communications)
- **Month 2-3:** Resident portal, manager dashboard, compliance features
- **Month 3-4:** Testing, bug fixes, pilot preparation
- **Month 4-6:** Pilot execution with 3 customers, iteration based on feedback

---

## Phase 2: Maintenance Triage & Coordination (Months 6-12)

### Product Vision
Expand account value by solving the #2 pain point (maintenance) for existing collections customers with minimal friction.

### New Features

#### 1. Maintenance Request Intake
- SMS/email/web form submission by tenants
- Required fields: description, location, urgency, photos/videos
- AI-powered triage: categorize urgency (emergency, urgent, routine)
- Automatic routing: emergency to on-call, routine to schedule

#### 2. Vendor Dispatch & Scheduling
- Vendor directory (contact info, skills, rates, SLA)
- Work order creation and assignment
- Automated vendor notification (SMS/email with job details)
- Scheduling calendar with conflict detection
- "Resident prep" messages (what to expect, access instructions)

#### 3. Status Tracking & SLA Monitoring
- Work order lifecycle: Submitted → Assigned → In Progress → Completed → Closed
- SLA alerts: Overdue work orders, aging tickets
- Tenant status updates: "Tech dispatched, ETA 2pm," "Work completed, please confirm"
- Photo documentation required at completion

#### 4. Maintenance Analytics
- **Metrics:** Time to first response, time to completion, cost per work order, vendor performance
- **Benchmarks:** Compare properties, identify high-cost categories
- **Predictive Alerts:** "HVAC service overdue," "Water heater replacement due in 6 months"

### Integration Points
- Pull maintenance categories and vendor lists from PMS
- Push completed work orders back to PMS for accounting/invoicing

### Success Metrics (Phase 2)
- [ ] 50% of collections customers adopt maintenance module
- [ ] 30% reduction in time-to-completion for routine maintenance
- [ ] 20% improvement in tenant satisfaction (CSAT score on maintenance)
- [ ] 20-30 total customers (collections + maintenance)

### Development Timeline (Phase 2)
- **Month 6-8:** Maintenance features development
- **Month 8-10:** Testing and pilot with existing customers
- **Month 10-12:** Iteration, expansion to new customers

---

## Phase 3: Lease Revenue Optimization (Months 12-18)

### Product Vision
Increase customer LTV by helping managers maximize rent revenue compliantly without crossing into algorithmic pricing territory.

### New Features

#### 1. Lease Renewal Management
- Lease expiration calendar (60, 90, 120 day alerts)
- Automated renewal offers (manager-approved terms)
- Tenant response tracking (renewing, vacating, negotiating)
- Move-out workflow (inspection scheduling, deposit return)

#### 2. Market Rent Guidance (NOT Algorithmic Pricing)
- Rent comps from public sources (Zillow, Rentometer, CoStar)
- Portfolio internal benchmarks (unit type, location, amenities)
- Suggested range for manager consideration (NOT automated price-setting)
- Transparent methodology (no black-box algorithms)

**Critical Compliance Note:**
- ❌ Avoid RealPage-style algorithmic pricing
- ❌ No cross-landlord data sharing for price-setting
- ❌ No automated rent increases without manager approval
- ✅ Transparent, auditable guidance only

#### 3. Late Fee & Revenue Protection
- Configurable late fee rules (state-compliant maximums)
- Automatic calculation and application
- Escalation calendar (when to charge, when to escalate to legal)
- Revenue recovery tracking (fees collected vs waived)

#### 4. Owner Reporting Enhancements
- Monthly owner statements (revenue, expenses, NOI)
- Cash flow forecasts (based on lease expiration, historical collections)
- Portfolio-level reporting (aggregate across properties)
- White-label export for owner distribution

### Success Metrics (Phase 3)
- [ ] 30% of customers adopt lease revenue features
- [ ] 5%+ increase in rent revenue per unit (from better renewals, fee enforcement)
- [ ] Zero regulatory issues related to pricing
- [ ] 50+ total customers

### Development Timeline (Phase 3)
- **Month 12-15:** Lease revenue features development
- **Month 15-18:** Testing, pilot, iteration

---

## Future Expansion Opportunities (Year 2+)

### Full-Stack PMS Platform
- **Full accounting module:** Replace QuickBooks for smaller operators
- **Trust accounting:** Complete state-compliant trust account management
- **Owner portal:** White-label investor reporting and self-service
- **Leasing & marketing:** Integrate with Zillow/Apartments.com, lead management
- **Commercial/warehouse expansion:** CAM charges, TI tracking, long-lease workflows

---

## Product Development Process

### Agile Methodology
- **Sprint Length:** 2 weeks
- **Ceremonies:** Sprint planning, daily standup, sprint review, retrospective
- **Roles:** Product Owner, Scrum Master, Development Team

### Feature Prioritization Framework
- **Impact vs Effort Matrix:**
  - High Impact, Low Effort → Do first
  - High Impact, High Effort → Plan carefully
  - Low Impact, Low Effort → Quick wins
  - Low Impact, High Effort → Avoid

### Quality Standards
- **Code Review:** All PRs reviewed by ≥1 team member
- **Testing:** Unit tests (80%+ coverage), integration tests, E2E tests
- **Performance:** Page load <2s, API response <200ms
- **Security:** OWASP Top 10 prevention, dependency scanning
- **Compliance:** All features reviewed for TCPA/FDCPA/FHA compliance

---

## Dependencies

### External Dependencies
- Payment processor partnerships (Stripe, Plaid)
- Communication provider partnerships (Twilio, SendGrid)
- PMS integration requirements (AppFolio, Yardi, Buildium)
- Legal counsel for compliance review
- Customer feedback from pilots

### Internal Dependencies
- Engineering team hiring and onboarding
- Product design and UX resources
- Customer success team for pilots
- Sales and marketing alignment

---

## Risks & Mitigation

### Risk 1: Feature Creep (Trying to Build Full PMS Too Soon)
- **Mitigation:** Strict adherence to phase gates, validate each phase before next

### Risk 2: Technical Debt Accumulation
- **Mitigation:** 20% of sprint capacity for refactoring, code review standards

### Risk 3: Integration Complexity (PMS Compatibility Issues)
- **Mitigation:** Start with CSV imports, build API integrations over time

### Risk 4: Compliance Features Hurt Usability
- **Mitigation:** Design compliance as seamless features, user testing

---

## Next Steps

1. **Finalize Phase 1 feature specifications** (detailed user stories)
2. **Create technical architecture document**
3. **Hire founding engineer** (or contract development team)
4. **Set up development environment and CI/CD pipeline**
5. **Begin Phase 1 development** (Month 0-6 timeline)
