# THORN — Product Concepts (as inferred from channel)

**Agent:** THORN (Product Strategist)
**Date:** 2026-08-09
**Note:** THORN's full concept designs were names only in the relay (not posted with flows, revenue, or specs before VEX's stress-test). The names inferred from the channel are: **TapRide**, **Anchor**, **Standing Order**, **Concierge Dispatch**. Below are THORN's concepts as reconstructed from the strategic framing.

---

## THORN's Strategic Reframe

**Build the summoner, not the payment product.** Payment is already redundant (tap/cash/Opal/Cabcharge). The gap is zero-device summoning.

### THORN's Key Insight (from the conversation)

> "The market doesn't need a new payments product — payment infrastructure is already redundant. It needs a zero-device summoner."

### THORN's Internal Ranking

1. **Standing Order** — lead product (pre-committed home route, rank trigger, non-hardware)
2. **TapRide** — zero-prep companion (station kiosk)
3. **Anchor** — keychain hardware (v2 only)

---

## Concept A: TapRide — Station Kiosk

**Core Mechanism:** A card-tap kiosk on the platform dispatches a taxi — the kiosk holds the connectivity the rider lacks.

**User Flow:** Tap contactless card at station exit → enter/select home suburb → kiosk books over the 13CABS phone line + shows driver ETA/plate/code → driver verifies code, kiosk pre-authorised the fixed home fare (regulated rank/hail max, no surge) → ride, card settles.

**What the user needs:** wallet card + Opal. No keychain.

**Revenue:** ~$1.50/dispatch take-rate + station placement fees + premium guarantee tier.

**Key Risk:** capital-heavy per-hub, vandalism/upkeep (Moochies graveyard), thin late-night taxi supply.

**MVP Scope:** one station, NFC reader + tablet + payment SDK + 13CABS call-out. ~3 weeks.

## Concept B: Anchor — Keychain LTE-M/NB-IoT SOS Button

**Core Mechanism:** One press pings backend over Telstra LTE-M rail → backend books a home taxi + charges card on file. Button initiates; backend summons.

**User Flow:** pair once on a working phone (iSIM→account/card/home) → carry daily, opt-in → hold 2s at station → device SMS-es backend → backend books via 13CABS, driver picks you up, card settles.

**What the user needs:** keychain + card already on file.

**Revenue:** A$29 hardware one-off (no forced sub; optional dispatch credit) + ~$1.50/dispatch.

**BOM/Cert:** Monarch 2 GM02S production module ~A$15–25 @ volume → ~A$35–50 landed. ACMA: General Equipment Rule + RCM + TLC Labelling Notice, penalties 100–500 penalty units. Budget months + A$15–50k for type-approval before retail.

**Key Risk:** battery + subscription/abandonment trap + carrier sunsets (3G-2024 lesson).

## Concept C: Standing Order — Pre-committed Home Route

**Core Mechanism:** Commit a default station→home route + funding in advance; the trigger is a physical zero-device channel — taxi rank or landline — never an app.

**User Flow:** set up once online (card + home + fixed fare) → on loss walk to rank (zero-device summon) → hand physical card / quote code → driver verifies against standing order → fixed-fare charged, no phone.

**What the user needs:** wallet + pre-registered account.

**Revenue:** A$4–6/mo membership (guarantee-fee economics).

**Key Risk:** ranks are sparse outside CBD — model collapses for the suburban majority.

**MVP Scope:** account + card-linking + 13CABS pre-book + one landline + driver code check. ~2 weeks.

## Concept D: Concierge Dispatch — Phone-Line First Last Mile

**Core Mechanism:** Pre-funded get-home account; summoning over any reachable voice line (13CABS already does this); payment entirely off-phone.

**User Flow:** pre-fund + save address → phone lost → reach any payphone/public line → call concierge → operator fixes fare + dispatches to pre-funded card → ride home, settles from account.

**What the user needs:** pre-funded account + any voice line.

**Revenue:** A$5–8/use + 5% account mark-up; natural for corporate/travel programs.

**Key Risk:** declining public-payphone infra — if they can't reach a line, premise weakens.

**MVP Scope:** no hardware; calls-in → fixed-fare routing → card settlement wrapping 13CABS. ~3 weeks.