# RevClamp Enterprise -- B2B Revenue Protection & Compliance Guardrails

[![RevClamp Enterprise -- B2B Revenue & Compliance Guardrails](https://revclamp.com/assets/revclamp-product-banner.png)](https://revclamp.com)

<p align="center">
  <a href="https://revclamp.com"><img src="https://img.shields.io/badge/Platform-revclamp.com-10B981?style=for-the-badge&logo=cloudflare&logoColor=white" alt="RevClamp Platform" /></a>
  <a href="https://registry.modelcontextprotocol.io/v0/servers?search=com.revclamp/revclamp-mcp"><img src="https://img.shields.io/badge/MCP_Registry-com.revclamp%2Frevclamp--mcp_v1.20.31-3B82F6?style=for-the-badge" alt="Official MCP Registry v1.20.31" /></a>
  <a href="https://mcptry.com/servers/com.revclamp/revclamp-mcp"><img src="https://mcptry.com/badge/com.revclamp/revclamp-mcp.svg" alt="mcptry status and score" /></a>
  <a href="https://glama.ai/mcp/servers/revclamp/revclamp-mcp"><img src="https://img.shields.io/badge/Glama-RevClamp_MCP_Server-8B5CF6?style=for-the-badge" alt="Glama MCP Server" /></a>
  <a href="https://revclamp.com/status"><img src="https://img.shields.io/badge/Trust_&_Status-5%2F5_Operational-059669?style=for-the-badge" alt="System Status" /></a>
</p>

**RevClamp Enterprise** builds deterministic, **0% take-rate** B2B revenue protection, **Visa CE 3.0** non-destructive dispute evidence staging (`submit: false`), **Stripe `2025-03-31.basil`** entitlement enforcement, and **EU/XI VIES VAT** compliance vaults for SaaS and Shopify Plus wholesale merchants.

---

## Verify in `<60` Seconds (1-Command Local CLI Smoke Check -- Zero API Key)

```bash
npx -y github:lhphong09t2/revclamp-mcp#v1.20.31 --self-test
```

All **9 deterministic MCP tools** execute **100% locally in-process** inside `local_engine.mjs` on caller-supplied snapshots with zero network calls by default. Supplying `REVCLAMP_API_KEY` (`rg_live_...`) or connecting to `POST https://api.revclamp.com/api/mcp` unlocks the persistent 90-day SQLite WAL workspace ledger, live EU Commission VIES SOAP consultation IDs & outage retry holds, and automated Stripe/Shopify webhook ingestion.

---

## The 3 Core Production Engines

| Engine | Target Ecosystem | Core Deterministic Capability | Discovery / Entrypoint |
| :--- | :--- | :--- | :--- |
| **`saas-stripe-sentinel`** | Stripe Billing & Usage (`2025-03-31.basil`) | Multi-subscription `has_more` pagination enforcement, 0-14d dunning grace-period cutoffs, non-destructive **Visa CE 3.0** dispute evidence staging (`submit: false`, `<= 18,000` UTF-16 code units), and multi-currency dispute outcome attribution. | [`revclamp.com/tools/stripe-basil-auditor`](https://revclamp.com/tools/stripe-basil-auditor) |
| **`saas-shopify-vat`** | Shopify Plus B2B & EU Cross-Border | 27 EU member state + Northern Ireland (`XI`) VAT normalization (`GR -> EL`), VIES `HTTP 200 OK` `errorWrappers` circuit breaking (`MS_UNAVAILABLE` / `GLOBAL_MAX_CONCURRENT_REQ`), integer EUR-cent Net-15/30/60 reconciliation, SHA-256 checksum CSV exports, and print-ready A4 quarterly VAT compliance certificates. | [`revclamp.com/tools/vies-vat-validator`](https://revclamp.com/tools/vies-vat-validator) |
| **[`revclamp-mcp`](https://github.com/lhphong09t2/revclamp-mcp)** | Model Context Protocol (`2025-06-18`) & CLI | Zero-dependency `stdio` & Streamable HTTP (`POST https://api.revclamp.com/api/mcp`) server exposing 9 deterministic B2B FinOps, dispute, webhook HMAC, and VAT compliance tools for Claude Desktop, Cursor, Windsurf, and CI pipelines. | [`github.com/lhphong09t2/revclamp-mcp`](https://github.com/lhphong09t2/revclamp-mcp) / [`revclamp.com/mcp`](https://revclamp.com/mcp) / [`registry.modelcontextprotocol.io`](https://registry.modelcontextprotocol.io/v0/servers?search=com.revclamp/revclamp-mcp) / [`mcp.so #6110`](https://github.com/chatmcp/mcpso/issues/6110) |

---

## Official MCP Server (`com.revclamp/revclamp-mcp` `v1.20.31`)

- **Official MCP Registry ID:** `com.revclamp/revclamp-mcp` (`v1.20.31`)
- **Streamable HTTP Endpoint:** `POST https://api.revclamp.com/api/mcp`
- **Well-Known Discovery Card:** [`https://revclamp.com/.well-known/mcp.json`](https://revclamp.com/.well-known/mcp.json)
- **Full LLM Reference:** [`https://revclamp.com/llms-full.txt`](https://revclamp.com/llms-full.txt)

| # | MCP Tool Name | Domain | Primary Capability |
| :---: | :--- | :--- | :--- |
| 1 | `revclamp_audit_revenue_leakage` | Stripe Billing & Usage | Runs a 90-day B2B revenue leakage and dispute readiness audit across subscriptions, usage events, and disputes. |
| 2 | `revclamp_evaluate_ghost_usage` | Stripe `2025-03-31.basil` | Evaluates multi-subscription customer snapshots (`has_more: false` enforced) and 0-14d dunning grace windows for unpaid API/LLM bleed. |
| 3 | `revclamp_stage_stripe_dispute_ce3` | Visa 10.4 / CE 3.0 | Evaluates 120d-365d prior undisputed charges (`ip_subnet`/`device_id` overlap) and stages a `submit: false` draft (`<= 18,000` UTF-16 code units). |
| 4 | `revclamp_validate_eu_vat_vies` | EU & `XI` B2B VAT | Normalizes 27 EU member states + Northern Ireland (`XI`) VAT IDs (`GR -> EL`), supports split (`buyerCountryCode` + `vatNumber` including numeric VAT IDs) or combined (`buyerVatId` / `vatId`) aliases with fail-closed `CONFLICTING_PARAMETER_ALIASES` guards, and evaluates VIES `HTTP 200` `errorWrappers` holds. |
| 5 | `revclamp_reconcile_b2b_net_terms` | B2B Wholesale Net-30 | Reconciles Net-15/30/60 upfront deposits and credit notes using exact integer EUR-cent accounting. |
| 6 | `revclamp_verify_webhook_signature` | Webhook HMAC-SHA256 | Generates and verifies `Stripe-Signature`, `X-Shopify-Hmac-Sha256`, and `X-RevClamp-Signature` over raw UTF-8 bytes with 300s replay checks. |
| 7 | `revclamp_calculate_roi_and_plan_fit` | 0% Take-Rate ROI & Plan Fit | Calculates monthly and annual B2B margin savings in integer USD cents vs. 25%-30% chargeback agencies and recommends the optimal tier. |
| 8 | `revclamp_simulate_webhook_replay` | Webhook Replay & FSM | Simulates 1-10 subscription lifecycle webhooks against a 72h deduplication `Set` and monotonic `createdSec` guard vs. naive arrival-order handlers. |
| 9 | `revclamp_lint_dispute_evidence` | Dispute Evidence UTF-16 & CE 3.0 | Lints `evidence[access_activity_log]` payloads against the 18,000 UTF-16 code unit ceiling, non-destructive CE 3.0 markers, and merchant note preservation. |

---

## 8 Free Interactive B2B FinOps & Compliance Diagnostic Tools (Zero Signup)

All 8 browser-based engineering tools run live at [`https://revclamp.com/tools`](https://revclamp.com/tools) with instant JSON/CSV export and zero signup required:

| # | Interactive Diagnostic Tool | Live URL | Engineering Focus |
| :---: | :--- | :--- | :--- |
| 1 | **Stripe `2025-03-31.basil` Ghost-Usage Auditor** | [`/tools/stripe-basil-auditor`](https://revclamp.com/tools/stripe-basil-auditor) | Detects per-item `current_period_end` drift, uncollected meter events, and dunning grace-window API bleed. |
| 2 | **Visa CE 3.0 Compelling Evidence Readiness Checker** | [`/tools/stripe-ce3-checker`](https://revclamp.com/tools/stripe-ce3-checker) | Verifies 2+ undisputed historical transactions (120-365 days prior) matching IP subnet, device fingerprint, and billing descriptors. |
| 3 | **18,000 UTF-16 Stripe Dispute Evidence Linter** | [`/tools/stripe-dispute-evidence-char-counter`](https://revclamp.com/tools/stripe-dispute-evidence-char-counter) | Audits UTF-16 surrogate pairs, non-destructive `--- BEGIN REVCLAMP CE3 EVIDENCE ---` markers, and `submit: false` staging safety. |
| 4 | **20-ID EU & `XI` VIES VAT Batch Validator** | [`/tools/vies-vat-validator`](https://revclamp.com/tools/vies-vat-validator) | Normalizes EU-27 + `XI` VAT numbers (`GR -> EL`), detects VIES `HTTP 200` soft-faults, and exports quarterly CSV audit bundles (SHA-256 checksum) & A4 VAT compliance certificates. |
| 5 | **Shopify Plus B2B Net-Terms Deposit & Credit-Note Calculator** | [`/tools/b2b-net-terms-calculator`](https://revclamp.com/tools/b2b-net-terms-calculator) | Reconciles Net-15/30/60 wholesale deposits, partial captures, and VAT-adjusted credit notes in integer cents. |
| 6 | **Stripe, Shopify & RevClamp Webhook HMAC-SHA256 Tester** | [`/tools/webhook-signature-tester`](https://revclamp.com/tools/webhook-signature-tester) | Verifies raw-body UTF-8 HMAC-SHA256 signatures and detects JSON re-serialization drift and replay window violations. |
| 7 | **B2B Chargeback ROI & 0% Take-Rate Calculator** | [`/tools/b2b-chargeback-roi-calculator`](https://revclamp.com/tools/b2b-chargeback-roi-calculator) | Compares flat-rate automated CE 3.0 staging against 25%-30% contingency chargeback recovery agencies. |
| 8 | **72h Webhook Replay & Out-of-Order State Machine Simulator** | [`/tools/webhook-replay-simulator`](https://revclamp.com/tools/webhook-replay-simulator) | Benchmarks monotonic `event.created` state transitions and 72-hour idempotency keys against out-of-order webhook bursts. |

---

## Golden Trio B2B Intelligence Companion MCP Suite

| Companion MCP Server & Apify Actor | Primary B2B Intelligence Signal | Local MCP Stdio Command | Apify Store & npm |
| :--- | :--- | :--- | :--- |
| **RevClamp AdPulse** (`@revclamp/google-ads-transparency-mcp`) | Zero-browser Google Ads Transparency Center (`AR...` entity disambiguation, `CR...` creatives, static `content.js` ad copy, regional disclosures) | `npx -y @revclamp/google-ads-transparency-mcp --mcp-stdio` | [Apify Store](https://apify.com/revclamp/google-ads-transparency-mcp) / [npm](https://www.npmjs.com/package/@revclamp/google-ads-transparency-mcp) |
| **RevClamp TalentPulse** (`@revclamp/unified-ats-jobs-mcp`) | Zero-browser 5-in-1 B2B ATS Job & Hiring Signal Feed across Greenhouse, Workday CXS, Ashby, Lever, and SmartRecruiters | `npx -y @revclamp/unified-ats-jobs-mcp --mcp-stdio` | [Apify Store](https://apify.com/revclamp/unified-ats-jobs-mcp) / [npm](https://www.npmjs.com/package/@revclamp/unified-ats-jobs-mcp) |
| **RevClamp ContactPulse** (`@revclamp/b2b-domain-contact-enricher-mcp`) | Zero-browser B2B Domain Contact, RFC 9116 `/.well-known/security.txt`, Schema.org `ContactPoint`, and DoH `MX` / `SPF` / `_dmarc` Enricher | `npx -y @revclamp/b2b-domain-contact-enricher-mcp --mcp-stdio` | [Apify Store](https://apify.com/revclamp/b2b-domain-contact-enricher-mcp) / [npm](https://www.npmjs.com/package/@revclamp/b2b-domain-contact-enricher-mcp) |

---

## Documentation, Security & Trust Center

- **Security, Compliance & GDPR/SOC2 Architecture:** [`https://revclamp.com/docs/security-compliance`](https://revclamp.com/docs/security-compliance)
- **Live System Status & SLA Telemetry:** [`https://revclamp.com/status`](https://revclamp.com/status)
- **Engineering Deep-Dives & Post-Mortems:** [`https://revclamp.com/blog`](https://revclamp.com/blog)
- **Support & Enterprise Inquiries:** [`support@revclamp.com`](mailto:support@revclamp.com)
