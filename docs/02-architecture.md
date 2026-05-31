# 02 — Architecture

> Working draft — final architecture locks at M1 RFC.

## Components

```
┌─────────────────────────────────────────────────────────────────┐
│  TalerSME Merchant Workstation (mobile-first PWA + local server) │
│  ┌───────────────────┐   ┌────────────────────┐                 │
│  │ Setup Wizard UI   │   │ Invoice Composer    │                 │
│  │ (Vite + Tailwind) │   │ (conversational)    │                 │
│  └────────┬──────────┘   └────────┬───────────┘                 │
│           │                       │                              │
│           └───────┬───────────────┘                              │
│                   ▼                                              │
│         ┌──────────────────────────────────┐                     │
│         │  Rust backend (Axum)              │                    │
│         │  ┌──────────────────────────────┐ │                    │
│         │  │ AI inference layer            │ │                    │
│         │  │  • local Phi-3-mini Q4 (def.) │ │                    │
│         │  │  • cloud LLM (opt-in fallback)│ │                    │
│         │  └──────────────────────────────┘ │                    │
│         │  ┌──────────────────────────────┐ │                    │
│         │  │ Taler merchant adapter        │ │                    │
│         │  │  (taler-rust or hand-rolled)  │ │                    │
│         │  └──────────────────────────────┘ │                    │
│         │  ┌──────────────────────────────┐ │                    │
│         │  │ Encrypted local storage       │ │                    │
│         │  │  (sqlite + sqlcipher)         │ │                    │
│         │  └──────────────────────────────┘ │                    │
│         └────────────┬─────────────────────┘                     │
└──────────────────────│───────────────────────────────────────────┘
                       │  HTTPS
                       ▼
            ┌─────────────────────────┐
            │ GNU Taler exchange       │
            │ (operated by merchant's  │
            │  preferred Taler bank)   │
            └─────────────────────────┘

┌─────────────────────────────────────────────────────────────────┐
│  Customer-facing Q&A Widget (embeddable JS snippet)              │
│  Runs on merchant's site → talks to merchant's TalerSME backend  │
│  Local LLM serves Q&A → no customer data leaves merchant's host  │
└─────────────────────────────────────────────────────────────────┘
```

## Key design decisions

| Decision | Why |
|---|---|
| **Rust backend, single static binary** | Cross-platform deployment without runtime dependency hell; aligns with applicant's MyHealth-Europe pattern |
| **Local-first LLM (Phi-3-mini Q4 via Candle)** | Privacy: customer Q&A doesn't leak conversation patterns to OpenAI/Anthropic |
| **Cloud LLM as opt-in fallback only** | Better quality when merchant explicitly accepts trade-off |
| **PWA, not native mobile apps** | Cross-platform without app-store gatekeeping; smaller distribution overhead |
| **AGPL-3.0 + commercial dual license** | Open community + sustainable commercial path |
| **No customer data persistence on merchant device beyond audit log** | Privacy minimisation; align with Taler's own design philosophy |
| **Modular WPs releasable independently** | Mitigates single-developer bottleneck risk |

## What lives where

- `crates/talersme-core` — measurement library, Taler adapter, business logic
- `crates/talersme-server` — Axum HTTP server, mobile-first UI delivery
- `crates/talersme-ai` — LLM inference layer (Candle wrapping Phi-3)
- `widget/` — customer-facing embeddable JS (separate build artifact)
- `docs/` — architecture, vision, roadmap, threat model
- `pilots/` — anonymised case studies from pilot SME deployments (added M5-M7)

## Threat model (high-level — full version M3)

1. AI hallucination in setup wizard breaking merchant deployment → mitigated by read-only/dry-run defaults + explicit confirmation
2. Customer Q&A widget leaking data to LLM provider → mitigated by local LLM default + opt-in cloud disclosure
3. Encrypted local storage key loss → mitigated by clear backup recipe in deployment guide
4. Taler protocol evolution breaking integration → mitigated by version pinning + Taler ICH engagement
