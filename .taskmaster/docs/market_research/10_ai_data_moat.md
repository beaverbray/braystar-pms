# PRD: AI Differentiation & Data Moat
## Collections OS - Sustainable Competitive Advantage Through Intelligence

**Version:** 1.0
**Status:** Planning Phase
**Owner:** Product & Data Science Team
**Last Updated:** November 2025

---

## Overview

Define AI/ML strategy, data collection framework, and long-term defensibility plan for Collections OS. Focus on building proprietary intelligence on payment behavior that creates sustainable competitive advantage and network effects.

## Strategic Context

- **Core Thesis:** AI is the *how* (makes product better), not the *why* (customers buy outcomes)
- **Positioning:** "Behavioral science + 10,000+ payment outcomes" (not "AI-powered")
- **Moat:** Proprietary data on what works (timing, channel, tone, cohort) → defensible over time
- **Compliance:** Never use AI for tenant screening, credit scoring, or automated pricing (avoid discrimination risk)

## Goals & Success Metrics

### Phase 1 Goals (Months 0-6): Rules-Based Foundation
- Prove behavioral playbooks deliver 15%+ improvement without ML
- Collect baseline data: 10,000+ payment attempts across 3 pilot properties
- Label outcomes: Reminded → Paid or Reminded → Ignored
- Build data infrastructure for supervised learning

### Phase 2 Goals (Months 6-12): Supervised Learning
- Train classifiers on timing, channel, tone, cohort
- A/B test AI-optimized vs. baseline messages
- Achieve ≥3% marginal improvement from ML (18%+ total vs. 15% baseline)
- Validate statistical significance of AI improvements

### Phase 3 Goals (Months 12-18): Generative AI & Personalization
- Deploy RAG (retrieval-augmented generation) for compliant message variations
- Personalization within Fair Housing compliance bounds
- Predictive analytics: forecast which tenants likely to go delinquent
- Expand data moat: 50,000+ labeled payment attempts

---

## The AI Stack

### Phase 1: Rules-Based with Behavioral Science (Months 0-6)

**Philosophy:** Prove value without ML first, collect data for later.

#### Behavioral Playbooks (Pre-Built)
Based on research in behavioral economics, social psychology, and debt collection best practices.

**Timing Principles:**
- Pre-due reminder (2 days before): Reduces forgetfulness, sets expectation
- Due-date reminder (day of): Urgency without pressure
- Grace period (3-5 days late): Friendly offer to help (empathy)
- Escalation (7+ days late): Firm but professional (consequences)

**Tone Variations:**
- **Friendly:** "We're here to help" (builds rapport, reduces resistance)
- **Neutral:** "Rent is due" (professional, factual)
- **Urgent:** "Action required" (creates motivation through loss aversion)

**Channel Selection (Based on Research):**
- **SMS:** 98% open rate, 90% read within 3 minutes (high urgency)
- **Email:** Lower urgency, better for detailed info (payment plan options)
- **Voice:** Highest impact but most intrusive (use sparingly)

**Social Proof & Behavioral Nudges:**
- "Most of your neighbors have already paid" (descriptive norm)
- "Pay today to avoid late fees" (loss aversion)
- "We offer flexible payment plans" (reduce barrier, offer alternative)

#### Template Library (20+ Pre-Built Templates)
**Example Templates:**

**Pre-Due Reminder (Friendly):**
> "Hi [Tenant Name], friendly reminder that rent is due on [Due Date]. You can pay online at [Link]. Questions? Reply to this message or call us at [Phone]. - [Property Name]"

**Grace Period (Empathy + Offer):**
> "Hi [Tenant Name], we noticed your rent payment is a few days late. If you're experiencing financial difficulty, we offer flexible payment plans. Contact us at [Phone] to discuss options. We're here to help! - [Property Name]"

**Escalation (Firm but Professional):**
> "[Tenant Name], URGENT: Your rent is 7 days past due. Balance: $[Balance]. Please contact us immediately at [Phone] to avoid late fees and further action. Payment link: [Link]. - [Property Name]
>
> *This is an attempt to collect a debt. Any information obtained will be used for that purpose.*"

#### A/B Testing Framework
- Test message variants within same property
- Measure: Open rate, click rate, payment rate, time to payment
- Statistical significance: ≥100 messages per variant
- Winning template becomes default (continuous optimization)

**Success Metric (Phase 1):** 15%+ improvement in on-time rent with rules-based playbooks alone.

---

