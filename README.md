# Awesome-Automated-Privacy-Policy-Enforcers

# Top Automated Privacy Policy Enforcers Ecosystem

**Curated List of SaaS Products & Open-Source GitHub Projects**  
*Focused on PII Redaction, Consent Enforcement & Data Access Governance*  
**Last updated: March 2026**

This repository tracks notable **SaaS platforms** and **open-source projects** for **Automated Privacy Policy Enforcers**. These tools sit between your data and external systems—scrubbing PII before it reaches third-party LLMs, enforcing consent policies at the token level, and maintaining audit trails for regulatory compliance.

**Examples** include OneTrust, Transcend, Securiti.ai, Ketch, DataGrail, MineOS, Privacera, BigID, Osano, and Immuta (the category leaders).

**Open-source emphasis**: This section is heavily expanded with every major active project for self-hosting, deterministic PII masking, and open privacy policy enforcement—ideal for privacy engineers, compliance teams, and developers seeking transparent, vendor-independent privacy infrastructure.

Contributions welcome! Open a PR to add/update entries. Keep descriptions factual and link to official sites.

## Table of Contents
- [SaaS/Hosted Platforms](#saas-hosted-platforms)
- [Open-Source GitHub Projects](#open-source-github-projects)
- [How to Contribute](#how-to-contribute)
- [Disclaimer](#disclaimer)

## SaaS/Hosted Platforms

- **[OneTrust](https://www.onetrust.com/)**  
  Enterprise privacy management platform with consent management, data mapping, DSR automation, and AI governance modules. Widely deployed for GDPR and CCPA compliance at scale.

- **[Transcend](https://transcend.io/)**  
  Privacy infrastructure platform with data subject request automation, consent management, and data mapping. Focuses on developer-friendly privacy engineering.

- **[Securiti.ai](https://securiti.ai/)**  
  Data privacy and AI governance platform with data discovery, classification, and policy enforcement across cloud environments.

- **[Ketch](https://www.ketch.com/)**  
  Privacy automation platform with consent management, data subject rights, and policy enforcement across web and mobile.

- **[DataGrail](https://www.datagrail.io/)**  
  Privacy management platform with data discovery, DSR automation, and consent tracking. Integrates with 1,000+ SaaS applications.

- **[MineOS](https://www.mineos.ai/)**  
  Privacy operations platform automating data subject requests, consent management, and data mapping.

- **[Privacera](https://privacera.com/)**  
  Data security and governance platform with fine-grained access control, data masking, and policy enforcement across cloud data platforms.

- **[BigID](https://bigid.com/)**  
  Data intelligence platform for privacy, security, and governance. Features data discovery, classification, and policy enforcement across structured and unstructured data.

- **[Osano](https://www.osano.com/)**  
  Privacy management platform with consent management, DSR automation, and vendor risk assessment.

- **[Immuta](https://www.immuta.com/)**  
  Data access governance platform with policy enforcement, data masking, and audit trails for cloud data platforms.

## Open-Source GitHub Projects

- **[Membrane](https://pypi.org/project/membrane-ai/)**  
  Open-source SDK that intercepts prompts, **deterministically masks PII locally**, and seamlessly restores it from the LLM's response. Built specifically to handle **LLM paraphrasing**—maintains contextual entity trackers so even when the model radically paraphrases, identity resolves deterministically. Zero trust: masking happens entirely locally before the outbound network request is even constructed. Supports OpenAI, Anthropic, Gemini, and Ollama. Enterprise tier adds AWS KMS, HashiCorp Vault, RBAC, and immutable audit logging .

- **[Fides (Ethyca)](https://github.com/ethyca/fides)**  
  Open-source privacy engineering platform (Apache-2.0) for managing **data privacy requests** in your runtime environment and enforcing privacy regulations in code. Features **Privacy as Code**—define data practices in YAML, connect to real databases, and run DSRs (access, erasure, consent) against live data. Ships with Admin UI, Privacy Center for request submission, and CLI deployment via Docker .

- **[pii-masker-ai](https://pypi.org/project/pii-masker-ai/)**  
  Ultra-fast, **zero-dependency** PII masking and reversible unmasking for AI prompts, LLM agents, and vector databases. **Bi-directional reversible masking** with sequential placeholders (`<EMAIL_1>`, `<PHONE_1>`) so the LLM retains conversational context, then restores original data on return. **Permanent redaction** mode for logging and training datasets. Comprehensive pattern suite: credit cards (Luhn-validated), IBAN, IPv4/IPv6, MAC addresses, JWT, PEM private keys, OpenAI/Anthropic/GitHub/AWS/Slack/Stripe API keys, SSN, international phones, and regional IDs. CLI with **CI scanner** for pre-commit pipelines .

- **[promptcloak](https://pypi.org/project/promptcloak/)**  
  Fast, **zero-dependency** Python CLI and library that finds API keys, tokens, credentials, emails, IPs, and card numbers in text and replaces them with stable placeholders. **Reversible mappings** enable round-tripping redacted prompts/answers with LLMs. `--check` mode exits 1 if sensitive data is found—perfect for **CI/CD gates**. `--entropy` catches unknown high-entropy secrets. MIT licensed core .

- **[eunomia](https://pypi.org/project/eunomia-ai/)**  
  Open-source **data governance framework for LLM-based applications** working at the **token level**. Modular "instruments" can be combined: `PiiInstrument` identifies and replaces PII (EMAIL, PERSON, etc.), with configurable edit modes (replace, redact). Token-level enforcement means policies apply to individual tokens before they reach the model .

- **[Prompt Redaction Studio](https://hub.docker.com/r/bhairavpardiwala/prompt-redaction-studio)**  
  Self-hosted, **zero-egress** PII redaction for LLM prompts. Uses **Microsoft Presidio** with spaCy NER models running in-process. Web UI, JSON API, and desktop tray client. **Reversible tokens** (`<PERSON_1>`, `<EMAIL_ADDRESS_1>`) restore real values from model replies. **In-memory only**—no disk writes, mapping keyed by random session ID with 1-hour TTL. CI test intercepts every socket and DNS lookup to verify no network egress. Runs as non-root user .

- **[Maskeraid](https://addons.mozilla.org/zh-CN/firefox/addon/maskeraid-mask-data-from-llms/)**  
  Browser extension (Firefox/Chrome) that **sanitizes prompts before sending to LLMs** (ChatGPT, Claude, Gemini, HuggingFace). Custom regex and string replacement rules for emails, phones, credit cards, SSNs. **Local storage only**—no data sent to external servers. Real-time preview of masked text .

- **[Probo](https://pkg.go.dev/go.probo.inc/probo)**  
  Self-hostable GRC platform (ISC licensed) with **270+ MCP tools** for LLM agent integration. Covers full governance lifecycle: risk management, controls, vendor risk, **data privacy** (DPIA, TIA, processing activity records, rights requests), access reviews, audit programs. Every entity accessible via web console, CLI, MCP API, GraphQL, and n8n node. Policy-based RBAC, immutable audit logs, evidence chains .

- **[ODGS MCP Server](https://pypi.org/project/odgs-mcp-server/)**  
  Deterministic governance enforcement at the **AI agent boundary**. Connects any MCP-compatible agent to the **ODGS Sovereign Validation Engine**—evaluates data operations against governance rules at runtime and produces **S-Certs** (cryptographically signed records that a governance rule was applied). Free tier: validation, scoring, conformance checking. Licensed tier: regulatory compilation (EU AI Act, DORA, GDPR), drift detection, catalog sync .

- **[ODRE Framework](https://github.com/ODRE-Framework/odre-framework)**  
  Open-source **Open Digital Rights Enforcement** framework (UPM research) using W3C ODRL standard to define, use, and enforce privacy policies in digital environments. Python and Java implementations. Particularly focused on decentralized environments like Data Spaces, achieving transparency, control, and data sovereignty .

### Additional Strong Open-Source Options

- **[OpenOptOut](https://github.com/rlnunez/OpenOptOut)** — Self-hosted, distributed platform automating **personal data removal** from data brokers. Zero-knowledge identity vaults, multi-tenant consortium routing, sandboxed plugin extensibility. Built for libraries, schools, credit unions, and non-profits .
- **[Pryv.io](https://github.com/pryv/open-pryv.io)** — Open-source **personal data store** with API-first architecture, consent management, and audit trails. PostgreSQL/SQLite storage, multi-core deployment .
- Community **n8n** workflows for privacy policy automation and PII detection alerting.

**Frameworks for building custom systems**: Combine **Membrane** for LLM prompt PII masking with **Fides** for DSR automation and policy enforcement, **pii-masker-ai** for CI/CD PII scanning, **Probo** for GRC lifecycle management, and **PostgreSQL** for persistence—creating a fully self-hosted, enterprise-grade privacy enforcement platform.

## How to Contribute

1. Fork the repo.
2. Add/edit entries in `README.md` (follow existing format).
3. Include: name, link, 1–2 sentence description, and whether it's SaaS or open-source.
4. Submit PR with a short explanation.

Star the repo if you find it useful!

## Disclaimer

- This is a **community-curated** list — not exhaustive and not an endorsement.
- Privacy enforcement tools handling PII must comply with data protection regulations (GDPR, CCPA, HIPAA, etc.) and maintain appropriate audit trails.
- **PII detection is probabilistic, not perfect.** No regex or NLP model catches every sensitive value. Defense in depth—multiple detection engines, human review for high-risk workflows, and regular false-negative testing—is essential. Masking before LLM calls is a control, not a guarantee.
- **Placeholder restoration introduces correlation risk.** Reversible masking creates a mapping between placeholders and real values. If the mapping is compromised or the placeholder pattern is predictable, the protection degrades. In-memory-only mappings with short TTLs (as in Prompt Redaction Studio) reduce this surface .
- Self-hosted open-source solutions require proper security hardening, key management for reversible mappings, and ongoing maintenance. The Einstein Trust Layer pattern—masking, zero-retention with model providers, toxicity checks, and audit logging—provides a reference architecture for enterprise deployments .

---

**Made for privacy engineers, compliance officers, data protection teams, and developers building transparent privacy enforcement solutions.**  
Let's make Automated Privacy Policy Enforcers more open, data-driven, and privacy-preserving.
