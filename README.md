# TalerSME

> **AI assistant that removes the integration barrier preventing European SMEs from adopting GNU Taler payments.**

[![Status](https://img.shields.io/badge/status-early%20stage-orange)](#status) [![License](https://img.shields.io/badge/license-AGPL--3.0%20%2B%20commercial-blue)](#license) [![NGI TALER](https://img.shields.io/badge/funded%20by-NGI%20TALER%20(submission%20pending)-green)](https://nlnet.nl/taler/)

## Status

**Early stage.** Application submitted to [NLnet NGI TALER call #13](https://nlnet.nl/taler/) on 2026-05-31, awaiting review. Active development begins on grant award (orientation: autumn 2026). This repository is the canonical home for the project; star/watch to follow progress.

## The Problem

GNU Taler is technically excellent — privacy-preserving, low-overhead, designed for the EU digital sovereignty era. But its **merchant-side requires devops skills small businesses lack**. A Berlin cafe, a Lviv freelancer, a Krakow shop cannot deploy a Taler merchant backend on their own. The result is that Taler adoption is bottlenecked not by protocol limits but by SME-side UX.

## What We Build

TalerSME bridges that gap with **three conversational, mobile-first capabilities**:

### 1. Setup Wizard
AI walks the merchant through Taler backend deployment, key generation, webhook configuration, and bank-account binding in 10 minutes of natural-language dialogue — replacing 50 pages of technical docs.

### 2. AI Invoice Generation
> Merchant: *"Invoice Anna for the redesign, €1200, due in 14 days"*

TalerSME issues a signed Taler payment request, generates QR + payment link, sends to customer, tracks payment state.

### 3. Customer Q&A Widget
Embeddable JavaScript snippet for the merchant's site. Answers customer questions about Taler in their native language ("How do I pay? Is my data private?"), onboarding them into the ecosystem.

## Tech Stack

- **Backend:** Rust + Axum + sqlx + sqlcipher (encrypted local storage)
- **Taler integration:** GNU Taler merchant backend HTTP API (`taler-rust` crate or hand-rolled client)
- **AI inference:** Local Phi-3-mini Q4 via Candle (privacy-first, offline-capable) + optional OpenAI-compatible API fallback for higher-quality recommendations
- **Frontend:** Mobile-first PWA (Vite + TypeScript + Tailwind)
- **Customer widget:** Embeddable JavaScript snippet (vanilla JS, no framework lock-in)
- **Deployment:** Single static Rust binary OR Docker compose
- **Languages supported:** EN / DE / UA / PL minimum at M5

See [`docs/02-architecture.md`](docs/02-architecture.md) for the full picture.

## Roadmap (7 months from grant award)

| Milestone | What ships |
|---|---|
| **M1** | Architecture RFC + UX mockups + repo bootstrap |
| **M2** | Setup wizard MVP — single language (EN), Docker deployment path |
| **M3** | Invoice generation backend + REST API |
| **M4** | Customer Q&A widget MVP — embeddable snippet |
| **M5** | Multi-language: EN, DE, UA, PL |
| **M6** | 3-5 EU pilot SME deployments (healthcare / freelance / retail) |
| **M7** | 1.0 release + full documentation + 5-min demo video |

See [`docs/03-roadmap.md`](docs/03-roadmap.md) for milestone detail.

## License

- **Open-source repository:** [GNU AGPL-3.0](LICENSE) — ensures upstream contributions and prevents closed SaaS forks
- **Commercial dual license:** available from the applicant for vendors who need to embed TalerSME under non-AGPL terms (B2B compliance tools, proprietary SME platforms)

Pattern proven by Mastodon, Nextcloud, Sentry, Open edX.

## Team

Focused 2-person partnership:

- **Ruslan Hryban** — Project Lead / Principal Engineer (Ukraine) — technical work, NLnet liaison, milestone delivery, pilot integration. [linkedin.com/in/ruslan-hryban-ai](https://www.linkedin.com/in/ruslan-hryban-ai) | [griban.dev](https://griban.dev)
- **Dmytro Myroshnykov** — Operations & Community Engagement Lead — GNU Taler community outreach via the Integration Community Hub, EU pilot SME recruitment, post-grant sustainability.

External freelance support is budgeted separately for UI/UX, professional DE+UA localization, and pilot SME honoraria — see the application's budget breakdown.

## Funding

This project has applied for funding from the European Union's Horizon Europe research and innovation programme through [NLnet Foundation's NGI TALER fund](https://nlnet.nl/taler/) (grant agreement No. 101135475). Application status: under review (submission 2026-05-31).

## Contributing

Until grant award, contributions are paused — we expect to publish a `CONTRIBUTING.md` with code-of-conduct, signing requirements (DCO), and `good first issue` labels at M1. Star/watch to follow progress.

For early collaboration interest (pilot SME, translation, UX feedback), email: **ruslan@griban.dev**

## Related projects (by the same applicant)

- [MyHealth-Europe](https://github.com/sattva2020/myhealth-mcp) — open-source MCP server for self-hosted health data (EHDS-ready, Rust, parallel NLnet NGI Zero Commons Fund #13 application)

## Acknowledgements

NGI TALER is funded by the European Commission's [Next Generation Internet](https://ngi.eu) programme under [DG CONNECT](https://ec.europa.eu/info/departments/communications-networks-content-and-technology_en) with additional funding from the [Swiss State Secretariat for Education, Research and Innovation](https://www.sbfi.admin.ch/sbfi/en/home.html).

GNU Taler is developed by the [GNU community](https://www.gnu.org/) and [Taler Systems SA](https://taler-systems.com).
# talersme
