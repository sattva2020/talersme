# 03 — Roadmap

> 7-month execution plan from grant award. Subject to refinement in M1 RFC.

## M1 — Foundations

**Deliverables**
- D1.1 Architecture RFC merged (public)
- D1.2 Rust workspace bootstrapped (crates/talersme-core, crates/talersme-server, crates/talersme-ai stubs)
- D1.3 UX mockups (10 screens) for setup wizard + invoice composer + customer widget
- D1.4 CI matrix green on Linux x86 / macOS / Linux ARM64
- D1.5 GNU Taler Integration Community Hub design review session

**Acceptance**
- All deliverables public on this repository
- Repository has ≥1 external observer (Taler community)

## M2 — Setup Wizard MVP

**Deliverables**
- D2.1 Setup wizard end-to-end on Linux x86 (single language EN, Docker deployment path)
- D2.2 Taler merchant backend integration tested against Taler reference exchange
- D2.3 Audit log functional

**Acceptance**
- A non-developer test user completes Taler backend setup in ≤15 min via the wizard
- All wizard operations either read-only or explicit-confirm; no silent destructive calls

## M3 — Invoice Generation Backend

**Deliverables**
- D3.1 Invoice composer REST API
- D3.2 Conversational frontend for invoice generation
- D3.3 QR + payment-link generation
- D3.4 Payment state tracking (pending / confirmed / failed)

**Acceptance**
- End-to-end demo: natural-language prompt → signed Taler payment request → real payment on Taler reference exchange

## M4 — Customer Q&A Widget

**Deliverables**
- D4.1 Embeddable JS widget (vanilla, no framework lock-in)
- D4.2 Local LLM inference path (Phi-3-mini Q4 via Candle)
- D4.3 Opt-in cloud LLM fallback with disclosure
- D4.4 20-question quality test suite

**Acceptance**
- Widget deployed on the project landing page
- ≥80% acceptable answers on 20-question quality test (validated by 3 external ML engineers)

## M5 — Multi-language

**Deliverables**
- D5.1 EN / DE / UA / PL UI translations
- D5.2 Taler-specific knowledge base (RAG layer) in all 4 languages
- D5.3 Professional terminology review (DE + UA) — payments + technical glossary

**Acceptance**
- All 3 capabilities (wizard / invoice / widget) work end-to-end in all 4 languages
- 20-question quality test passes ≥80% per language

## M6 — Pilot Deployments

**Deliverables**
- D6.1 3-5 EU SMEs deployed with TalerSME in production (target: ≥2 DE/AT, ≥1 CEE)
- D6.2 Anonymised case studies for each pilot
- D6.3 First external contributor PR merged

**Acceptance**
- Each pilot accepts ≥1 real Taler transaction
- Each pilot's case study published

## M7 — 1.0 Release

**Deliverables**
- D7.1 Tagged 1.0 release
- D7.2 Full documentation site
- D7.3 5-min demo video
- D7.4 Final NLnet report
- D7.5 Presentation at NLnet community event

**Acceptance**
- Release notes signed; documentation complete
- Final report accepted by NLnet
