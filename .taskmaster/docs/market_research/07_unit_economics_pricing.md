# PRD: Unit Economics & Pricing Strategy
## Collections OS - Business Model & Financial Projections

**Version:** 1.0
**Status:** Planning Phase
**Owner:** Finance & Strategy Team
**Last Updated:** November 2025

---

## Overview

Define pricing model, calculate unit economics, project financial performance, and establish metrics framework for Collections OS. Ensure sustainable business model with attractive LTV:CAC ratio and reasonable payback period.

## Strategic Context

- **Pricing Philosophy:** Value-based pricing aligned with ROI created (26% of value created)
- **Competitive Positioning:** Competitive with incumbents but slightly premium due to specialized value
- **Business Model:** Hybrid (platform fee + per-unit fee + optional performance fee)
- **Land-and-Expand:** Start with collections, expand to maintenance and lease revenue tools

## Goals & Success Metrics

### Primary Goals
1. **Validate pricing** with target customers (willingness to pay ≥ target price)
2. **Achieve target unit economics** (LTV:CAC ≥3:1, payback ≤12 months)
3. **Model financial projections** for Year 1-3
4. **Establish metrics dashboard** for ongoing tracking

### Success Metrics
- [ ] Pricing validated with ≥10 target customers
- [ ] LTV:CAC ≥3.5:1 (target)
- [ ] CAC payback ≤12 months
- [ ] Gross margin ≥85%
- [ ] Net revenue retention (NRR) ≥105%
- [ ] Annual churn ≤15%

## Pricing Model

### Hybrid Pricing Structure

**Component 1: Platform Fee (Per Customer)**
- **Amount:** $200-$400/month flat fee per property management company
- **Rationale:** Covers account management, compliance updates, support
- **Scales with:** Number of users, properties managed (not units—simplifies billing)
- **Tiers:**
  - Starter (50-100 units): $200/month
  - Growth (100-300 units): $300/month
  - Professional (300-500 units): $400/month
  - Enterprise (500+ units): Custom

**Component 2: Per-Unit Fee**
- **Amount:** $0.50-$1.00/unit/month
- **Rationale:** Aligns with incumbent pricing (AppFolio ~$1.40/unit, Yardi ~$1/unit)
- **Scales with:** Total units under management
- **Minimum:** Waived for pilot, $500/month for paid customers
- **Tiers:**
  - Starter (50-100 units): $0.75/unit
  - Growth (100-300 units): $0.75/unit
  - Professional (300-500 units): $0.60/unit
  - Enterprise (500+ units): $0.50/unit (volume discount)

**Component 3: Performance Fee (Optional for Pilot)**
- **Amount:** 5-10% of incremental rent collected vs baseline
- **Rationale:** Aligns incentives, reduces risk for customer
- **Caps:** Max 2X per-unit fee (avoid gouging if results exceptional)
- **Use Case:** Pilot customers hesitant to commit upfront
- **Example:**
  - Baseline on-time rate: 72%
  - Improved on-time rate: 87% (+15%)
  - Incremental rent collected: $30K/year for 200-unit property
  - Performance fee: 10% × $30K = $3K/year ($250/month)

### Pricing Tiers (Examples)

| Tier | Units | Platform Fee | Per-Unit Fee | Monthly Total | Annual Total |
|------|-------|--------------|--------------|---------------|--------------|
| **Starter** | 50-100 | $200 | $0.75 | $237-$275 | $2,850-$3,300 |
| **Growth** | 100-300 | $300 | $0.75 | $375-$525 | $4,500-$6,300 |
| **Professional** | 300-500 | $400 | $0.60 | $580-$700 | $6,960-$8,400 |
| **Enterprise** | 500+ | Custom | $0.50 | Custom | Custom |

**Add-Ons:**
- Maintenance Module: +$0.25/unit/month
- Lease Revenue Tools: +$0.25/unit/month
- Premium Support: +$100/month (dedicated account manager, priority phone support)

---

## Value-Based Pricing Rationale

### ROI Calculation for Target Customer (200 Units)

**Baseline Scenario (Before Collections OS):**
- On-time rent rate: 72% (28% late)
- Average rent per unit: $1,000/month
- Late tenants: 56 units (28% × 200)
- Average lateness: 10 days
- Cash flow impact: ~$2,500/month opportunity cost
- Staff time on collections: 15 hours/week × $25/hour = $1,500/month
- **Total Monthly Cost of Late Rent:** ~$4,000

