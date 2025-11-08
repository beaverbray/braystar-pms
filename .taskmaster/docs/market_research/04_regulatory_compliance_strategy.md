# PRD: Regulatory Compliance Strategy
## Property Management SaaS - Compliance as Competitive Advantage

**Version:** 1.0
**Status:** Planning Phase
**Owner:** Legal & Product Team
**Last Updated:** November 2025

---

## Overview

Develop comprehensive regulatory compliance strategy that not only mitigates legal risk but positions compliance as a core product feature and competitive advantage. Focus on Fair Housing, TCPA, FDCPA, payment processing, trust accounting, and data privacy.

## Strategic Context

- **Compliance as Moat:** RealPage's regulatory troubles create opening for compliance-first alternative
- **Risk Mitigation:** Property managers hungry for solutions that reduce their compliance burden
- **Differentiation:** "Built-in compliance" as key sales message
- **Product Integration:** Compliance guardrails as features, not afterthoughts

## Goals & Success Metrics

### Primary Goals
1. **Identify all applicable regulations** for collections automation in property management
2. **Design compliance-by-design product architecture** with built-in guardrails
3. **Create compliance documentation** for customers and internal teams
4. **Establish ongoing compliance monitoring** and update processes
5. **Position compliance as competitive advantage** in sales and marketing

### Success Metrics
- [ ] All 7 regulatory domains mapped with requirements documented
- [ ] Compliance requirements translated into product features
- [ ] Legal review completed for all templates and workflows
- [ ] Compliance documentation created (customer-facing and internal)
- [ ] Zero compliance violations in pilot phase
- [ ] Compliance messaging tested and validated with customers

## Key Regulatory Domains

### Domain 1: Fair Housing Act (FHA) & Algorithmic Discrimination
**Regulation:** Federal Fair Housing Act, HUD guidance on AI/algorithms

**Key Requirements:**
- No discrimination based on protected classes (race, color, national origin, religion, sex, familial status, disability)
- Avoid disparate impact from algorithmic decisions
- Equal treatment in collections outreach

**Risks:**
- HUD enforcement actions (fines, consent decrees)
- Private lawsuits (class actions)
- Reputational damage

**Our Approach:**
- ❌ Avoid tenant screening entirely (stay out of high-risk domain)
- ❌ No protected class data in algorithmic decisions
- ✅ Equal treatment enforcement (same sequence for all tenants at same stage)
- ✅ Audit trails showing consistent treatment
- ✅ Human override logging for Fair Housing review

### Domain 2: Debt Collection (FDCPA & Regulation F)
**Regulation:** Fair Debt Collection Practices Act, CFPB Regulation F (2021)

**Key Requirements:**
- Contact time restrictions (8am-9pm local time)
- Frequency limits (7 attempts per 7 days per debt)
- Required disclosures in all communications
- Cease contact upon request
- No harassment, abuse, or deceptive practices

**Risks:**
- CFPB enforcement ($500-$1,500 per violation)
- Class action lawsuits
- State attorney general actions

**Our Approach:**
- ✅ Quiet hours enforcement (8am-9pm local)
- ✅ Attempt counter with auto-throttling
- ✅ Required FDCPA disclosures auto-inserted
- ✅ "Cease contact" flag with immediate suppression
- ✅ Human-in-the-loop for legal escalations

### Domain 3: Telephone Consumer Protection Act (TCPA)
**Regulation:** TCPA, FCC rules (updated 2024)

