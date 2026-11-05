# SOP-AI-01: Generative AI Incident Triage & Kill-Switch Runbook

**Severity Classification:** P1 (Critical - Security/Brand/Hallucination Breach) & P2 (Major Degradation)  
**Target Response Time:** Triage < 10 mins | Kill-Switch Execution < 60 seconds  

---

## 1. Severity Definitions

- **P1 - Critical AI Incident:**
  - Leakage of customer PII or confidential client data in model completion.
  - Active adversarial jailbreak producing legally liable or hazardous statements.
  - Widespread hallucination affecting >5% of concurrent live transactions.
  - Complete gateway outage across primary and secondary model endpoints.
- **P2 - Major Degradation:**
  - Token latency p95 exceeding 6,000ms.
  - Semantic cache hit rate drops to 0%.
  - Guardrail false-positive rejection rate exceeds 8%.

---

## 2. Immediate Containment Workflow

```text
[Incident Detected]
      │
      ├─► Step 1: Execute Instant Kill-Switch (CLI / AWS AppConfig Flag)
      │           Sets feature flag: `AI_CHAT_ENABLED=FALSE`
      │           Automated failover redirects UI to standard static workflow.
      │
      ├─► Step 2: Quarantine Session Logs
      │           Export prompt, retrieved context embeddings, and raw response to encrypted S3 bucket.
      │
      ├─► Step 3: Convene Emergency Triage Bridge
      │           P&L Delivery Exec, Lead AI Engineer, CISO Incident Commander.
      │
      └─► Step 4: Root Cause & Remediation
                  Identify whether breach occurred via embedding poisoning, prompt injection, or model drift.
```

---

## 3. Emergency Kill-Switch Execution Commands

### Option A: AWS Systems Manager / AppConfig (Recommended)
```bash
# Push instant kill-switch configuration to edge proxies
aws appconfigdata start-configuration-session   --application-identifier "ClientDeliveryPlatform"   --environment-identifier "Production"   --configuration-profile-identifier "AIFeatureFlags"

aws ssm put-parameter   --name "/production/ai/kill_switch"   --value "ACTIVE"   --overwrite
```

### Option B: Cloudflare Edge Worker Bypass
```bash
# Route all traffic directly to fallback human-assisted queue
curl -X PATCH "https://api.cloudflare.com/client/v4/zones/${ZONE_ID}/workers/routes/${ROUTE_ID}"      -H "Authorization: Bearer ${CF_API_TOKEN}"      -H "Content-Type: application/json"      --data '{"pattern":"*/ai/assist*","script":"fallback-queue-router"}'
```

---

## 4. Post-Incident Review & Sign-Off
Within 24 hours of incident closure:
1. Conduct blame-free Post-Mortem.
2. Update the Adversarial Test Suite in `checklists/28-point-ai-production-readiness.md`.
3. Submit written executive summary to the Client CIO and Enterprise Risk Committee.