**Improved Scenario (With Collections OS):**
- On-time rent rate: 87% (+15%)
- Late tenants: 26 units (13% × 200)
- Average lateness: 5 days (improved)
- Cash flow impact: ~$650/month
- Staff time on collections: 5 hours/week × $25/hour = $500/month
- **Total Monthly Cost of Late Rent:** ~$1,150

**Value Created:**
- Cash flow improvement: $2,500 - $650 = $1,850/month
- Staff time saved: $1,500 - $500 = $1,000/month
- **Total Monthly Value:** $2,850/month ($34,200/year)

**Our Pricing:**
- Monthly fee: $650 (Professional tier, 200 units)
- **% of Value Captured:** $650 / $2,850 = 23% (reasonable for SaaS)
- **Customer ROI:** 4.4X ($2,850 value / $650 cost)

**Competitive Comparison:**
- AppFolio: ~$560/month for 200 units (collections is just one feature)
- Our pricing: $650/month (specialized collections value)
- **Premium justified:** 16% higher but delivers 15%+ improvement in on-time rent

---

## Unit Economics Model

### Assumptions
- **Target Customer:** 200 units, Professional tier
- **Annual Contract Value (ACV):** $7,800 ($300 platform + $0.60/unit × 200 × 12)
- **Gross Margin:** 85% (software-as-a-service, minimal COGS)
- **Customer Acquisition Cost (CAC):** $4,000 (blended across channels)
- **Customer Lifetime:** 3 years (conservative)
- **Annual Churn:** 15%
- **Net Revenue Retention (NRR):** 105% (expansion from modules)

### Base Case Economics (200-Unit Customer)

| Metric | Value | Calculation |
|--------|-------|-------------|
| **Annual Contract Value (ACV)** | $7,800 | ($300 × 12) + ($0.60 × 200 × 12) |
| **Gross Revenue (Year 1)** | $7,800 | ACV |
| **COGS (15%)** | $1,170 | Messaging, payments, infrastructure |
| **Gross Profit (85%)** | $6,630 | $7,800 - $1,170 |
| **Customer Acquisition Cost (CAC)** | $4,000 | Blended across channels |
| **CAC Payback Period** | 12 months | $4,000 / ($7,800 × 85% / 12) |
| **Customer Lifetime (Years)** | 3 years | 1 / 15% churn + 5% NRR |
| **Lifetime Value (LTV)** | $21,294 | $7,800 × (1 + 1.05 + 1.10) × 85% |
| **LTV:CAC Ratio** | 5.3:1 | $21,294 / $4,000 |

**Interpretation:**
- Strong unit economics (LTV:CAC > 3:1 target)
- Acceptable payback period (12 months ≤ target)
- Healthy gross margin (85% typical for SaaS)

### Sensitivity Analysis

| Scenario | ACV | CAC | Gross Margin | Churn | NRR | Payback | LTV:CAC | Notes |
|----------|-----|-----|--------------|-------|-----|---------|---------|-------|
| **Conservative** | $6,000 | $5,000 | 80% | 20% | 100% | 16 mo | 2.9:1 | Smaller customers, higher churn |
| **Base Case** | $7,800 | $4,000 | 85% | 15% | 105% | 12 mo | 5.3:1 | 200 units avg, solid retention |
| **Optimistic** | $10,000 | $3,500 | 85% | 10% | 110% | 9 mo | 7.8:1 | Larger customers, partner channel |

**Key Takeaway:** Even in conservative scenario, unit economics are viable (LTV:CAC > 2.5:1)

---

## Cost Structure (COGS Breakdown)

### Per-Customer COGS (Monthly for 200-Unit Customer)

| Cost Category | Amount | % of Revenue | Notes |
|---------------|--------|--------------|-------|
| **Messaging (Twilio)** | $50 | 7.7% | ~1,000 SMS @ $0.05 each |
| **Email (SendGrid)** | $10 | 1.5% | ~5,000 emails @ $0.002 each |
| **Payment Processing** | $20 | 3.1% | Stripe/Plaid fees (if processing) |
| **Infrastructure (AWS)** | $15 | 2.3% | Compute, storage, bandwidth |
| **Subtotal COGS** | **$95** | **14.6%** | |
| **Revenue** | $650 | 100% | Professional tier, 200 units |
| **Gross Profit** | $555 | **85.4%** | |

**Note:** COGS scales with usage (messages sent, payments processed), not linearly with units.

### Fixed Operating Expenses (Company-Level, Year 1)