### Phase 2: Supervised Learning (Months 6-12)

**Philosophy:** Use data collected in Phase 1 to train models that optimize messaging.

#### Data Collection Infrastructure

**Payment Attempt Dataset:**
Each record captures:
- **Tenant Attributes:** Days late, balance, payment history, lease terms, property
- **Message Attributes:** Channel (SMS/email), timing (day of week, time of day), tone (friendly/neutral/urgent), template ID
- **Outcome:** Paid (Y/N), time to payment (hours), amount paid, response (replied Y/N)

**Example Record:**
```json
{
  "attempt_id": "12345",
  "tenant_id": "T-6789",
  "property_id": "P-101",
  "days_late": 5,
  "balance": 1250,
  "payment_history": "3_late_last_6mo",
  "message": {
    "channel": "SMS",
    "sent_at": "2025-03-15 10:00:00",
    "day_of_week": "Friday",
    "tone": "friendly",
    "template_id": "grace_friendly_v2"
  },
  "outcome": {
    "paid": true,
    "time_to_payment_hours": 4.5,
    "amount_paid": 1250,
    "responded": true
  }
}
```

**Data Volume Targets:**
- Month 6: 10,000 payment attempts (3 pilot properties)
- Month 12: 50,000 payment attempts (50 properties)
- Year 2: 500,000 payment attempts (500 properties)

#### Pattern Recognition (Supervised Learning)

**Model 1: Timing Optimizer**
- **Input:** Tenant cohort, day of week, time of day, days late
- **Output:** Predicted response rate (probability of payment)
- **Training:** Label historical data with "paid" vs. "ignored"
- **Optimization:** Find best timing for each cohort

**Model 2: Channel Selector**
- **Input:** Tenant demographics, communication preferences, past channel response
- **Output:** Optimal channel (SMS vs. email vs. voice)
- **Training:** Logistic regression or random forest
- **Optimization:** Maximize payment rate per channel

**Model 3: Tone Classifier**
- **Input:** Tenant payment history, current delinquency severity, property culture
- **Output:** Recommended tone (friendly vs. neutral vs. urgent)
- **Training:** Gradient boosting on historical tone performance
- **Optimization:** Balance payment rate with complaint rate

**Model 4: Cohort Segmentation**
- **Input:** Tenant attributes (age, income, payment history, lease terms)
- **Output:** Predicted response pattern (e.g., "responds to empathy" vs. "needs urgency")
- **Training:** Clustering (k-means, DBSCAN) + supervised classification
- **Optimization:** Personalize playbook by cohort

#### Continuous Improvement Loop
```
Tenant late → Model selects playbook → Message sent → Outcome observed
→ Label added to dataset → Model retrains nightly → Next message improved
```

**Retraining Cadence:**
- Daily: Update predictions with new data
- Weekly: Retrain models on latest dataset
- Monthly: Evaluate model performance, A/B test new models vs. baseline
- Quarterly: Major model updates, feature engineering

