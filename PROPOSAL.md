# EquiPlus AI — Project Proposal

**The AI-Powered Ethical Investment Companion**
Version 1.1 · October 2026 · Prepared by: Rijab Butt · Contact: rijabbutt23@gmail.com

---

## Key Terms

1. **Ethical investing (ESG, Shariah, BDS screening):** investing filtered against values-based criteria, including Shariah compliance, boycott, divestment and sanctions (BDS) datasets, and environmental, social and governance factors.
2. **Shariah-compliant screening (KMI-30):** checking whether a stock meets Islamic finance rules, such as limits on interest-bearing debt and non-compliant revenue, using the KSE Meezan Index as the reference.
3. **Glocal market data (PSX and global):** one dashboard combining Pakistan Stock Exchange and US and European market data, with holdings reported in PKR or USD.
4. **Predictive growth analysis:** a five-year projection of revenue, costs, profit or loss and cash for a startup, under three growth scenarios, with break-even and risk flags.
5. **AI investment analyst (Gemini, n8n):** an AI assistant that reads SEC and SECP filings and explains findings in English or Urdu, built on an automated n8n workflow.

---

## 1. Project Overview & Problem Statement

### Overview

EquiPlus AI is an AI-powered investment companion that brings together data from the Pakistan Stock Exchange (PSX) and major global markets, and screens every asset against the ethical rules that many investors actually follow: Shariah compliance (KMI-30), Boycott, Divestment and Sanctions (BDS) datasets, and ESG criteria. It also provides predictive growth analysis for startups and companies, with five-year revenue, profit/loss and cash projections under three scenarios.

### Problem Statement

1. **Ethical screening is missing from mainstream tools.** Global brokerage apps show profit and loss. Faith-based screeners stop at Shariah. Local PSX terminals show prices but no AI analysis. No single product combines market data, ethical screening and explained AI analysis across both PSX and global markets.

2. **Local investors are underserved.** Many retail investors in Pakistan are priced out of, or discouraged by, USD-only card payments and English-only tools. Urdu-language analysis is rare.

3. **Founders lack accessible financial modelling.** Early-stage founders in Pakistan and the wider region often prepare investor materials without a structured growth and break-even model, and investors have no quick way to stress-test a pitch.

4. **Ethical investors must do the research by hand.** To check whether a company is on a BDS dataset or meets Shariah screening, investors must search several sources separately, and then find alternatives themselves when a holding fails their criteria.

### Evidence of Need

- Investors in Pakistan, the Middle East and South Asia commonly ask for Shariah-compliant options, and BDS and ESG considerations are increasingly raised by socially conscious younger investors. (Market sizing to be validated in Phase 1; see Section 9.)
- The PSX KMI-30 index provides a published Shariah reference set; BDS datasets such as those maintained by the BDS movement, Who Profits and AFSC Investigate are publicly available.

---

## 2. Proposed Solution

EquiPlus AI is delivered as a web platform, with a mobile app to follow, built on four connected layers:

| Layer | What it does | Technology |
|---|---|---|
| **Public website** | Marketing, interactive screener, plans, FAQ, legal pages, bilingual (English / Urdu) | HTML, JavaScript, Three.js 3D background, Vercel hosting |
| **Data and automation** | Routes requests to US feeds (Polygon, FMP) or PSX feeds (Capital Stake, BSL); syncs ethical datasets daily; calls the AI analyst | n8n workflows |
| **AI analysis** | Reads SEC and SECP filings, answers in English or Urdu, suggests ethical alternatives | Google Gemini 2.0 Flash |
| **Data and accounts** | Assets with ethical flags, portfolios in PKR or USD, subscriptions, row-level security | Supabase (PostgreSQL, Auth) |

### Core Ideas

- **Ethics inside the reasoning, not as an afterthought.** An asset that fails a user's filter is not just hidden. The analyst explains why and proposes compliant peers in the same sector.
- **Glocal by design.** One dashboard shows local (PSX, PKT clock) and global (NYSE/NASDAQ, EST) holdings, unified in the user's base currency.
- **Local payment options.** PKR plans accept Safepay, PayPro, JazzCash and EasyPaisa. USD plans use Stripe.
- **Transparent predictions.** Growth analysis uses a published, explainable method, with clear disclaimers. It is a planning aid, not investment advice.

