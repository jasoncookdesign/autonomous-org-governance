# Customization Guide

This guide walks through every `[YOUR_*]` placeholder in the repository, organized by category. Fill these in before deploying the framework.

Search for `[YOUR_` across the repository to find every instance:

```bash
grep -r "\[YOUR_" . --include="*.md"
```

---

## 1. Identity and Communication

These placeholders define the email addresses your organization uses for communication and airlock transfers.

### `[YOUR_ORG_EMAIL]`

**What it is:** The dedicated organizational email account your agents use for communication and as the destination for airlock email transfers.

**Decision guidance:** This should be a separate account from your personal email — not your primary address. The framework is designed around a clean separation between your personal identity (clean side) and your sandbox organization (sandbox side). A purpose-built address like `your-org@gmail.com` or a custom domain address works well.

**Where it appears:** Operations Director role, capability policies for airlock and communication, reporting policy, security policy.

**Example value:** `my-sandbox-org@gmail.com`

---

### `[YOUR_PERSONAL_EMAIL]`

**What it is:** Your personal email address — the one agents send reports and escalations to, and the one you use to send materials into the sandbox via email airlock.

**Decision guidance:** This is your real email — the one you actually check. The President Agent sends session digests, weekly governance summaries, and escalation requests here. The Operations Director monitors the org email inbox for messages forwarded from this address.

**Where it appears:** Operations Director role, airlock policy, reporting policy, capability policies, security policy.

**Example value:** `you@yourdomain.com`

---

## 2. Infrastructure

These placeholders describe your sandbox host — the dedicated machine where agents run.

### `[YOUR_SANDBOX_HOST]`

**What it is:** A human-readable description of your sandbox compute host.

**Decision guidance:** This can be any dedicated machine: a Mac mini, a NUC, a cloud VM, a spare laptop, or a VPS. The key requirement is that it is dedicated to sandbox operations and not shared with your personal workloads. Replace this with a brief description of whatever you are using.

**Where it appears:** `policies/infrastructure/infrastructure-policy.md`

**Example values:** `Mac mini`, `Ubuntu NUC`, `cloud VM`, `dedicated server`

---

### `[YOUR_SANDBOX_HOSTNAME]`

**What it is:** The local network hostname for your sandbox host.

**Decision guidance:** Set this in your router's DHCP configuration so the machine always gets the same name on your local network. A descriptive, non-personal name is preferable. Must be stable — the framework requires a fixed hostname because policy documents reference it.

**Where it appears:** `policies/infrastructure/infrastructure-policy.md`, `policies/security/security-policy.md`

**Example values:** `sandbox.local`, `org-host.local`, `agent-box.local`

---

### `[YOUR_SANDBOX_IP]`

**What it is:** The fixed local IP address of your sandbox host.

**Decision guidance:** Set a DHCP reservation in your router so this machine always gets the same IP. This prevents the sandbox from operating with a dynamic address that changes between sessions. Choose an address outside your router's dynamic DHCP range.

**Where it appears:** `policies/infrastructure/infrastructure-policy.md`, `policies/security/security-policy.md`

**Example values:** `192.168.1.100`, `10.0.0.50`, `172.16.0.10`

---

### `[YOUR_CPU_GPU_SPECS]`

**What it is:** A brief description of your sandbox host's CPU and GPU.

**Decision guidance:** Used in the compute limits section to document what hardware the resource limits are calculated against. Fill in whatever your machine has. If your machine has no discrete GPU, you can omit the GPU reference.

**Where it appears:** `policies/infrastructure/infrastructure-policy.md`

**Example values:** `8-core CPU, integrated GPU`, `12-core CPU, 16-core GPU`, `AMD Ryzen 9, RTX 3060`

---

### `[YOUR_RAM]`

**What it is:** The total RAM on your sandbox host.

**Decision guidance:** Used to calculate per-agent memory limits and the host-level ceiling. The framework allocates most RAM to agents, reserving some for the OS and core tools.

**Where it appears:** `policies/infrastructure/infrastructure-policy.md`

**Example values:** `16GB`, `32GB`, `64GB`

---

### `[YOUR_STORAGE]`

**What it is:** The internal storage capacity of your sandbox host.

**Decision guidance:** Informational — documents what storage the sandbox operates on. Important if you are managing KB retention and archival with limited space.

**Where it appears:** `policies/infrastructure/infrastructure-policy.md`

**Example values:** `256GB SSD`, `1TB NVMe`, `500GB SSD`

---

### `[YOUR_EXTERNAL_STORAGE]`

**What it is:** Any external storage attached to your sandbox host.

**Decision guidance:** If you have external storage for the knowledge base or backups, document it here. If you have no external storage, remove this line from the infrastructure policy.

**Where it appears:** `policies/infrastructure/infrastructure-policy.md`

**Example values:** `2TB external USB3`, `4TB NAS share`, `none`

---

### `[YOUR_MAX_AGENTS]`

**What it is:** The maximum number of concurrent agent processes permitted on your sandbox host.

**Decision guidance:** This is a resource governance limit, not a hard OS limit. Set it based on your machine's RAM and how many agents you realistically expect to run simultaneously. The President Agent counts against this limit. A reasonable starting point is 3-5 for a machine with 16-32GB RAM.

**Where it appears:** `policies/infrastructure/infrastructure-policy.md`

**Example values:** `3`, `4`, `5`

---

### `[YOUR_RAM_PER_AGENT]`

