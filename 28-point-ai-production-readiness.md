# 28-Point Enterprise AI Production Readiness Checklist

**Document Version:** 2.4  
**Classification:** Enterprise IT Operations & Governance  
**Mandatory Sign-off Gate:** Level 3 & Level 4 Enterprise Deployments  

---

## Pillar 1: Data Sovereignty, Privacy & Ingestion Security
- [ ] **1.1 Zero Data Retention (ZDR) Enforced:** API contracts stipulate that foundation model vendors do not cache, persist, or use enterprise prompts/completions for model retraining.
- [ ] **1.2 Data Residency Compliance:** All inference endpoints, embeddings storage, and vector databases operate strictly within Australian geographic boundaries (e.g., AWS `ap-southeast-2` / Azure `australiaeast`).
- [ ] **1.3 Automated PII & Sensitive Entity Redaction:** Pre-processor filter strips TFNs, BSBs, credit card numbers, Medicare identifiers, and names before tokenisation.
- [ ] **1.4 Access Control Matrix (RBAC/ABAC):** Vector indices enforce document-level and row-level entitlements mirroring Active Directory / IAM security policies.
- [ ] **1.5 Data Lineage & Provenance Tagging:** Ingested training/grounding datasets contain cryptographically hashed audit trails verifying source ownership and freshness timestamp.
- [ ] **1.6 Consent & Copyright Clearance:** Any scraping or external corpora verification has formal IP sign-off from Legal Counsel.
- [ ] **1.7 Transit & Rest Encryption:** TLS 1.3 in transit and AES-256 with customer-managed keys (CMK / BYOK) at rest.

---

## Pillar 2: Algorithmic Safety, Guardrails & Defensive Prompting
- [ ] **2.1 Adversarial Prompt Injection Defense:** Guardrail layers intercept direct jailbreaks, base64 obfuscation, recursive instruction overrides, and multi-turn persona hijacking.
- [ ] **2.2 Hallucination Benchmark Score (Grounding Fidelity):** RAG responses achieve >96% citation accuracy with strict context-window bounded citations.
- [ ] **2.3 Toxicity & Hate Speech Interceptors:** Confidence score thresholding (<0.01 tolerance) on harmful, discriminatory, or unsolicited advisory outputs.
- [ ] **2.4 Deterministic Output Anchoring:** Strict temperature pinning (0.0 to 0.2) for analytical, legal, and transactional use cases; JSON schema validation on all agent tool outputs.
- [ ] **2.5 Automated Fallback & Graceful Degradation:** Defined fallback copy when guardrails trigger, redirecting users to human escalation pathways without revealing internal system prompts.
- [ ] **2.6 Cross-Model Evaluation (Red Teaming):** Independent black-box and grey-box adversarial penetration testing completed prior to UAT.
- [ ] **2.7 Bias & Demographic Parity Review:** Output evaluation completed across test demographic strata to prevent adverse selection or unfair treatment.

---

## Pillar 3: FinOps, Latency SLAs & Token Unit Economics
- [ ] **3.1 Dynamic Semantic Caching:** High-frequency, deterministic Q&A queries served from Redis/semantic cache layer to reduce external API roundtrips (>35% targeted hit rate).
- [ ] **3.2 Model Down-Routing (Tiered Inference):** Routine triage routed to efficient SLMs (e.g., Claude 3 Haiku / GPT-4o-mini), reserving frontier LLMs exclusively for complex synthesis.
- [ ] **3.3 Hard Account-Level Rate Limits & Spend Ceilings:** Real-time billing webhooks trigger automated throttling at 80% and fail-safe cut-offs at 100% of daily spend.
- [ ] **3.4 p95 / p99 Latency Benchmarks Met:** Streaming responses begin within 800ms (Time-to-First-Token); end-to-end task completion meets contractual SLAs.
- [ ] **3.5 Cost Per Transaction Unit Metric Established:** Financial model documents cost per processed claim, query, or ticket to guarantee target delivery operating margins.
- [ ] **3.6 Token Usage Telemetry:** Structured JSON logging capturing input tokens, output tokens, cached tokens, and associated financial cost per business unit ID.
- [ ] **3.7 Multi-Region / Multi-Provider Failover:** High-availability routing implemented across primary and secondary foundation model regions or equivalent fallback LLM providers.

---

## Pillar 4: Human-in-the-Loop (HITL), Audit & Incident Containment
- [ ] **4.1 Dual-Key Authorization for High-Impact Decisions:** AI agents restricted from executing financial transfers, policy terminations, or external contractual commitments without human supervisor sign-off.
- [ ] **4.2 Comprehensive Audit Trail Immutability:** Write-once-read-many (WORM) audit storage recording prompt hash, retrieved context chunks, model version, and generated response.
- [ ] **4.3 Emergency Instant Kill-Switch:** Runbook and automated API endpoint verified to instantly detach AI tool capabilities or disconnect client-facing bots within <60 seconds.
- [ ] **4.4 Human Oversight Feedback Loop:** Real-time feedback buttons (thumbs up/down, corrective commentary) streamed into MLOps triage queues for active fine-tuning.
- [ ] **4.5 APRA / Regulatory Review Pack Generated:** Solution Architecture and Risk Assessment package formatted and reviewed by 2nd-line enterprise risk committee.
- [ ] **4.6 Support Team Operational Readiness:** Tier 1/2 service desk trained on common user failure modes, guardrail trigger scenarios, and ticket escalation trees.
- [ ] **4.7 Periodic Model Drift Schedule:** Automated weekly batch evaluation against baseline golden test datasets to detect model degradation after vendor API updates.

---

## Gate Approvals

| Role | Sign-off Name | Date | Status |
| :--- | :--- | :--- | :--- |
| **Delivery Executive / Account Lead** | | | `APPROVED / REJECTED` |
| **Head of AI / Lead Architect** | | | `APPROVED / REJECTED` |
| **Chief Information Security Officer (CISO)** | | | `APPROVED / REJECTED` |
| **Enterprise Legal & Privacy Counsel** | | | `APPROVED / REJECTED` |