| Category | Monthly | Annual | Notes |
|----------|---------|--------|-------|
| **Salaries (Founder + Rep)** | $15K | $180K | Founder $60K, Rep $100K (from Month 6), Engineer $120K |
| **Marketing & Sales** | $10K | $120K | See GTM PRD for breakdown |
| **Legal & Compliance** | $3K | $36K | Counsel, insurance, certifications |
| **Software & Tools** | $2K | $24K | CRM, dev tools, analytics |
| **Office & Admin** | $2K | $24K | Co-working, travel, misc |
| **Total Opex** | **$32K** | **$384K** | |

**Breakeven Analysis:**
- Monthly opex: $32K
- Gross profit per customer: $555/month (200-unit avg)
- **Customers needed to break even:** 58 customers (~11,600 units)
- **MRR at breakeven:** $37,700

---

## Financial Projections (Year 1-3)

### Year 1 Projections

| Metric | Q1 | Q2 | Q3 | Q4 | Year 1 Total |
|--------|----|----|----|----|--------------|
| **New Customers** | 5 | 10 | 15 | 20 | 50 |
| **Cumulative Customers** | 5 | 15 | 30 | 50 | 50 |
| **Avg ACV** | $7,800 | $7,800 | $7,800 | $7,800 | $7,800 |
| **MRR (End of Quarter)** | $3,250 | $9,750 | $19,500 | $32,500 | $32,500 |
| **ARR (End of Quarter)** | $39K | $117K | $234K | $390K | $390K |
| **Quarterly Revenue** | $10K | $39K | $88K | $156K | $293K |
| **Quarterly COGS (15%)** | $1.5K | $5.9K | $13.2K | $23.4K | $44K |
| **Quarterly Gross Profit** | $8.5K | $33.1K | $74.8K | $132.6K | $249K |
| **Quarterly Opex** | $96K | $96K | $96K | $96K | $384K |
| **Quarterly Net Income** | -$87.5K | -$62.9K | -$21.2K | $36.6K | -$135K |

**Year 1 Summary:**
- Revenue: $293K
- Gross Profit: $249K (85% margin)
- Net Loss: -$135K (approaching profitability by Q4)
- Ending MRR: $32,500
- Ending ARR: $390K

### Year 2 Projections (Assumes Continued Growth + Module Upsells)

| Metric | Year 2 |
|--------|--------|
| **New Customers** | 100 (20% MoM growth from Year 1 momentum) |
| **Churned Customers** | -8 (15% annual churn on Year 1 cohort) |
| **Net New Customers** | 92 |
| **Cumulative Customers** | 142 |
| **Module Adoption** | 30% adopt maintenance (+$0.25/unit), 15% adopt lease revenue (+$0.25/unit) |
| **Avg ACV** | $8,580 (expansion from modules) |
| **Ending MRR** | $101,430 |
| **ARR** | $1.22M |
| **Revenue** | $900K |
| **Gross Profit** | $765K (85% margin) |
| **Opex** | $720K (hire 2 more reps, 1 engineer, 1 CSM) |
| **Net Income** | $45K (profitable!) |

### Year 3 Projections (Scale + Platform Maturity)

| Metric | Year 3 |
|--------|--------|
| **Cumulative Customers** | 250 |
| **ARR** | $2.5M |
| **Revenue** | $2.1M |
| **Gross Profit** | $1.8M (85% margin) |
| **Net Income** | $500K (profitable with healthy margin) |

---

## Expansion Revenue (Land-and-Expand)

### Year 1 Customer Journey (200-Unit Customer)

| Month | Product | MRR | ARR | Notes |
|-------|---------|-----|-----|-------|
| 1-3 | Collections OS | $650 | $7,800 | Base product |
| 6 | + Maintenance Module | $700 | $8,400 | +$50/month (+$0.25 × 200) |
| 12 | + Lease Revenue Tools | $750 | $9,000 | +$50/month (+$0.25 × 200) |
| 24 | + Premium Support | $850 | $10,200 | +$100/month |

**Net Revenue Retention Calculation:**
```
Year 1 Starting MRR (50 customers @ $650): $32,500
Year 1 Churned MRR (15% churn): -$4,875
Year 1 Expansion MRR (30% adopt maintenance, 15% adopt lease): +$4,125
Year 2 MRR from Year 1 Cohort: $31,750

NRR = $31,750 / $32,500 = 97.7% (below target due to early churn)
```

**Target NRR:** 105-110% by Year 2 (as module adoption increases and product matures)

