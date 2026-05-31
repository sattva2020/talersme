# 01 — Vision

## The opportunity window

GNU Taler is at a critical adoption inflection in 2026:
- The **protocol is stable** (NGI TALER 2024-2026 cycle has hardened core components)
- **EU policy** has made privacy-respecting digital payments a priority (Digital Euro debate, several national banks publicly endorse Taler-style models)
- **AI is mature enough** for technical-onboarding use cases — small local LLMs (Phi-3-mini, Qwen2-1.5B Q4) reason about API documentation accurately enough to walk a non-technical merchant through setup; not feasible 18 months ago

But **the merchant-side UX has not caught up** with the protocol. SMEs that would benefit most from Taler (privacy-respecting payments, low transaction fees, sovereignty from US payment giants) are blocked at the integration step.

Whoever ships the canonical SME-onboarding tool in 2026-2027 sets the pattern for the next wave of Taler adoption.

## Who we serve

**Primary:** small and micro European enterprises — cafes, freelancers, online shops, consultants, NGOs — who want privacy-respecting payments but lack devops capacity.

**Secondary:** Taler-aware developers and agencies building Taler integrations for clients, who need a faster onboarding tool than the current CLI + REST API workflow.

**Tertiary:** the Taler community itself — TalerSME generates real-world merchant adoption case studies and feedback that flows back to protocol design.

## What success looks like at M+12

- ≥3 independent downstream forks or deployments
- ≥10 EU SMEs running TalerSME in production
- ≥1 commercial-license customer (compliance-driven embedding)
- TalerSME's normalised setup metrics adopted as community reference for "Taler merchant onboarding difficulty"
- Active community on the project's issue tracker

## What we deliberately do NOT build

- **Not a wallet** — that's customer-side, well-served by existing Taler wallet apps
- **Not a payment processor** — that's the role of the Taler exchange
- **Not a generic e-commerce platform** — we integrate into existing merchant sites, not replace them
- **Not a Taler protocol replacement** — we are application-layer, not protocol-layer
- **Not a closed-source commercial product** — the open-source repository is the canonical home; commercial license is an option for embedders only