### Current Prototype Status

| Area | Status |
|---|---|
| Public website (home, 3D hero, Golden Circle, screener, tiers, plans, FAQ, About, Privacy, Terms) | Built, bilingual |
| Predictive growth analysis (inputs, 5-year scenarios, break-even, risk flags) | Built, client-side |
| Pitch deck upload (PDF read in browser, 9-section review) | Built |
| Database schema with row-level security (profiles, assets, portfolios, holdings, plans, subscriptions) | Written, not yet deployed |
| n8n workflows (daily ethical sync, market router with Gemini analyst) | Written, not yet tested against live APIs |
| Pitch deck (6 slides) | Built |
| Login and signup | Demo only; Supabase Auth not connected |
| Payments | Not connected; plan buttons are placeholders |
| Flutter mobile app: login, dashboard, screener, growth analysis, portfolio, plans, account | First version written (Android and iOS code). Not yet compiled or run on a device; the build environment could not download the Flutter SDK |
| Live market data | Not connected |

---

## 3. Objectives & Expected Outcomes

### Objectives

| # | Objective | Measure of success | Target timeframe |
|---|---|---|---|
| O1 | Launch a secure, live beta of the web platform | Live on a production domain with working auth | Month 3 |
| O2 | Deliver reliable PSX and US market data | Quotes refreshed within an agreed latency; uptime ≥ 99% | Month 4 |
| O3 | Run the daily ethical sync reliably | 30 consecutive daily runs with no failed upserts | Month 4 |
| O4 | Enable paid subscriptions in PKR and USD | First paying subscribers via both gateway types | Month 5 |
| O5 | Validate product demand with real users | ≥ 500 registered beta users; ≥ 5% convert to paid | Month 6 |
| O6 | Ship the Flutter mobile app | App store release (Android first) | Month 9 |

### Expected Outcomes

- **For investors:** a single place to check PSX and global holdings against Shariah, BDS and ESG criteria, with explained AI analysis in English or Urdu.
- **For founders:** a structured, five-year growth and break-even view, plus a checklist of pitch-deck sections investors expect.
- **For the business:** a recurring subscription revenue model, a defensible position in an underserved niche, and a data asset (curated ethical records) that grows over time.

### Success Metrics (first 12 months)

- Monthly active users and retention at 30 days
- Free-to-paid conversion rate
- Share of paid users choosing PKR versus USD (validates the local pricing bet)
- Number of analysis runs and pitch-deck uploads per active user
- Accuracy of the ethical sync against source datasets (manual spot-checks each month)

---

## 4. Target Users

| Segment | Description | Primary need | How EquiPlus helps |
|---|---|---|---|
| **Local retail investors (Pakistan)** | Individuals investing on the PSX, often with limited capital and a preference for Shariah-compliant options | Halal screening, PKR pricing, local payment methods, Urdu | Shariah screening, PKR plans, JazzCash / EasyPaisa, Urdu reports |
| **Ethically motivated investors (MENA, South Asia, global)** | Investors who choose assets based on values, including BDS and ESG criteria | Clear ethical flags with sources; alternatives when a holding fails | BDS and ESG screening, alternatives engine |
| **Early-stage founders** | Startup founders preparing for investor conversations | Growth model, break-even view, pitch-deck checklist | Predictive growth analysis, deck review |
| **Angel and early-stage investors** | Individuals screening startups | Fast, consistent first-pass analysis | Predictive analysis and risk flags |
| **Students and advisers** | Finance and entrepreneurship students, and advisers who need teaching or discussion aids | Explainable examples | Scenario outputs, bilingual explanations |

### Primary Persona

**Ayesha, 29, Lahore.** She works in a corporate job and invests monthly on the PSX. She wants Shariah-compliant stocks, but she finds most apps only in English and priced in dollars. She pays with JazzCash and wants a simple screener and a clear explanation of why a company is excluded.

---

## 5. Key Features / Deliverables

### Phase 1 deliverables (MVP, Months 1–3)

