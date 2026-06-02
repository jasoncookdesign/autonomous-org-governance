# Autonomous Org Governance

A governance framework template for building constitutionally-defined, policy-governed autonomous AI organizations operating in a sandboxed environment.

This repository provides a complete, ready-to-adapt governance structure for organizations where AI agents operate with real authority: writing code, managing information, drafting communications, analyzing finances, and producing creative work — all within explicit, auditable constraints that keep a human in final control.

---

## What This Is

Most AI agent deployments are tool calls with no guardrails. This framework treats the AI organization as a governed entity: agents have roles, roles have capabilities, capabilities have authority levels, and every autonomous action has a maximum acceptable loss defined in advance.

The result is an AI organization that behaves less like an unbounded tool and more like a governed workforce — useful precisely because it operates inside constraints, not despite them.

---

## Constitutional Design Principles

The framework is built on six inviolable principles from the Constitution:

**Deny-by-default authority.** Nothing is permitted unless explicitly granted. Silence, ambiguity, and inference do not imply permission. The correct response to uncertainty is escalation.

**Human sovereignty.** The CEO (you) is the sole constitutional authority. No agent, role, model, automation, or workflow may supersede your authority. All policy changes require your approval. All capability activations require your approval.

**Explicit authority.** Authority must be written, specific, scoped, and auditable. Roles do not create authority. Capabilities create authority. Workloads consume authority.

**Identity firewall.** The sandbox assists the CEO. It does not represent the CEO. Sandbox identities remain distinct from your personal identity unless you explicitly authorize an exception.

**Maximum Acceptable Loss.** Every autonomous capability must define a worst-case loss threshold. Capabilities that cannot tolerate compromise must not be delegated.

**Append-only audit trails.** All material actions must be traceable. The organization must produce sufficient logs, reports, and explanations for you to understand what happened, why it happened, which policy authorized it, and which role performed it.

---

## Directory Structure

```
autonomous-org-governance/
├── constitution/           Root governance document — human sovereignty, deny-by-default, explicit authority
├── operations/             Machine-facing sandbox operating charter for all agents
├── governance/             Governance manual — operational handbook translating the constitution into practice
├── roles/                  Role definitions for all organizational positions
├── capabilities/           Capability policies — the actual permission grants for autonomous action
├── policies/
│   ├── agents/             Temporary agent authorization and lifecycle rules
│   ├── airlock/            Approved information transfer channels and procedures
│   ├── audit/              Reporting requirements and incident response procedures
│   ├── finance/            Wallet governance and spending authority rules
│   ├── infrastructure/     Sandbox host, network, accounts, and approved software
│   ├── knowledge/          Knowledge base governance, classification, and retention
│   └── security/           Baseline security practices for all roles and tools
├── audit/                  Filed audit records — logs, manifests, incident reports, capability reviews
├── templates/              Reusable templates for roles, capabilities, workloads, incidents, escalations
├── workloads/              Active, proposed, completed, and archived workloads
│   ├── active/
│   ├── proposed/
│   ├── completed/
│   └── archived/
├── knowledge/              Sandbox knowledge base — airlock-cleared artifacts only
├── CUSTOMIZATION.md        Guide to filling in all [YOUR_*] placeholders
└── LICENSE
```

---

## Key Documents — Reading Order

Start here to understand the framework before customizing it:

1. **`constitution/constitution.md`** — The root of trust. Defines the twelve constitutional articles that govern everything else. Read this first.

2. **`operations/sandbox-operating-charter.md`** — The machine-facing behavioral specification. This is what your agents read to understand how to operate. Covers authority levels, default behavior under uncertainty, data classification, airlock rules, financial rules, prompt injection handling, and escalation format.

3. **`governance/governance-manual.md`** — The human-readable operational handbook. Explains the full system architecture, how roles and capabilities are structured, the airlock architecture, identity governance, financial and wallet governance, and the implementation roadmap.

4. **`roles/`** — Role definitions for the initial organizational structure. Each role establishes purpose, responsibilities, permitted capabilities, prohibited actions, and escalation requirements. Start with `president-agent.md`.

5. **`capabilities/`** — The actual permission grants. Each capability policy defines exactly what a role may do, on which systems, at what authority level, subject to what spending limits and maximum acceptable loss. This is where authority lives.

6. **`policies/`** — Domain-specific operational rules covering airlock procedures, incident response, wallet governance, knowledge base management, security, and infrastructure.

---

## Getting Started

### 1. Clone this repository

```bash
git clone https://github.com/your-org/autonomous-org-governance.git
cd autonomous-org-governance
```

### 2. Fill in the placeholders

Open `CUSTOMIZATION.md` and work through every `[YOUR_*]` placeholder. The guide explains what each placeholder means, what decision it represents, and how to think about it. Key categories:

- **Identity & Communication** — your org email, personal email
- **Infrastructure** — your sandbox hostname, IP address, hardware specs
- **Financial Controls** — your virtual card provider, transaction limits, monthly caps, maximum acceptable loss thresholds
- **External Accounts** — your image generation account (for the Creative Director)

### 3. Define your roles

Review the role definitions in `roles/`. The initial catalog covers eight roles:

- **President Agent** — operational coordination
- **Engineering Director** — software development
- **Operations Director** — airlock and workflow operations
- **Knowledge Director** — knowledge base governance
- **Security Steward** — compliance and incident response
- **Research Director** — web research and synthesis
- **Creative Director** — creative production
- **Financial Analysis Director** — financial analysis (no account access)

Add, remove, or adapt roles to match your actual use case. Use `templates/role-template.md` for new roles.

### 4. Define your capabilities

Capabilities are the permission grants. Each role's capability policy defines exactly what that role may do. Review `capabilities/` and adapt spending limits, maximum acceptable loss thresholds, approved vendors, and approved systems to match your environment.

### 5. Adapt the policies

Review `policies/` and update the infrastructure policy to match your actual sandbox host, the airlock policy to match your actual transfer channels, and the wallet policy to match your virtual card provider and spending philosophy.

### 6. Provision your sandbox infrastructure

The governance framework describes a sandboxed environment with:
- A dedicated compute host (separate from your personal machine)
- Separated organizational accounts (not your personal accounts)
- An approved airlock for moving information in
- A read-only policy repository your agents can consult

The `policies/infrastructure/infrastructure-policy.md` describes the reference architecture. Adapt it to your actual hardware and setup.

---

## Design Philosophy

**Governance-first AI safety at the individual scale.** Enterprise AI governance frameworks are built for compliance teams, not individuals building personal AI organizations. This framework applies the same zero-trust, least-privilege, explicit-authority principles at a scale a single person can actually operate.

**Blast radius minimization.** Every capability defines a Maximum Acceptable Loss. The system is designed around the assumption that something will eventually go wrong — a prompt injection, an unexpected charge, an overeager agent. The question is not whether but how bad. MAL limits keep "bad" bounded.

**Escalation as normal behavior.** Most AI systems are designed to complete tasks. This framework is designed to escalate gracefully when authority is unclear. An agent that stops and asks is more trustworthy than one that improvises. Escalation is expected behavior, not failure.

**Separation of concerns.** Roles coordinate. Capabilities authorize. This separation prevents role titles from becoming informal permission grants. An agent with the title "Director" has no more authority than its capability policies explicitly grant.

**Auditability over autonomy.** If an action cannot be logged, explained, and reviewed, it should not be autonomously executed. The audit trail is not bureaucracy — it is the mechanism by which you maintain meaningful oversight of an organization that operates faster than you can supervise in real time.

---

## License

MIT License — see `LICENSE`.

Built by Jason Cook. Contributions welcome.
