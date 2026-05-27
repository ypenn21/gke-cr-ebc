# GKE & Cloud Run EBC Briefing Agenda
## Modernizing Your LAMP Stack for the Cloud-Native Era

**Format:** Executive Briefing Center
**Duration:** ~3.5 Hours
**Audience:** Executive & Decision-Maker Level

---

## Pre-Briefing Preparation *(Internal — Google Team Only)*
**15 min before session**

- Confirm attendee list and roles
- Align on customer's top 3 pain points (cost, reliability, developer velocity, scale)
- Stage any demo environments
- Brief all Google speakers on discovery call notes

---

## Agenda at a Glance

| # | Session | Duration |
|---|---|---|
| 1 | Welcome & Introductions | 15 min |
| 2 | Your Business: Listening Session | 20 min |
| 3 | The Modernization Imperative: GKE & Cloud Run as the Answer | 25 min |
| 4 | Google Cloud's Application Modernization Vision | 20 min |
| — | Break | 10 min |
| 5 | The Migration Journey: From LAMP to Cloud-Native | 30 min |
| 6 | Reference Architecture: What It Looks Like | 15 min |
| — | Break | 10 min |
| 7 | Customer Success Stories | 15 min |
| 8 | Live Demo *(optional)* | 20 min |
| 9 | The Business Case: ROI & TCO | 15 min |
| 10 | Your Recommended Journey: Next Steps | 15 min |
| 11 | Open Q&A and Executive Discussion | 20 min |
| 12 | Close & Executive Summary | 10 min |

**Total: ~3 hrs 25 min (excluding optional demo)**

---

## Detailed Agenda

### 1. Welcome & Introductions
**15 min**

- Google EBC host welcomes attendees and sets the tone
- Round-table introductions: name, role, and one word describing their current infrastructure challenge
- Session goals: not a sales pitch — a strategic working session

> **Speaker note:** Open with curiosity. The most effective EBCs are conversations, not presentations.

---

### 2. Your Business: Listening Session
**20 min**

*Discovery-first. Google listens, customer talks.*

- Current application landscape and business context
- Where is the LAMP stack creating friction today?
  - Scaling challenges during peak traffic (holiday sales, flash events)?
  - Slow release cycles holding back the business?
  - Rising infrastructure costs and operational overhead?
  - Developer talent retention tied to modern tooling?
- What does success look like in 12–18 months?

> **Framing:** "Before we share anything, we want to make sure today's conversation is anchored in what matters most to you."

---

### 3. The Modernization Imperative: GKE & Cloud Run as the Answer
**25 min**

*The business case and the solution land in the same breath.*

#### Why Now — The Hidden Cost of Your LAMP Stack

LAMP on VMs was built for a different era of the internet. Today it creates three structural business problems:

- **Cost inefficiency:** VMs run 24/7 at full size whether it's 3am or Black Friday — you're always paying for peak, even when traffic is zero
- **Fragility at scale:** A sudden traffic spike (flash sale, viral moment) can overwhelm a fixed VM estate; scaling up means hours of provisioning, not seconds
- **Operational drag:** Your team spends cycles on VM patching, database maintenance, and manual deployments — time that isn't building features or growing revenue

#### The Answer: Two Technologies, One Platform Decision

GKE and Cloud Run are not abstract cloud products — they are direct solutions to the problems above:

| Your LAMP Pain Point | Cloud Run Solves It When... | GKE Solves It When... |
|---|---|---|
| Paying for idle capacity | Your app is HTTP-driven web traffic → **scales to zero, pay nothing at off-peak** | You have background workers or cron jobs that run continuously |
| Can't handle flash sales | You need instant, automatic scale-up for sudden spikes → **Cloud Run handles this natively** | You need fine-grained control over scaling thresholds and resource limits |
| Manual deployments slow releases | **Both** move you to automated CI/CD via Cloud Build — code committed = code deployed | Same |
| DBA overhead on MySQL | **Both** move you to Cloud SQL — managed MySQL with automated backups, patching, and failover | Same |

**Cloud Run** is the right fit if your application is primarily request-driven web traffic — it abstracts away all infrastructure, scales in seconds for flash sales, and costs nothing when traffic is zero. The most capital-efficient compute model available.

**GKE** is the right fit if your application has background workers, complex internal networking, scheduled jobs, or requires platform-level control — the power of Kubernetes without managing the control plane.

The business outcome is the same either way: lower compute costs, faster releases, and a team no longer doing ops toil. The choice between them is made by your workload's characteristics, not by preference.