**What it is:** The maximum RAM any single agent process may consume.

**Decision guidance:** Divide your usable RAM (total RAM minus OS overhead, roughly 4-6GB) by your max concurrent agents. This prevents any single runaway agent from starving the others. Round down to a sensible number.

**Where it appears:** `policies/infrastructure/infrastructure-policy.md`

**Example values:** `4 GB`, `6 GB`, `8 GB`

---

### `[YOUR_CPU_PER_AGENT]`

**What it is:** The maximum CPU cores any single agent process may use.

**Decision guidance:** Divide your total CPU cores by your max concurrent agents, keeping a few cores reserved for the OS. This is a soft governance limit, not a hard OS enforcement.

**Where it appears:** `policies/infrastructure/infrastructure-policy.md`

**Example values:** `3`, `4`, `6`

---

### `[YOUR_TOTAL_RAM_CEILING]`

**What it is:** The total RAM ceiling across all agent processes combined.

**Decision guidance:** This should be your total RAM minus OS overhead (typically 4-6GB for macOS/Linux). For example, on a 24GB machine, a ceiling of 18GB reserves 6GB for the OS. If you set this, the Security Steward is responsible for monitoring compliance.

**Where it appears:** `policies/infrastructure/infrastructure-policy.md`

**Example values:** `12 GB`, `18 GB`, `24 GB`

---

## 3. Financial Controls

These placeholders define the financial guardrails on autonomous spending. Think carefully about these — they are your primary protection against unexpected charges.

### `[YOUR_VIRTUAL_CARD_PROVIDER]`

**What it is:** The service you use to provision virtual credit cards for your sandbox wallets.

**Decision guidance:** Virtual card services let you create dedicated cards with per-merchant locks, transaction limits, and monthly caps. This separation ensures agent spending cannot reach your primary credit cards. Popular options include Privacy.com, Revolut virtual cards, or your bank's virtual card feature. The framework references this as the approved wallet provider.

**Where it appears:** `policies/finance/wallet-policy.md`, `roles/engineering-director.md`, `roles/operations-director.md`, `templates/role-template.md`

**Example values:** `Privacy.com`, `Revolut`, `Capital One Eno`

---

### `[YOUR_TX_LIMIT]`

**What it is:** The per-transaction spending limit for agent wallets.

**Decision guidance:** This is the maximum a single transaction may charge on an agent wallet. Set this conservatively — you can always raise it per-wallet at provisioning time. The goal is to bound the blast radius of any single unexpected charge. For API and SaaS usage, $25-$50 per transaction covers most legitimate use cases.

**Where it appears:** `roles/engineering-director.md`, `roles/operations-director.md`, `capabilities/software-development.md`, `policies/finance/wallet-policy.md`, `templates/role-template.md`

**Example values:** `$25`, `$50`, `$100`

---

### `[YOUR_MONTHLY_CAP]`

**What it is:** The monthly spending cap for agent wallets.

**Decision guidance:** This is the maximum an agent wallet may spend in a calendar month. Set this to an amount you would not be distressed to lose if something went wrong. For most sandbox operations, $50-$200/month covers legitimate API and SaaS costs while keeping exposure bounded.

**Where it appears:** `roles/engineering-director.md`, `roles/operations-director.md`, `capabilities/software-development.md`, `policies/finance/wallet-policy.md`, `templates/role-template.md`

**Example values:** `$50`, `$100`, `$200`

---

### `[YOUR_MAL]`

**What it is:** The Maximum Acceptable Loss — the worst-case financial exposure you could tolerate if a wallet were fully compromised.

**Decision guidance:** This should equal or be close to the monthly cap. It is the answer to: "If this wallet were drained to zero by a bad actor or runaway automation, what is the most I could lose?" Size your virtual card limits to enforce this. Any charge outside the pre-approved vendor list should trigger a High incident regardless of amount.

**Where it appears:** `roles/engineering-director.md`, `roles/operations-director.md`, `capabilities/software-development.md`, `policies/finance/wallet-policy.md`, `templates/role-template.md`

**Example values:** `$100`, `$200`, `$500`

---

## 4. External Accounts

### `[YOUR_IMAGE_GEN_ACCOUNT]`

**What it is:** A description of the account type used for image generation tools (DALL-E, Midjourney, Stable Diffusion) in the Creative Director capability.

**Decision guidance:** The Creative Director capability includes a bounded Article VI Identity Firewall exception allowing access to image generation tools via a personal account, subject to a CEO-approved generation budget. Replace this placeholder with a description of the account arrangement you are using (e.g., "CEO personal OpenAI account", "shared team account", "dedicated org account"). If you are not using shared personal accounts, remove this exception and replace with whatever account arrangement you are using.

**Where it appears:** `capabilities/creative-production.md`, `roles/creative-director.md`

**Example values:** `CEO personal OpenAI account`, `dedicated org account`, `shared team account`

---

## Review Date Placeholders

The capability policies contain `[YOUR_REVIEW_DATE]` placeholders where the original implementation had specific review dates. Fill these in with dates approximately 90 days from your activation date, or use a recurring cadence like "quarterly" or "every 6 months."

---

## After Customization

Once all placeholders are filled in, run the verification check to confirm no originals remain:

```bash
grep -r "\[YOUR_" . --include="*.md"
```

Then review the constitutional hierarchy one more time — Constitution, Governance Manual, Sandbox Operating Charter — to confirm the values you have chosen are consistent with each other and with your actual infrastructure and risk tolerance.
