# Buzz Agents — "Get Me Home" Product Brainstorm

**Created:** 2026-08-09
**Platform:** Buzz v0.5.3
**Community relay:** wss://nasyhub.communities.buzz.xyz
**Orchestrator:** NaSy (human bridge — OpenClaw ↔ Buzz plugin was broken)

## The Incident

NaSy lost his phone in his manager's car on Friday evening (Aug 7, 2026) after a team outing. He didn't realize until he was on the train. He had his wallet (ATM card, Opal card, cash), a laptop with no internet, and no way to book a cab — all ride apps require a phone. He borrowed a stranger's phone to call his wife, who picked him up. The phone was retrieved from the manager on Sunday.

## The Three Agents

| Agent | Name | Role | Prompt |
|-------|------|------|--------|
| 🧠 | **SATORI** | Researcher | Maps existing solutions, failed attempts, data, infrastructure |
| 🗡️ | **THORN** | Product Thinker | Generates 3-5 product concepts with user flows, revenue, BOM/cert |
| ⚖️ | **VEX** | Critic | Stress-tests every concept, finds failure modes, gives verdicts |

## Constraints Given to All Agents

1. **No asking strangers for help** — the solution must get the person home without relying on a stranger's goodwill
2. **Zero internet connectivity** — the person may have no internet-connected devices
3. **Hardware allowed** but limited to keychain-sized, low-complexity devices (LTE-M/NB-IoT SOS buttons using off-the-shelf modules)
4. **No Apple Watch, phones, or complex hardware**
5. **Must work with only what someone already carries** (wallet, cards, keys)

## Workflow

1. NaSy posted the incident summary in `#get-me-home` channel
2. `@SATORI` ran research → 7 areas, sourced
3. `@THORN` generated concepts → 5 concepts (SATORI) + 4 concepts (THORN)
4. `@VEX` stress-tested all 9 → verdicts, meta-call
5. All three converged on Stranded Fund + Concierge Dispatch as the shippable MVP

## Key Files

- `~/Desktop/buzz-agents-get-me-home.md` — Original agent specs file
- `research/` — Full agent outputs in this repo