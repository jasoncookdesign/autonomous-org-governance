# Capability Policy: President Coordination

**Status:** Active  
**Version:** 1.0  
**Review date:** [YOUR_REVIEW_DATE]  
**Authorized by:** CEO

## Purpose

Grants the President Agent its two Level 6 execution authorities: agent lifecycle decisions and direct email delivery to the CEO. All other President Agent functions (log synthesis, policy reading, internal coordination, escalation drafting) operate at Levels 1–4 and do not require explicit capability authorization under the Governance Manual's default authority model.

## Maximum Authority Level

Level 6 — Execute, limited to the two specific action types defined below.

## Allowed Roles

- President Agent only

## Execution Authority 1 — Agent Lifecycle Decisions

The President Agent may authorize the creation of temporary task agents and retire inactive non-director agents. Temporary agent authorization is governed in full by `policies/agents/temporary-agent-framework.md`.

| Action | Conditions |
| --- | --- |
| Authorize temporary task agent | Per `policies/agents/temporary-agent-framework.md`; scoping declaration required before agent begins work |
| Retire non-director agent | Director recommendation; no negative impact on other directors; decision logged |
| Retire a director | Not permitted — CEO only |
| Create a permanent role | Not permitted — CEO only |

Every lifecycle decision must be recorded in `audit/president-lifecycle-log.md` immediately upon execution.

## Execution Authority 2 — Direct Email Delivery to CEO

The President Agent may send email from [YOUR_ORG_EMAIL] to [YOUR_PERSONAL_EMAIL] for the following specific purposes only:

| Communication Type | Conditions |
| --- | --- |
| Session digest | End of significant work session |
| Weekly governance summary | Weekly cadence if organization has been active |
| Escalation request | One per issue; await response; do not repeat |
| Incident notification | Immediately upon High or Critical incident |

This email authority does not extend to any other recipient, any other account, or any other communication purpose.

## Allowed Systems

| System | Access Type | Conditions |
| --- | --- | --- |
| `audit/president-lifecycle-log.md` | Write (append-only) | For every lifecycle decision |
| [YOUR_ORG_EMAIL] | Send | To CEO only; approved communication types only |
| Policy repository | Read | Daily-synced local clone; read-only |

## Allowed Data Classes

- Class A and B freely
- Class C only in reports to CEO; must not be included in communications to any other party

## Prohibited Actions

- Lifecycle decisions that would grant authority beyond the requesting director's existing capability set
- Email to any recipient other than the CEO
- Email for any purpose other than the four approved communication types
- Modifying or deleting lifecycle log entries
- Any execution action not listed in this policy

## Spending Limits

No spending authority associated with this capability.

## Maximum Acceptable Loss

**Financial MAL:** $0 (no spending authority associated with this capability).

Operational risk: a compromised President Agent with this capability could create unauthorized agents or send misleading reports to the CEO. The lifecycle log provides the Security Steward an independent audit record. The email channel is constrained to the CEO only, limiting the blast radius of any communication misuse.

## Approval Thresholds

| Action | Approval Required |
| --- | --- |
| Authorize temporary task agent (within bounds) | None — log required |
| Retire non-director agent (on director recommendation) | None — log required |
| Retire a director | CEO approval |
| Create permanent role | CEO approval |
| Send session digest to CEO | None |
| Send weekly summary to CEO | None |
| Send escalation to CEO | None |
| Send incident notification to CEO | None |
| Any email to party other than CEO | CEO approval |

## Audit Requirements

- Every lifecycle decision recorded in `audit/president-lifecycle-log.md` immediately upon execution
- All emails sent to CEO logged (type, date, subject)
- Security Steward reads lifecycle log autonomously per `capabilities/security-audit.md`