> **Executive takeaway:** The reason to move now isn't industry trend pressure — it's that your current architecture is charging you for problems GKE and Cloud Run eliminate by design. The cost of waiting is a monthly bill you don't have to pay.

---

### 4. Google Cloud's Application Modernization Vision
**20 min**

*Strategic roadmap, not a product catalog.*

- Google's philosophy: meet you where you are, move at your pace
- The three destinations of a modern application platform:
  - **Managed containers** — you control the workload, Google manages the infrastructure
  - **Serverless** — you focus only on code; Google handles everything else
  - **CI/CD** — eliminate the toil of manual build, deploy, and release management with set of ci/cd tools setup for automation. 
- How Google Cloud connects these layers into a unified, secure platform
- Google's own infrastructure story: Gmail, Search, and YouTube all run on the same Kubernetes-based foundation as GKE

> **Executive takeaway:** Google isn't selling you a product — we run our own business on this. You're getting what Google uses internally.

---

### BREAK
**10 min**

---

### 5. The Migration Journey: From LAMP to Cloud-Native
**30 min**

*Google Cloud's proven four-phase migration framework — framed entirely around business impact, risk reduction, and timeline.*

#### Phase 1 — Assess: Know What You Have
**5 min**

- Map your current application: what's stateful, what's stateless, what is your database doing
- Identify the business risk: where does the monolith hurt you today?
- Outcome: a prioritized modernization backlog with a clear TCO baseline

#### Phase 2 — Plan: Design for the Future
**10 min**

Decoupling strategy — the three pillars every LAMP migration must address:

- **Storage:** Product images move from local VM disks → Cloud Storage (globally durable, CDN-ready)
- **Sessions:** Shopping cart sessions move from local PHP files → Memorystore (Redis) — shoppers never lose their cart between page loads, even as traffic scales
- **Database:** MySQL moves from a self-managed VM → Cloud SQL (fully managed: automated backups, patching, failover — your team stops being DBAs)

#### Phase 3 — Deploy: Zero-Downtime Migration
**10 min**

**The Strangler Fig Pattern** — the key to a safe migration with no big-bang cutover:

1. A routing layer sits in front of your existing application
2. New services go live behind it while the old system keeps running
3. Traffic shifts gradually from old to new — one feature at a time
4. When the migration is complete, the old system is decommissioned

Business never goes dark. Customers never notice.

**Additional execution steps:**
- **Database Migration Service (DMS):** Keeps Cloud SQL in sync with your live GCE database in real time. Cutover is a DNS update, not a scheduled outage
- **Cloud Build:** Automates your deployment pipeline — when a developer commits code, a new container is built and deployed automatically. No more manual pushes, no more deployment Fridays

#### Phase 4 — Optimize: Day-Two Value
**5 min**

- **Cloud CDN:** Static assets (product images, CSS, JavaScript) are cached globally at Google's edge — pages load faster for every shopper, and backend compute costs drop
- **Autoscaling:** The system scales itself — up for Black Friday, back down on Tuesday morning. You never over-provision, you never under-deliver
- **Observability:** Cloud Logging and Cloud Monitoring give your team visibility into application health before your customers call you about it

> **Executive takeaway:** This isn't a rip-and-replace. It's a controlled, phased modernization where the business stays online the entire time.

---

### 6. Reference Architecture: What It Looks Like
**15 min**

*A visual walkthrough of the end-state architecture — no code, just components and their business purpose.*

| Component | What It Replaces | Business Benefit |
|---|---|---|
| **GKE or Cloud Run** | GCE Virtual Machines | Pay for what you use; scales automatically |
| **Cloud SQL (MySQL)** | Self-managed MySQL on VM | No patching, automated backups, built-in HA |
| **Memorystore (Redis)** | Local PHP session files | Shoppers never lose cart; scales horizontally |
| **Cloud Storage** | Local `/var/www/html/images` | Durable, globally accessible, CDN-ready |
| **Cloud CDN** | No equivalent | Pages load faster globally; less backend load |
| **Cloud Build** | Manual deployments | Automated CI/CD; faster, safer releases |
| **Secret Manager** | Hardcoded credentials | Security and compliance — secrets never in code |
| **Cloud Monitoring** | Reactive firefighting | Proactive alerting before customers are impacted |

---

### BREAK
**10 min**

---

### 7. Customer Success Stories
**15 min**

*Proof points from organizations that made this exact journey.*

