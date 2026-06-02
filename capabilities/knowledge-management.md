# Capability Policy: Knowledge Management

**Status:** Active  
**Version:** 1.0  
**Review date:** [YOUR_REVIEW_DATE]  
**Authorized by:** CEO

## Purpose

Grants the Knowledge Director authority to ingest airlock-cleared artifacts, classify and organize KB content, apply retention policy, and maintain the knowledge base in a well-structured and retrievable state.

## Maximum Authority Level

Level 5 — Stage for archival operations (preparing content for archival)  
Level 6 — Execute for ingestion, classification, reorganization, and archival per approved retention schedule

Deletion is explicitly excluded from this capability. Deletion requires separate CEO approval per item.

## Allowed Roles

- Knowledge Director
- Temporary task agents authorized by President Agent operating within Knowledge Director scope

## Allowed Systems

| System | Access Type | Conditions |
| --- | --- | --- |
| KB filesystem (`/knowledge/`) | Read / Write / Reorganize | Freely permitted |
| KB inbox (`/knowledge/inbox/`) | Read / Write / Route | Freely permitted |
| KB archive (designated archive folder) | Write (archival) | Per approved retention schedule only |
| Google Drive (designated digital organization folder) | Write (mirror) | For CEO read access; sync only |

## Allowed Data Classes

- Class A (Public) — no retention limit
- Class B (Internal) — no retention limit
- Class C (Sensitive) — 180-day retention; archive after; deletion requires CEO approval
- Class D (Restricted) — NOT permitted in KB under any circumstances; escalate immediately if encountered

## KB Structure

```
/knowledge/
  index.md
  /projects/
  /research/
  /operations/
  /technology/
  /creative/
  /people/
  /finance/
  /inbox/
  /archive/        ← archival destination for aged Class C content
```

## Ingestion Rules

1. An artifact may be ingested without per-item CEO approval if it has cleared an approved airlock channel (documented by Operations Director manifest).
2. An artifact that has not cleared an approved channel may not be ingested. Escalate to CEO.
3. Class D artifacts may not be ingested under any circumstances. Escalate immediately.
4. Inbox items must be classified and routed within 48 hours of arrival. If classification cannot be determined within 48 hours, escalate to CEO.

## Retention Enforcement

| Class | Limit | Action at Limit |
| --- | --- | --- |
| A | None | Retain indefinitely |
| B | None | Retain indefinitely |
| C | 180 days from ingestion | Knowledge Director archives autonomously per schedule |
| D | Not permitted | Never ingest; escalate |

Archival is autonomous per this schedule. Deletion requires explicit CEO approval regardless of age or classification.

The Knowledge Director must maintain a retention log recording ingestion date, classification, and archival date for all Class C artifacts.

## Cross-Referencing Standard

- Use `[[article-name]]` wiki link format for internal cross-references
- Index (`knowledge/index.md`) must be updated whenever a new article is added or an existing one is moved
- Tags may be applied to articles using a consistent tagging scheme defined by the Knowledge Director and documented in `knowledge/index.md`

## Prohibited Actions

- Ingesting artifacts that have not cleared an approved airlock channel
- Ingesting or retaining Class D content
- Deleting any KB artifact without CEO approval
- Exporting KB content to external services, accounts, or recipients
- Accessing source systems represented in KB artifacts (KB content is a derivative artifact, not a portal to the source)
- Modifying policy documents stored in the policy repository

## Spending Limits

No spending authority associated with this capability.

## Maximum Acceptable Loss

**Financial MAL:** $0 (no spending authority associated with this capability).

Information exposure risk: unauthorized export of KB content could expose Class C content (financial exports, business strategy, personal context). The Knowledge Director must treat export requests as high-risk and escalate any ambiguous case.

## Approval Thresholds

| Action | Approval Required |
| --- | --- |
| Ingest airlock-cleared artifact | None |
| Classify and route artifact | None |
| Reorganize KB structure | None |
| Archive Class C artifact per retention schedule | None |
| Ingest artifact not cleared by airlock | CEO approval |
| Delete any artifact | CEO approval |
| Export KB content externally | CEO approval |
| Retain Class C beyond 180 days | CEO approval |

## Audit Requirements

The Knowledge Director must log and report to President Agent:

- Artifacts ingested (source manifest reference, classification assigned)
- Routing decisions
- Archival actions (artifact, reason, date)
- Inbox items escalated for classification uncertainty
- Any content identified as potential Class D after ingestion
- Index updates