| ID | Feature | Description |
|---|---|---|
| F1 | Secure accounts | Email and password sign-up and login via Supabase Auth; profile with language and currency preferences |
| F2 | Ethical screener | Toggles for BDS exclusion, strict Shariah (KMI-30) and PSX-only; results with reasons |
| F3 | Asset data model | Assets table with exchange, asset class, and ethical compliance JSON, using the schema already written |
| F4 | Market data integration | PSX feed (Capital Stake or BSL) and US feed (Polygon or FMP) through the n8n router |
| F5 | Predictive growth analysis | Five-year revenue, cost, profit/loss and cash projections, three scenarios, break-even year, risk flags |
| F6 | Pitch-deck review | PDF upload read in the browser; checks nine standard sections |
| F7 | Bilingual interface | English and Urdu with right-to-left layout across all pages |
| F8 | Legal and support pages | FAQ, About, Privacy Policy, Terms of Service (reviewed by counsel before launch) |

### Phase 2 deliverables (Months 4–6)

| ID | Feature | Description |
|---|---|---|
| F9 | Portfolio tracker | Holdings in PKR or USD; base-currency unification using forex rates |
| F10 | Daily ethical sync | n8n schedule that pulls BDS datasets and upserts flagged assets into Supabase, with monitoring |
| F11 | AI analyst | Gemini 2.0 Flash reads filings (SEC 10-K/10-Q; SECP PDFs) and answers in English or Urdu |
| F12 | Ethical alternatives | Suggests clean competitors in the same sector for flagged holdings |
| F13 | Subscriptions | Stripe (USD); Safepay, PayPro, JazzCash and EasyPaisa (PKR); plan management and cancellation |
| F14 | Market-open clocks | PSX (PKT) and NYSE/NASDAQ (EST) session indicators on the dashboard |

### Phase 3 deliverables (Months 7–9)

| ID | Feature | Description |
|---|---|---|
| F15 | Flutter mobile app | First version covers login and signup, a dashboard with market clocks and portfolio summary, the screener, the growth analysis (with pitch-deck PDF upload), portfolio, plans and account settings. Shares the Supabase backend. Next: device testing, Android release, then iOS |
| F16 | Website crawling for analysis | n8n crawler reads a submitted company website for the analysis |
| F17 | Alerts | Price and compliance-change notifications |
| F18 | Vector search for news | Qdrant collections separating local (Dawn, Business Recorder, Profit) and global news |

---

## 6. Implementation Plan & Timeline

The plan assumes a small core team (see Section 7) and two-week sprints.

### Timeline Overview

| Phase | Months | Focus | Key milestone |
|---|---|---|---|
| **Phase 0: Validation** | Month 0 (2–3 weeks) | Confirm market demand, legal review of disclaimers, confirm data-licence terms with providers | Go / no-go decision |
| **Phase 1: MVP** | Months 1–3 | Accounts, screener, data model, market feeds, growth analysis, deck review, bilingual UI | Closed beta |
| **Phase 2: Monetisation and automation** | Months 4–6 | Portfolio, ethical sync, AI analyst, subscriptions, market clocks | Public launch and first paid users |
| **Phase 3: Mobile and scale** | Months 7–9 | Flutter app hardening and device testing, crawler, alerts, vector news search | App store release |
| **Phase 4: Growth** | Months 10–12 | Partnerships, referral programme, feature iteration from user data | 12-month review |

### Detailed Plan (Phase 1 example)

| Weeks | Work package | Owner | Output |
|---|---|---|---|
| 1–2 | Confirm Supabase project; apply schema and RLS; test policies | Backend | Working database |
| 1–2 | Replace demo auth with Supabase Auth; profile creation trigger | Frontend and backend | Real login and signup |
| 3–4 | Build PSX and US feed workflows in n8n; error handling and rate-limit control | Data | Quotes stored and served |
| 3–4 | Connect screener to live assets table | Frontend | Screener on live data |
| 5–6 | Daily ethical sync: dataset parser, ticker mapping, upsert, failure alerts | Data | Ethical flags in database |
| 5–6 | Move growth analysis calculation to a tested module; add unit tests | Frontend | Tested analysis engine |
| 7–8 | Security review, load test, privacy checks; closed beta with 50 users | All | Beta feedback log |
| 9–10 | Fix priority issues; legal review of policies; prepare launch | All | Beta release candidate |
| 11–12 | Buffer for slippage; onboarding content; support process | All | Phase 1 complete |