**Expansion Levers:**
- Module adoption (maintenance, lease revenue, accounting)
- Unit count growth (customers acquire more properties)
- Pricing increases (annual 3-5% for inflation)
- Premium support upgrades
- White-label services for larger customers

---

## Pricing Validation Plan

### Research Questions
1. What is willingness to pay for 15%+ on-time rent improvement?
2. How does pricing compare to perceived value?
3. What pricing model is preferred (flat fee, per-unit, performance-based, hybrid)?
4. What is acceptable price range by customer segment (Starter, Growth, Professional)?
5. Would customers pay more for add-on modules?

### Validation Methods

#### 1. Customer Discovery Pricing Questions (Week 3-4)
Ask during discovery interviews:
- "If we could prove 15% improvement in 30 days, what would you pay per month?" (open-ended)
- "Would you prefer flat fee, per-unit pricing, or performance-based?" (preference)
- "How does $650/month for 200 units sound?" (reaction test)
- "What's your current software spend per unit?" (anchoring)

#### 2. Van Westendorp Price Sensitivity Meter (Week 5-6)
Survey 20-30 target customers with 4 questions:
- "At what price would this be too expensive?" (too expensive)
- "At what price would this be expensive but worth considering?" (expensive)
- "At what price would this be a bargain?" (cheap)
- "At what price would this be too cheap to be credible?" (too cheap)

Plot responses to find optimal price point (intersection of "too expensive" and "cheap").

#### 3. A/B Pricing Test (Pilot Phase)
Offer 3 pricing variations to pilot customers:
- **Variation A:** $200 platform + $0.75/unit (higher platform, lower per-unit)
- **Variation B:** $300 platform + $0.60/unit (balanced)
- **Variation C:** Performance-based only (10% of incremental rent)

Measure conversion rate and customer satisfaction by variation.

### Target Validation Results
- [ ] ≥70% of customers accept proposed pricing (Variation B)
- [ ] ≥50% prefer hybrid model (platform + per-unit) vs performance-only
- [ ] Acceptable price range: $500-$800/month for 200 units
- [ ] ≥80% say pricing is "fair" or "great value" vs "expensive"

---

## Metrics Dashboard

### Leading Indicators (Track Monthly)
- New customers acquired
- Average deal size (ACV)
- Customer acquisition cost (CAC) by channel
- Sales cycle length (days)
- Demo-to-pilot conversion rate
- Pilot-to-paid conversion rate

### Lagging Indicators (Track Monthly/Quarterly)
- Monthly Recurring Revenue (MRR)
- Annual Recurring Revenue (ARR)
- Gross margin (%)
- CAC payback period (months)
- LTV:CAC ratio
- Net revenue retention (NRR)
- Annual churn rate (logo and revenue)

### Customer Health Metrics (Track Monthly)
- On-time rent improvement (baseline → current)
- Staff hours saved per 100 units
- Resident opt-in rate for SMS (%)
- TCPA/FDCPA complaint rate (<0.1%)
- Net Promoter Score (NPS)
- Product adoption (active users, features used)

---

## Dependencies

### External Dependencies
- Customer discovery pricing validation data
- Competitive pricing intelligence
- Payment processor fee structures (Stripe, Plaid)
- Industry benchmarks for SaaS metrics

### Internal Dependencies
- Product roadmap (feature set for pricing tiers)
- Go-to-market strategy (channel costs inform CAC)
- Customer success resources (impact churn and NRR)

---

## Risks & Mitigation

### Risk 1: Price Too High (Low Conversion)
- **Mitigation:** Pricing validation with 20+ customers, flexible pilot pricing, performance-based option

### Risk 2: Price Too Low (Can't Cover Costs)
- **Mitigation:** Model unit economics carefully, monitor COGS, adjust pricing annually

### Risk 3: CAC Higher Than Expected
- **Mitigation:** Focus on high-ROI channels, optimize conversion funnel, referral programs

### Risk 4: Churn Higher Than Expected
- **Mitigation:** Customer success focus, regular check-ins, proactive issue resolution

### Risk 5: Module Adoption Lower Than Expected (Low NRR)
- **Mitigation:** Make modules seamless, clear value prop, bundle discounts

---

## Next Steps

1. **Conduct pricing validation** with 20 customer discovery interviews
2. **Run Van Westendorp survey** with 20-30 target customers
3. **Finalize pricing model** based on validation data
4. **Build financial model** with sensitivity scenarios
5. **Set up metrics dashboard** for ongoing tracking