- **Retail / e-commerce on Cloud Run:** Migrated from LAMP on VMs — outcome: 55% reduction in compute costs, 3x faster checkout page performance during peak
- **Mid-market PHP monolith on GKE:** Outcome: from 2 deploys per week to 15 per day; engineering team redeployed from ops to feature work
- **Database migration to Cloud SQL:** Eliminated 40 hours/month of DBA maintenance work; zero unplanned downtime in first year

> **Speaker note:** Use Google-approved customer references or anonymized case studies. Prioritize stories closest to the customer's industry vertical.

---

### 8. Live Demo *(Optional)*
**20 min**

*Tailor to audience technical depth. Skip or make optional for pure executive audiences.*

- Show a containerized PHP application deploying to Cloud Run in under 2 minutes
- Demonstrate autoscaling behavior under simulated load
- Show Cloud Monitoring dashboard with live metrics

---

### 9. The Business Case: ROI & TCO
**15 min**

*Translate everything into numbers the CFO cares about.*

**Cost levers:**
- Scale-to-zero (Cloud Run): pay $0 when traffic is zero
- Autoscaling (GKE): eliminate standing over-provisioning for peak headroom
- Managed services (Cloud SQL, Memorystore): eliminate VM licensing and DBA overhead

**Speed levers:**
- Automated CI/CD: days of release cycles → hours
- Faster page load via CDN: direct revenue impact in e-commerce (every 100ms of latency = ~1% conversion drop)

**Risk levers:**
- No scheduled maintenance windows for DB patching
- Phased migration (Strangler Fig) = no big-bang cutover risk
- Built-in HA and failover across availability zones

> **Bring a preliminary TCO model if possible — even directional numbers anchor the conversation.**

---

### 10. Your Recommended Journey: Proposed Next Steps
**15 min**

*End with momentum, not ambiguity.*

**Immediate (0–30 days)**
- Schedule a Technical Architecture Review (complimentary with Google Cloud)
- Run a LAMP stack discovery assessment to baseline current TCO
- Identify one candidate workload for a Cloud Run proof-of-concept

**Near-Term (30–90 days)**
- Stand up a non-production Cloud Run environment with one migrated service
- Pilot Cloud SQL with a read replica of the production database
- Establish Cloud Build CI/CD pipeline for the pilot workload

**Strategic (90–180 days)**
- Begin Strangler Fig migration for production traffic
- Migrate session management to Memorystore
- Activate Cloud CDN for static asset delivery

**Proposed Engagement Model**
- Dedicated Google Cloud Customer Engineer assigned to your account
- Access to Google Professional Services for migration execution
- Quarterly EBC check-in to review progress and roadmap alignment

---

### 11. Open Q&A and Executive Discussion
**20 min**

- Open floor for questions, concerns, or "what about..." scenarios
- Address procurement, security, compliance, or organizational change questions
- Google team listens for signals on blockers and objections

---

### 12. Close & Executive Summary
**10 min**

- Google EBC host summarizes the 3 key takeaways from today's session
- Confirm agreed next steps and owners on both sides
- Provide attendees with a one-page leave-behind summarizing the journey and proposed roadmap
- Thank attendees; transition to optional networking lunch or 1:1s

---

## Key Messages to Reinforce

> **1. You don't have to choose between stability and modernization.**
> The Strangler Fig migration pattern keeps your business running at 100% while the new platform is built around it.

> **2. GKE and Cloud Run are not competing products — they are complementary choices.**
> Match the platform to the workload, not the other way around.

> **3. The biggest cost of your LAMP stack isn't the infrastructure bill — it's the opportunity cost.**
> Every hour your team spends on VM patching and manual deployments is an hour not spent building features that grow revenue.

> **4. Google runs its own business on this.**
> GKE is the same platform that powers Google's products at global scale. You're getting proven technology, not a pilot program.

---

## Suggested Speaker Lineup

| Segment | Suggested Speaker |
|---|---|
| Welcome & Introductions | EBC Host / Account Executive |
| Listening Session | Account Executive + Customer Engineer |
| Modernization Imperative & GKE/Cloud Run | Customer Engineer / Technical Specialist |
| Google Cloud Vision | Industry Solutions Consultant |
| Migration Journey (4 Phases) | Customer Engineer |
| Reference Architecture | Customer Engineer |
| Customer Success Stories | Account Executive or Partner |
| Business Case / TCO | Account Executive |
| Next Steps & Close | Account Executive + EBC Host |