#### Success Metric (Phase 2):
- **Marginal Improvement:** ≥3% from ML optimization (18%+ total vs. 15% baseline)
- **Statistical Significance:** p-value <0.05 on A/B tests
- **Complaint Rate:** <0.1% (ensure AI doesn't increase complaints)

---

### Phase 3: Generative AI & Personalization (Months 12-18)

**Philosophy:** Use LLMs to generate compliant message variations and personalize within bounds.

#### Retrieval-Augmented Generation (RAG)

**Knowledge Base:**
- **Compliance Policies:** FHA, TCPA, FDCPA do's and don'ts
- **State-Specific Rules:** Late fee caps, notice requirements, eviction timelines
- **Template Library:** Approved message variants with legal review
- **Best Practices:** Tone guidelines, Fair Housing language, empathy frameworks

**LLM Workflow:**
1. **Input:** Tenant context (days late, balance, payment history), property context
2. **RAG Retrieval:** Fetch relevant compliance rules and approved templates
3. **LLM Generation:** Generate message variation constrained by compliance rules
4. **Human Review:** Manager or compliance officer approves before deployment (initially)
5. **Automated Approval:** Once model proven, auto-approve low-risk variations

**Example Prompt (Internal):**
```
Generate a friendly rent reminder for a tenant who is 3 days late with a $1,200 balance.

Constraints:
- Must include FDCPA disclosure if debt collection applies
- Must respect TCPA quiet hours (8am-9pm local)
- Must offer payment plan option (Fair Housing equal treatment)
- Tone: Empathetic but clear about consequences
- Length: <160 characters for SMS

Retrieved Templates: [Template ID 45, 67, 89]
Retrieved Compliance Rules: [FDCPA disclosure language, Fair Housing equal treatment]
```

**Generated Output:**
> "Hi [Name], we noticed rent is 3 days past due ($1,200). We're here to help—contact us for payment plan options. Pay online: [Link]. - [Property]"

#### Personalized Messaging (Within Compliance Bounds)

**Personalization Dimensions:**
- **Tenant Payment History:** First-time late vs. chronic late payer (different tone)
- **Life Events (If Shared by Tenant):** Job loss, medical issue (empathy + options)
- **Property Culture:** Luxury vs. affordable housing (tone adjustment)
- **Communication Preference:** Prefers SMS vs. email (channel selection)

**Fair Housing Compliance:**
- ✅ Personalization based on payment behavior (OK - not protected class)
- ✅ Personalization based on tenant-declared preferences (OK - explicit consent)
- ❌ Personalization based on demographics (NOT OK - protected classes)
- ❌ Differential treatment without business justification (NOT OK - disparate impact)

**Guardrails:**
- All personalization logged for Fair Housing audit
- Equal treatment verification: same delinquency stage → same escalation sequence
- Human override logged and reviewed for bias
- Quarterly Fair Housing audit report

#### Predictive Analytics

**Use Case 1: Delinquency Forecasting**
- **Model:** Predict which current tenants likely to go delinquent next month
- **Input:** Payment history, lease terms, seasonality, property characteristics
- **Output:** Risk score (0-100) for each tenant
- **Action:** Proactive outreach (pre-due reminder to high-risk tenants)

**Use Case 2: Cash Flow Forecasting**
- **Model:** Forecast property-level cash flow based on payment patterns
- **Input:** Historical collections, lease expirations, seasonal trends
- **Output:** Expected cash flow by week (P10, P50, P90 scenarios)
- **Value:** Helps managers plan staffing, expenses, capital projects

**Use Case 3: Maintenance Need Prediction**
- **Model:** Predict upcoming maintenance issues based on work order history
- **Input:** Property age, past work orders, seasonality, unit characteristics
- **Output:** Predicted maintenance needs and costs (6-month horizon)
- **Value:** Proactive budgeting and vendor scheduling

#### Success Metric (Phase 3):
- **Improvement:** 20%+ total on-time improvement (Phase 1: 15%, Phase 2: 18%, Phase 3: 20%+)
- **Personalization Adoption:** 50%+ of customers enable personalized messaging
- **Fair Housing Compliance:** Zero violations, 100% equal treatment verified

---

## Why This Creates a Moat

### Network Effects from Proprietary Data

**After 6 Months (10 Properties, 1,000 Units):**
- ~10,000 payment attempts
- ~500 payment plans negotiated
- ~1,000 tenant interactions logged

**After 12 Months (50 Properties, 5,000 Units):**
- ~50,000 payment attempts
- ~2,500 payment plans negotiated
- ~5,000 tenant interactions logged

**After 24 Months (500 Properties, 50,000 Units):**
- ~500,000 payment attempts
- ~25,000 payment plans negotiated
- ~50,000 tenant interactions logged

### What We Learn That Competitors Can't Replicate

1. **Timing Optimization:**
   - Which day of week/time of day has highest payment rate by cohort
   - How timing varies by property type (luxury vs. affordable, urban vs. suburban)
   - Seasonal patterns (holiday delays, tax refund spikes)

2. **Channel Effectiveness:**
   - Which tenants respond better to SMS vs. email
   - How channel preference correlates with demographics and payment history
   - Optimal channel sequence (SMS first, email if no response, voice as last resort)

3. **Tone & Messaging:**
   - Which message tone increases payment rate without increasing complaints
   - How to balance urgency with empathy for different cohorts
   - Localization (language, cultural norms by geography)

4. **Escalation Strategy:**
   - Which escalation sequence minimizes bad debt without burning tenant relationships
   - When to offer payment plans vs. immediate payment
   - How to identify "can't pay" vs. "won't pay" tenants

5. **Property-Level Insights:**
   - Benchmarking across similar properties (best vs. worst performers)
   - Identifying property management best practices (what top quartile does differently)
   - Portfolio optimization (which properties to prioritize for intervention)

### Why Incumbents Can't Copy This Easily

**AppFolio/Yardi/Buildium:**
- Have payment data but treat collections as commodity feature—not investing in behavioral intelligence
- Broad product focus (dozens of features) vs. our specialized depth
- Legacy architecture makes rapid ML iteration harder
- Corporate inertia (quarterly earnings pressure, risk aversion)

**New Entrants:**
- Don't have dataset yet, can't train models from scratch
- Need 12-18 months to collect sufficient data for supervised learning
- Don't have compliance expertise or template library (years to build)
- Can't match our network effects once we have 500+ properties

**Horizontal Tools (Stripe, Twilio):**
- Have payment/messaging data but lack property management context
- Don't understand rent collection workflows, compliance, or behavioral nuances
- Not incentivized to build vertical-specific intelligence

### Defensibility Over Time

**Year 1: Rules-Based Playbooks**
- Easily copied by competitors (behavioral science is public knowledge)
- Differentiation: Execution, compliance, customer success

**Year 2: Supervised Learning Models**
- Requires dataset to train (12-18 months to collect)
- Differentiation: Proprietary data, model performance

**Year 3: Generative AI with Compliance Knowledge**
- Hard to replicate (requires compliance expertise + LLM fine-tuning + RAG infrastructure)
- Differentiation: Policy knowledge base, approved template library, Fair Housing guardrails

**Year 5: Network Effects at Scale**
- 10,000+ properties, millions of payment interactions
- Defensible moat: Data flywheel (more customers → more data → better models → more customers)

---

## What We DON'T Use AI For (Critical Compliance)

### Prohibited Use Cases

❌ **Tenant Screening:** Avoid algorithmic discrimination risk entirely
- No credit scoring, no eviction prediction, no tenant quality classification
- Leave to third-party screening services (TransUnion, CoreLogic)
- Why: HUD/DOJ actively enforcing against algorithmic screening (SafeRent settlement)

❌ **Automated Rent Pricing:** Avoid RealPage-style coordination risk
- No cross-landlord data sharing for price-setting
- No automated rent increases without manager approval
- Market rent guidance only (transparent, auditable)
- Why: DOJ investigating RealPage for antitrust violations

❌ **Automated Legal Action:** Human always in loop for eviction/collections lawsuits
- Escalation to legal requires manager approval
- No AI decides to evict or file lawsuit
- Why: High-stakes decision with tenant rights implications

❌ **Giving Legal Advice:** AI never tells tenants or managers "this is the law"
- Provide templates with disclaimer ("consult attorney")
- No interpretation of state-specific rules
- Why: Unauthorized practice of law, liability risk

### Allowed Use Cases (With Guardrails)

✅ **Collections Automation (With Compliance):**
- Behavioral playbooks for rent reminders
- Timing and channel optimization
- Tone recommendations
- Guardrails: TCPA consent, FDCPA disclosures, Fair Housing equal treatment

✅ **Payment Plan Recommendations (Manager Approval Required):**
- Suggest installment schedule based on tenant cash flow
- Manager approves or adjusts before offering to tenant
- Guardrails: Equal treatment (same criteria for all), no discrimination

✅ **Cash Flow Forecasting (Informational Only):**
- Predict property-level cash flow
- No automated actions based on forecast
- Guardrails: Manager makes decisions, AI provides information

---

## AI as Product Feature (Not Marketing Gimmick)

### Customer-Facing Language

**✅ Good (Outcome-Focused):**
- "Learns which reminders work best for your properties"
- "Automatically optimizes message timing for highest response rate"
- "Powered by behavioral science + 10,000+ payment outcomes"
- "Reduces late rent by 15% using proven playbooks"

**❌ Bad (Technology-Focused):**
- "Our AI uses machine learning algorithms to..."
- "Next-generation neural networks optimize..."
- "Artificial intelligence predicts tenant behavior..."
- "ML-powered collections platform..."

### Key Message
**AI is the *how* (makes the product better over time), not the *why* (customers buy for outcomes, not technology).**

**Positioning:**
- Phase 1: "Behavioral science-backed collections playbooks"
- Phase 2: "Continuous learning from 50,000+ payment interactions"
- Phase 3: "Personalized messaging within Fair Housing compliance"

---

## Data Infrastructure & Security

### Data Collection

**What We Collect:**
- Tenant payment attempts and outcomes (anonymized for training)
- Message performance (open rate, click rate, payment rate)
- Property characteristics (size, type, location—aggregated)
- Manager actions (playbook selections, overrides)

**What We DON'T Collect:**
- Tenant PII beyond what's needed for messaging (name, phone, email, balance)
- Protected class data (race, religion, national origin—NEVER)
- Unnecessary tenant information (employment, credit score—not our domain)

### Data Security & Privacy

**Encryption:**
- Data at rest: AES-256
- Data in transit: TLS 1.3+
- Database: Encrypted columns for PII

**Access Control:**
- Role-based access control (RBAC)
- Minimum necessary principle
- Audit logging of all data access

**Anonymization for Training:**
- Tenant IDs hashed before model training
- Aggregated data only (no individual tenant re-identification)
- Differential privacy techniques for model outputs

**Retention & Deletion:**
- Transaction data: 7 years (IRS/accounting requirement)
- Tenant PII: Delete within 30 days of move-out (unless legal hold)
- Model training data: Anonymized, retained indefinitely

**Compliance:**
- CCPA/CPRA: Data subject access requests (DSAR), deletion rights
- GLBA: Financial data safeguards, privacy notices
- SOC 2 Type II: Annual audit (target within 18 months)

---

## Technical Architecture (AI/ML Stack)

### Data Pipeline
- **Ingestion:** Real-time message events (Twilio, SendGrid webhooks)
- **Processing:** Apache Kafka or AWS Kinesis (event streaming)
- **Storage:** PostgreSQL (transactional), Snowflake or BigQuery (analytics)
- **Feature Engineering:** dbt or Airflow (transform raw data to model features)

### Model Training & Deployment
- **Training:** Scikit-learn, XGBoost, PyTorch (model frameworks)
- **Experiment Tracking:** MLflow or Weights & Biases
- **Model Serving:** FastAPI + Docker (real-time predictions)
- **A/B Testing:** Feature flags (LaunchDarkly, custom)
- **Monitoring:** Model drift detection, performance degradation alerts

### LLM Infrastructure (Phase 3)
- **LLM Provider:** OpenAI GPT-4, Anthropic Claude, or fine-tuned open-source (Llama)
- **RAG Framework:** LangChain or LlamaIndex (retrieval-augmented generation)
- **Vector Database:** Pinecone or Weaviate (policy knowledge base embeddings)
- **Guardrails:** NVIDIA NeMo Guardrails or custom compliance filters

---

## Dependencies

### External Dependencies
- Payment outcome data (requires Plaid bank feed integration)
- Messaging delivery data (Twilio, SendGrid webhooks)
- Customer feedback (NPS, pilot results, win/loss analysis)
- Compliance counsel (legal review of AI-generated templates)

### Internal Dependencies
- Product roadmap (Phase 1 rules-based must succeed before Phase 2 ML)
- Engineering resources (data infrastructure, ML engineer)
- Data scientist or ML engineer hire (Phase 2 onwards)
- Customer success feedback loop (which playbooks work best)

---

## Risks & Mitigation

### Risk 1: AI Doesn't Improve Outcomes
- **Mitigation:** Phase 1 rules-based proves value first, ML is marginal improvement (not core value prop)

### Risk 2: Compliance Violations from AI
- **Mitigation:** Human-in-the-loop for new templates, Fair Housing audit, TCPA/FDCPA guardrails

### Risk 3: Insufficient Data Quality
- **Mitigation:** Rigorous data collection, validation rules, manual labeling for training set

### Risk 4: Model Drift (Performance Degrades Over Time)
- **Mitigation:** Continuous monitoring, automated retraining, A/B testing new models vs. baseline

---

## Success Metrics Summary

### Phase 1 (Months 0-6)
- [ ] 15%+ on-time improvement with rules-based playbooks
- [ ] 10,000+ payment attempts collected and labeled
- [ ] Data infrastructure operational

### Phase 2 (Months 6-12)
- [ ] 18%+ on-time improvement with ML optimization (+3% marginal)
- [ ] Statistical significance (p <0.05) on A/B tests
- [ ] 50,000+ payment attempts in training dataset

### Phase 3 (Months 12-18)
- [ ] 20%+ on-time improvement with personalization
- [ ] Zero Fair Housing violations
- [ ] Predictive analytics deployed (delinquency forecasting)

---

## Next Steps

1. **Phase 1 Focus:** Build behavioral playbooks, prove value without ML
2. **Data Infrastructure:** Set up event pipeline, data warehouse, labeling workflow
3. **Hire ML Talent:** Data scientist or ML engineer (Month 6-9)
4. **Compliance Review:** Legal counsel approves AI strategy and guardrails
5. **Customer Communication:** Positioning AI as "how," not "why"
