# Enterprise AI Governance RACI Matrix

**Scope:** End-to-end AI Delivery, Model Lifecycle Management & Regulatory Adherence  
**Key:**  
- **R (Responsible):** The doer who carries out the task.
- **A (Accountable):** The individual with final approval and fiduciary/operational veto.
- **C (Consulted):** Domain subject-matter expert whose input is mandatory before execution.
- **I (Informed):** Kept updated on progress, milestones, and incident outcomes.

---

| Lifecycle Phase & Operational Activity | Delivery Exec (P&L) | Enterprise CISO | Legal & Privacy | MLOps / AI Eng | Client CIO / Sponsor | Service Delivery Lead |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| **1. Business Case & Token FinOps Modeling** | **A** | C | I | R | C | R |
| **2. Foundation Model Vendor Contract Due Diligence (ZDR, Sovereignty)** | **A** | C | R | C | I | I |
| **3. Enterprise Threat Modeling & Injection Vector Assessment** | I | **A** | C | R | I | C |
| **4. PII Redaction Pipeline & Data Masking Implementation** | I | C | **A** | R | I | C |
| **5. Guardrail Configuration (Toxicity, Hallucination, Bounded Context)** | C | C | C | **R / A** | I | R |
| **6. Production Release Gate (28-Point Sign-Off)** | **A** | C | C | R | C | R |
| **7. Real-Time Token Spend & Margin Monitoring** | **A** | I | I | C | I | R |
| **8. P1 Generative AI Incident Triage & Emergency Kill-Switch** | **A** | C | C | R | I | **R** |
| **9. Model Drift & Continuous Performance Benchmarking** | I | I | I | **R / A** | I | R |
| **10. APRA CPS 234 / CPS 230 Regulatory Audit Evidence Pack** | **A** | R | R | C | C | C |

---

## Executive Operational Notes

1. **Dual Accountability Distinction:**  
   The Delivery Executive holds ultimate operational accountability (`A`) for commercial margins, client satisfaction, contractual SLAs, and production sign-offs. The Enterprise CISO and Legal Counsel retain veto authority regarding security policy breaches or regulatory non-compliance.
2. **Escalation Path:**  
   If an algorithmic failure rate exceeds 2.5% within any 15-minute rolling window, the Service Delivery Lead triggers the Incident SOP and alerts the Delivery Executive within 15 minutes.
