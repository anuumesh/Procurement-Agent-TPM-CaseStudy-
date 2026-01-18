Scenario 1 — ERP Upgrade Conflict
Issue

Oracle ERP upgrade requires 6 weeks downtime but Phase 1 deadline cannot slip.

Immediate Action Plan

Activate ERP sandbox replica

Freeze production integration

Shift Phase 1 to read-only cache mode

Implement API mock layer

Impact Assessment
Area	Impact
Timeline	No delay (workaround applied)
Budget	+8% infra cost
Scope	Limited write-back postponed
Alternative Options

Option A — Delay Phase 1 ❌ (Not acceptable politically)
Option B — Temporary Middleware Cache ✅ (Chosen)
Option C — Manual data sync ❌ (High risk)