**Key Requirements:**
- Prior express written consent for automated calls/texts
- Clear opt-out mechanism (STOP keyword)
- One-to-one consent (can't bundle with other agreements)
- Immediate processing of opt-outs

**Risks:**
- $500-$1,500 per violation (can add up quickly)
- Class action lawsuits
- Regulatory investigations

**Our Approach:**
- ✅ Explicit consent capture before any SMS/voice
- ✅ STOP/HELP keyword handling (instant)
- ✅ Consent audit trail (when, how, what was agreed)
- ✅ Quiet hours enforcement
- ✅ Annual consent reconfirmation

### Domain 4: Payment Processing (PCI-DSS, Nacha)
**Regulation:** PCI-DSS 4.0 (effective April 2025), Nacha rules

**Key Requirements (PCI):**
- No storage of full card data (PANs, CVVs)
- Encryption in transit and at rest
- Annual compliance validation (SAQ)
- Incident response plan

**Key Requirements (ACH/Nacha):**
- Proper authorization for ACH debits
- Honor return codes promptly
- Monitor unauthorized return rates
- Revocation process for authorizations

**Risks:**
- Data breaches (liability, fines, reputation)
- Payment processor termination
- Nacha fines and suspension

**Our Approach:**
- ✅ Use tokenized processors (Stripe, Plaid)—never touch raw card data
- ✅ PCI-DSS SAQ-A compliance (fully tokenized)
- ✅ ACH authorization forms with required disclosures
- ✅ Return processing automation
- ✅ Annual PCI compliance validation

### Domain 5: Trust Accounting & Fiduciary Requirements
**Regulation:** State-specific trust account requirements

**Key Requirements:**
- Segregated trust accounts for tenant/owner funds
- No commingling of funds
- Monthly reconciliation
- Detailed ledgers and audit trails
- Annual audits (in some states)

**Risks:**
- State licensing board actions
- Fiduciary breach lawsuits
- Criminal charges (in extreme cases)

**Our Approach (Phase 3):**
- ✅ Support two-account patterns (operating vs. trust)
- ✅ Three-way reconciliation (bank, trust ledger, PMS ledger)
- ✅ Audit trails for every transaction
- ✅ Export of trust accounting reports

**Note:** Phase 1 focuses on communications, not accounting. Full trust features are Phase 3.

### Domain 6: Data Privacy & Security (CCPA, GLBA)
**Regulation:** California Consumer Privacy Act, Gramm-Leach-Bliley Act

**Key Requirements (CCPA):**
- Consumer data rights (access, deletion, opt-out)
- Privacy policy disclosure
- Data breach notification

**Key Requirements (GLBA):**
- Financial data safeguards
- Privacy notices
- Security program

**Risks:**
- CCPA fines ($2,500-$7,500 per violation)
- Data breach liability
- Reputational damage

**Our Approach:**
- ✅ Data subject access request (DSAR) workflows
- ✅ Data retention policies with auto-deletion
- ✅ Encryption (TLS 1.3+, AES-256)
- ✅ Role-based access control (RBAC)
- ✅ Annual security audits (SOC 2 Type II target)

### Domain 7: Tax Reporting (1099-MISC, 1099-NEC)
**Regulation:** IRS 1099 reporting requirements

**Key Requirements:**
- Report rents to owners ($600+ threshold)
- Report contractor payments ($600+ threshold)
- W-9 collection
- TIN matching
- E-filing

**Risks:**
- IRS penalties for non-filing or incorrect filing
- Customer compliance burden

**Our Approach (Phase 3):**
- ✅ Automatic 1099 generation
- ✅ W-9 collection workflow
- ✅ TIN validation
- ✅ E-file integration

## Key Deliverables

### 1. Regulatory Compliance Matrix
- **Format:** Spreadsheet with all requirements mapped
- **Contents:**
  - Regulation name and citation
  - Applicable requirements
  - Product features that address each requirement
  - Responsible team/owner
  - Compliance verification method
  - Update cadence

### 2. Product Compliance Architecture
- **Format:** Technical design document
- **Contents:**
  - **Fair Housing Compliance:**
    - Equal treatment enforcement logic
    - Audit dashboard design
    - Template library with approved language
  - **FDCPA Compliance:**
    - Quiet hours implementation
    - Attempt frequency tracking
    - Required disclosure insertion
    - Cease contact flagging
  - **TCPA Compliance:**
    - Consent capture workflow
    - STOP/HELP keyword handling
    - Consent audit trail
    - Quiet hours enforcement
  - **Payment Compliance:**
    - Tokenization architecture
    - PCI-compliant payment pages
    - ACH authorization forms
  - **Data Privacy:**
    - DSAR portal design
    - Data retention and deletion policies
    - Encryption implementation
    - Access control (RBAC)

### 3. Compliance Documentation Suite

#### Customer-Facing Documents:
- **Fair Housing Compliance Guide** (1-2 pages)
  - "How Collections OS ensures equal treatment"
  - Audit trail capabilities
  - Manager responsibilities

- **TCPA Compliance Guide** (2-3 pages)
  - "TCPA-safe rent reminders"
  - Consent best practices
  - Keyword handling
  - Quiet hours enforcement

- **FDCPA Collections Playbook** (3-5 pages)
  - "Compliant debt collection practices"
  - Template library (approved language)
  - Frequency limits
  - Escalation workflow

- **Data Privacy & Security Overview** (1-2 pages)
  - "How we protect tenant and owner data"
  - Encryption standards
  - Access controls
  - DSAR process

#### Internal Documents:
- **Compliance Operations Manual** (10-15 pages)
  - Daily compliance checks
  - Incident response procedures
  - Template approval workflow
  - Quarterly compliance review process

- **Legal Review Checklist**
  - Template approval criteria
  - Message content review
  - Feature release compliance sign-off

- **Compliance Training Materials**
  - Onboarding training for new team members
  - Customer training resources
  - Sales team compliance overview

### 4. Template Library (FDCPA/TCPA Compliant)
- **Format:** Database of approved message templates
- **Categories:**
  - Pre-due reminders (friendly)
  - Due date reminders (neutral)
  - Grace period nudges (friendly/urgent)
  - Escalation messages (urgent/firm)
  - Payment plan offers
  - Cease contact confirmations
- **Each Template Includes:**
  - Message text
  - Legal review approval date
  - FDCPA disclosure language
  - Personalization tokens
  - Tone/urgency level
  - When to use (days late, balance threshold)

### 5. Consent Management System
- **Format:** Product feature specification
- **Contents:**
  - Consent capture workflow (web form, SMS double opt-in)
  - Consent form language (TCPA-compliant)
  - Consent status tracking per tenant (phone, email, voice)
  - Opt-out processing (STOP keyword instant handling)
  - Audit trail (all consent changes logged)
  - Annual reconfirmation workflow

### 6. Audit & Reporting Tools
- **Format:** Dashboard and report specifications
- **Reports:**
  - **Fair Housing Equal Treatment Report:**
    - Shows same sequence applied to all tenants at same delinquency stage
    - Flags anomalies for review
  - **TCPA Compliance Report:**
    - Consent status by tenant
    - Opt-outs honored
    - Quiet hours violations (should be zero)
  - **FDCPA Attempt Tracking:**
    - Frequency by tenant (7-day rolling window)
    - Escalation approval trail
    - Cease contact list
  - **Message Audit Log:**
    - Immutable log (who, what, when, channel, consent status)
    - Searchable by tenant, property, date range

### 7. Compliance Monitoring & Update Process
- **Format:** Process documentation
- **Contents:**
  - **Quarterly Compliance Review:**
    - Review new regulations and guidance
    - Update templates and features as needed
    - Legal counsel review
  - **Monthly Compliance Metrics:**
    - Violations/complaints (should be zero)
    - Template usage and effectiveness
    - Consent opt-in rates
  - **Incident Response:**
    - Complaint escalation process
    - Root cause analysis
    - Corrective action
  - **Update Communication:**
    - Customer notifications of compliance changes
    - Training updates for customers and internal teams

## Research & Legal Requirements

### Legal Counsel Engagement
- **Scope of Work:**
  - Review all message templates for FDCPA compliance
  - Review consent forms for TCPA compliance
  - Review Fair Housing equal treatment logic
  - Quarterly compliance updates as regulations evolve
  - Incident response support if complaints arise
- **Budget:** $10-20K initial retainer, $2-5K/quarter ongoing

### Compliance Certifications & Audits
- **PCI-DSS Compliance:** Annual SAQ-A validation (~$5K/year)
- **SOC 2 Type II:** Target within 18 months of launch (~$30-50K initial audit)
- **Penetration Testing:** Annual security assessment (~$10-15K/year)

### Insurance Coverage
- **Errors & Omissions (E&O) Insurance:** $2M coverage (~$5-10K/year)
- **Cyber Liability Insurance:** $2M coverage (~$10-15K/year)

## Action Items

### Month 1: Foundation
- [ ] Engage compliance counsel (RFP, select, onboard)
- [ ] Create regulatory compliance matrix
- [ ] Document product compliance architecture
- [ ] Define template approval workflow
- [ ] Set up compliance tracking system

### Month 2: Documentation
- [ ] Draft customer-facing compliance guides (4 guides)
- [ ] Create internal compliance operations manual
- [ ] Build template library with legal review
- [ ] Design consent management system
- [ ] Specify audit and reporting tools

### Month 3: Implementation & Validation
- [ ] Legal review of all templates (counsel approval)
- [ ] Implement compliance features in product
- [ ] Test compliance workflows (consent, quiet hours, frequency limits)
- [ ] Train internal team on compliance procedures
- [ ] Create customer training materials

### Month 4: Launch Preparation
- [ ] Obtain E&O and cyber insurance
- [ ] Complete PCI-DSS SAQ-A
- [ ] Finalize compliance documentation
- [ ] Set up quarterly compliance review process
- [ ] Prepare compliance messaging for sales/marketing

## Dependencies

### External Dependencies
- Legal counsel engagement and availability
- Insurance carrier approvals
- Payment processor compliance requirements (Stripe, Plaid)
- Industry association guidelines (NARPM, NAA)

### Internal Dependencies
- Product roadmap and feature development
- Template copywriting and approval
- Customer training and support resources
- Sales team compliance education

## Timeline

- **Month 1:** Foundation (counsel, matrix, architecture)
- **Month 2:** Documentation (guides, manual, templates)
- **Month 3:** Implementation & validation
- **Month 4:** Launch preparation

**Total Duration:** 4 months (can run parallel with product development)

## Success Criteria

### Minimum Viable Deliverables
- Compliance matrix with all 7 domains mapped
- Product compliance architecture documented
- Legal counsel engaged and templates reviewed
- Customer-facing compliance guides (4 guides)
- Template library (20+ approved templates)
- Consent management system specified

### Stretch Goals
- SOC 2 Type II audit initiated
- Compliance training program for customers
- Compliance as competitive advantage messaging validated
- Zero compliance violations in first year

## Risks & Mitigation

### Risk 1: Regulation Changes During Development
- **Mitigation:** Quarterly compliance review process, legal counsel updates, flexible architecture

### Risk 2: Template Approval Delays
- **Mitigation:** Start early, batch review process, maintain conservative language

### Risk 3: Customer Non-Compliance (Using System Incorrectly)
- **Mitigation:** Training, guardrails in product, audit reports flagging issues

### Risk 4: Compliance Complexity Hurts Usability
- **Mitigation:** Design compliance as seamless features, not burdensome workflows

## Next Steps

1. **RFP for compliance counsel** (this week)
2. **Create compliance matrix** (spreadsheet template)
3. **Draft product compliance architecture** (technical design doc)
4. **Budget approval** for legal, insurance, certifications ($50-75K Year 1)

---

## Appendix A: TCPA Consent Form Template (Sample)

### SMS Consent Language

> **Text Message Consent**
>
> By clicking "I Agree" below, you consent to receive automated text messages from [Property Name] regarding your rent account, including:
> - Payment reminders and due date alerts
> - Account balance updates
> - Payment confirmation messages
> - Important account notices
>
> **Message Details:**
> - Message frequency varies based on your account status
> - Message and data rates may apply
> - Consent is not required as a condition of tenancy
>
> **Opt-Out Anytime:**
> - Reply STOP to cancel text messages
> - Reply HELP for assistance
> - You can also opt out by logging into your resident portal
>
> **Privacy & Security:**
> - Your phone number will not be shared with third parties for marketing
> - We use industry-standard security to protect your information
> - See our full Privacy Policy at [link]
>
> By clicking "I Agree," you confirm:
> - You are the owner or authorized user of this phone number
> - You understand the terms above
> - You consent to receive automated text messages from [Property Name]
>
> [I Agree] [No Thanks]

---

## Appendix B: FDCPA-Compliant Message Examples

### Friendly Reminder (2 Days Before Due)
> Hi [Tenant Name], friendly reminder that rent is due on [Due Date]. You can pay online at [Link]. Questions? Reply to this message or call us at [Phone]. - [Property Name]

### Due Date Reminder (Day Of)
> [Tenant Name], rent is due today ([Due Date]). Pay online at [Link] or contact us if you need assistance. Thank you! - [Property Name]

### Grace Period Nudge (3 Days Late)
> Hi [Tenant Name], your rent payment is now [Days Late] days past due. Current balance: $[Balance]. Pay online at [Link] or contact us to discuss payment options. We're here to help! - [Property Name]
>
> *This is an attempt to collect a debt. Any information obtained will be used for that purpose.*

### Escalation Message (7 Days Late)
> [Tenant Name], URGENT: Your rent is [Days Late] days past due. Balance: $[Balance]. Please contact us immediately at [Phone] to avoid late fees and further action. Payment link: [Link]. - [Property Name]
>
> *This is an attempt to collect a debt. Any information obtained will be used for that purpose.*

### Cease Contact Confirmation
> [Tenant Name], we have received your request to cease communication. We will no longer contact you except as permitted by law (e.g., legal notices). For payment or account questions, please contact us at [Phone]. - [Property Name]

**Notes:**
- All messages include required FDCPA disclosure when applicable
- Personalization tokens: [Tenant Name], [Due Date], [Days Late], [Balance], [Property Name], [Link], [Phone]
- Tone varies by stage (friendly → neutral → urgent)
- Always provide payment link and contact option
- Never threatening, harassing, or deceptive language

---

## Appendix C: Regulatory Resource Library

### Fair Housing
- HUD Fair Housing Act: https://www.hud.gov/program_offices/fair_housing_equal_opp
- HUD AI Guidance (2024): https://archives.hud.gov/news/2024/pr24-098.cfm

### TCPA
- FCC TCPA Overview: https://www.fcc.gov/general/telemarketing-and-robocalls
- 2024 Consent Rule Changes: https://www.drips.com/resources/2024-tcpa-consent-rule-changes-overview

### FDCPA
- CFPB Regulation F: https://www.consumerfinance.gov/rules-policy/final-rules/debt-collection-practices-regulation-f/
- FDIC FDCPA Guidance: https://www.fdic.gov/resources/supervision-and-examinations/consumer-compliance-examination-manual/documents/7/vii-3-1.pdf

### Payment Compliance
- PCI-DSS 4.0: https://www.mwe.com/insights/new-pci-dss-4-0-credit-card-compliance-requirements-effective-april-1-2025/
- Nacha Rules: https://www.nacha.org/rules

### Trust Accounting
- Yardi Trust Accounting Guide: https://www.yardibreeze.com/blog/2025/09/trust-accounting-for-property-managers/
- California Trust Requirements: https://www.kts-law.com/trust-fund-timing-and-recordkeeping-requirements-for-california-property-managers/

### Industry Associations
- NARPM: https://www.narpm.org/
- NAA: https://www.naahq.org/
- IREM: https://www.irem.org/
