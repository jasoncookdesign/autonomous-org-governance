# Infrastructure Policy

Policy governing the sandbox host, network identity, account separation, approved software environment, remote access, and compute limits.

Infrastructure is an implementation detail -- governance is the root of trust -- but infrastructure decisions affect the security of every capability.

## Contents

| File | Description |
| --- | --- |
| `infrastructure-policy.md` | Sandbox host specs, network configuration, account separation rules, approved software environment, backup rules, and prohibited infrastructure actions |

## Current Sandbox Host (Summary)

- **Hostname:** `[YOUR_SANDBOX_HOSTNAME]` / **IP:** `[YOUR_SANDBOX_IP]`
- **Remote access:** Tailscale (replaceable with any VPN/remote access tool), macOS SSH
- **Compute limits:** See `infrastructure-policy.md` for configurable limits