### Dependencies

- Data-licence agreements with market-data providers must be signed before live feeds start (Week 3 at the latest).
- Legal review of Privacy Policy and Terms must be complete before any real user signs up.
- Payment gateway merchant accounts (Stripe; Safepay or PayPro) must be approved before Phase 2 billing.

---

## 7. Resources or Requirements

### Team

| Role | Responsibility | Phase |
|---|---|---|
| Founder / product lead | Vision, priorities, investor and partner relations, user research | All |
| Full-stack developer (web) | Website, screener, analysis module, Vercel deployment | All |
| Backend and data engineer | Supabase schema, n8n workflows, data feeds, ethical sync | Phase 1 onward |
| Flutter developer | Mobile app: first version written; device testing and store release | Phase 1–3 (contract acceptable) |
| UI/UX designer | Brand system, screens, usability testing | Phase 1–2 (part time) |
| Compliance and legal adviser | Disclaimers, privacy, terms, regulatory check in Pakistan (SECP) and abroad | Phase 0–1, then as needed |
| Customer support (part time) | Beta support, FAQ maintenance | Phase 2 onward |

### Technology and Services

| Item | Purpose | Notes |
|---|---|---|
| Vercel | Website hosting | Free tier for prototype; paid tier for production |
| Supabase | Database, authentication, row-level security | Pro tier recommended for production backups |
| n8n | Workflow automation (self-hosted or cloud) | Self-hosting gives control over secrets |
| Google Gemini API | AI analysis | Usage-based pricing; set spending limits |
| Market-data providers | Polygon or FMP (US); Capital Stake or BSL (PSX) | Licence fees; confirm redistribution rights |
| BDS and ethical datasets | Ethical flags | Open datasets; confirm licence terms and attribution |
| Payment gateways | Stripe; Safepay or PayPro; JazzCash and EasyPaisa | Merchant onboarding and fees |
| Qdrant | Vector search for news (Phase 3) | Managed or self-hosted |
| Domain, email, monitoring | Brand presence, support, uptime alerts | Standard SaaS costs |

### Budget Estimate (Assumptions to Validate)

The following are planning assumptions in USD, to be replaced with actual quotes.

| Category | Phase 1 (3 months) | Phase 2 (3 months) | Phase 3 (3 months) |
|---|---|---|---|
| People (contract and part time) | To be confirmed | To be confirmed | To be confirmed |
| Market data licences | To be quoted | To be quoted | To be quoted |
| Cloud, hosting and AI usage | Low (prototype tiers) | Moderate | Moderate to high |
| Legal and compliance | Required up front | Ongoing | Ongoing |
| Marketing and beta incentives | Minimal | Moderate | Moderate |

Recommend funding the Phase 1 budget and locking the data-licence quotes before committing to Phase 2.

### Tools Already in Use

- Brand assets from the EquiPlus AI brand sheet (logo, colours, typefaces Montserrat and Inter)
- Static website on Vercel (prototype)
- Database schema, workflow JSON files and deck build scripts in the project folder

---

## 8. Potential Challenges or Risks

