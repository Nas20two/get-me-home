# Get Me Home 🏠🚖

**You lose your phone. You're stranded. You can pay, but you can't summon a ride.**

Every ride app is phone-only. Your wallet has cash and cards. The Opal card got you to the station. But the last mile (station → home) is impossible without a phone.

This repo explores product concepts that solve this problem — non-hardware, keychain-hardware, and infrastructure approaches — stress-tested by three independent AI agents.

## The Consensus MVP

**Stranded Fund + Concierge Dispatch** — zero hardware, zero ACMA burden, near-zero marginal cost. Rides existing phone-booking rails (13CABS/131008). A pre-funded ride wallet + an operator line that dispatches a taxi from any working phone.

**The one insight that unblocked everything:** *"The co-lost object."* Phone + wallet + keys disappear together. The fix: let a third party with their own phone fund and pay the ride live.

## Repository Structure

| File | What |
|------|------|
| `MVP_SPEC.md` | Merged Stranded Fund + Concierge MVP spec |
| `DECISION_TABLE.md` | 4 adoption paths, agent verdicts, build guidance |
| `BUILD_PLAN.md` | 2-week parallel build plan |
| `AGENTS.md` | Buzz agent setup (SATORI, THORN, VEX) |
| `research/SATORI.md` | Full market research output |
| `research/THORN.md` | Product concepts |
| `research/VEX.md` | Stress-test critique and verdicts |

## Origin

The idea was born from a real incident: Friday August 7, 2026 — a team outing, a phone dropped in a manager's car, and an hour-long stranded-at-the-station ordeal. The only way out was borrowing a stranger's phone to call for a ride home.

**Three Buzz agents** (SATORI, THORN, VEX) were set up to brainstorm the problem independently. This repo archives their combined output.

## License

MIT — this is an open product concept. Build it, fork it, improve it.