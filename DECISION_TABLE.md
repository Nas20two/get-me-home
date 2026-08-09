# Decision Table — 4 Adoption Paths

## The "No-Help" Test
Every concept was tested against: *"Does this get the person home without asking a stranger for help, with zero internet-connected devices?"*

## The 4 Adoption Paths

| Path | Mechanism | Concepts | Verdict |
|------|-----------|----------|---------|
| **Contact point** | A third party with their own phone funds and dispatches the ride live | Stranded Fund, Concierge Dispatch | ✅ **SHIP FIRST** |
| **Surviving credential** | A pre-committed home route, triggered by a physical token or memorized code | Standing Order, Home Button | ⚠️ Needs work |
| **Capex** | Station infrastructure (kiosk reads card, dispatches taxi) | TapRide, Last-Mile Assist | ❌ Abandon |
| **None** | Use existing incumbents (taxi rank + 13CABS) | — | Always available |

## Full Verdict Matrix

| Concept | Owner | Type | Verdict | Why |
|---------|-------|------|---------|-----|
| **Stranded Fund** | SATORI | Service | ✅ **Ship first** | Zero hardware, zero ACMA, near-zero cost, rides existing rails |
| **Concierge Dispatch** | THORN | Service | ✅ **Shippable** | Same as Stranded Fund; merge into one product |
| Key-Ride | SATORI | Hardware | ⚠️ Needs work | Wallet dies with phone; no confirmation loop; ACMA gate |
| Home Button | SATORI | Hardware | ⚠️ Needs work | Ally is single point of failure; re-skins incumbent |
| Ride-Home | SATORI | B2B Service | ⚠️ Needs work | Identity proof is fatal; better as add-on to Cabcharge |
| TapRide | THORN | Infrastructure | ⚠️ Needs work | Design unverified; same co-lost-wallet trap |
| Last-Mile Assist | SATORI | Infrastructure | ❌ Abandon | Duplicates existing taxi rank; capital-heavy |
| Anchor | THORN | Hardware | ❌ Abandon | Misread — same as Key-Ride hardware |
| Standing Order | THORN | Service | ❌ Abandon | Solves predictable commute, not unplanned crisis |

## The Single Insight That Unblocks Everything

**"The co-lost object."**

Phone + wallet + keys disappear together. Any design requiring a surviving physical credential or payment instrument at the scene loses the person it's built for.

**The fix:** Let a third party with their own phone fund and pay the ride live. This dissolves:
- The prep dependency (someone else pays)
- The scam-suspicion objection (known ally, not stranger)
- The lost-wallet trap (payment happens on the ally's phone, not at the scene)

## VEX's Meta-Call (Aug 9, 2026)

> "Further critique has negative marginal value from here. The risk is iteration-paralysis, not under-rigour. The honest resolution is empirical: stand up Standing Order + Stranded Fund in parallel (~2 weeks, no hardware), spend the first week on the single gating dependency (a fleet partner accepting the lookup), and let adoption + funnel data pick."

## SATORI's Key Data

- Australians lose ~**1,370 smartphones/day**, ~A$755M/yr in replacements
- Average commute ~37 km / 64 min, 30% by train
- Last-mile fare (Sydney, regulated rank/hail): ~A$19–21 for 5km, no surge
- No public data exists for "people stranded at the station after losing their phone" — the 2-week build is the only way to produce this datapoint