| # | Risk | Likelihood | Impact | Mitigation |
|---|---|---|---|---|
| R1 | **Market-data licensing costs or restrictions** prevent redistribution of quotes to users | High | High | Confirm licence terms in Phase 0; budget for licences; show only delayed data where required |
| R2 | **Ethical data accuracy.** BDS and ethical datasets change, and mapping company names to tickers can be wrong | High | High | Manual spot-checks each month; show the source and reason for every flag; allow user corrections with review; never present a flag as final legal advice |
| R3 | **Investment-advice regulation.** Predictions and AI commentary could be seen as advice | Medium | High | Clear disclaimers; avoid buy/sell language; describe outputs as planning aids; legal review in Pakistan (SECP) and any target market before launch |
| R4 | **AI errors or hallucinated figures** in analyst commentary | Medium | High | Ground AI answers in retrieved filings; show citations; calculations done in code, not by the model; human review of high-visibility content |
| R5 | **Prediction over-reliance.** Users treat scenario outputs as forecasts | Medium | Medium | Visible disclaimers; plain-language explanation of assumptions; conservative defaults; publish methodology |
| R6 | **Payment friction and fraud** on local gateways | Medium | Medium | Use established gateways; monitor chargebacks; start with a small number of local methods |
| R7 | **Data privacy and security breach** | Low to medium | High | Row-level security; secrets kept server-side; encryption in transit; security review before beta; incident response plan; privacy policy reviewed by counsel |
| R8 | **Political or sanctions sensitivity** around BDS content and the Palestine-related positioning | Medium | Medium | Neutral, source-cited presentation; plain explanation of the criteria; legal review in each target market; clear policy on how datasets are chosen |
| R9 | **Dependency on third-party services** (Supabase, n8n, Gemini, Vercel) and their pricing or outages | Medium | Medium | Abstract provider calls behind n8n; export backups; monitor usage costs and set limits |
| R10 | **Low user adoption or conversion** | Medium | High | Early beta with target communities; measure conversion from the first month; adjust pricing and features based on data |
| R11 | **Scope creep** across markets, languages and platforms | High | Medium | Strict phase gates; defer non-core features; regular prioritisation reviews |
| R12 | **Key-person dependency** on a small team | Medium | Medium | Documentation; code in version control; shared access to all services |
| R13 | **Mobile app delays** | Medium | Medium | Ship web first; reuse shared backend; Android before iOS |
| R14 | **Currency and rate risk** for USD-priced plans and forex conversion | Low to medium | Low | Update forex rates regularly; display rate and date; price in PKR for local users |
| R15 | **Flutter app not yet verified.** The first version has not been compiled or tested on devices, so bugs or dependency-version issues may appear | High | Medium | Build and run on Android and iOS emulators first; add unit tests for the calculation logic; pin package versions; device testing before beta |

---

## 9. Additional Details (Optional)

### Compliance and Legal Principles

- EquiPlus is an information and analysis platform. It is not a broker, dealer, investment adviser or exchange.
- Every analysis output carries the disclaimer: informational, not investment advice, past performance and AI output do not guarantee future results.
- Personal data is protected by row-level security and processed only for the purposes in the Privacy Policy.
- Privacy and terms follow the principles of Pakistan's data protection rules and, for EU residents, the GDPR. Counsel to confirm.
- Ethical flags come from named, published sources. Each flag shows its source and reason.

### Open Questions to Resolve in Phase 0

1. Which market-data providers offer redistribution terms that fit a subscription product?
2. Does any SECP requirement apply to an analysis and screening platform in Pakistan, and what is the right licensing or disclaimer approach?
3. What is the right price point for Rs. 2,000 Pro versus USD equivalents?
4. Which BDS dataset(s) should be the primary source, and what is the update and attribution policy?
5. How much of the AI analysis should run in the browser versus through the n8n service?

### Measurement and Review

- Monthly review of metrics in Section 3, sprint reviews every two weeks, and a formal 12-month review.
- Quarterly review of ethical-sync accuracy and of the predictive model's assumptions against any realised outcomes that users choose to share.

### Next Steps

1. Approve this proposal and confirm the Phase 0 budget.
2. Start data-licence and legal conversations.
3. Confirm the Supabase project and begin Phase 1 Week 1.
4. Recruit or contract the backend and Flutter roles.
5. Compile and test the Flutter app on Android and iOS, then fix issues found in device testing.

### Change Log

| Version | Date | Changes |
|---|---|---|
| 1.0 | October 2026 | First full proposal: overview, solution, objectives, users, features, plan, resources, risks |
| 1.1 | October 2026 | Added key terms; Flutter app status (login, dashboard, screener, growth analysis, portfolio, plans, account); updated feature F15, timeline, team, risks (new R15) and next steps |

---

*This proposal is a planning document. Budget figures, timelines and market-size claims are estimates to be validated during Phase 0. Nothing in this document is investment advice.*
