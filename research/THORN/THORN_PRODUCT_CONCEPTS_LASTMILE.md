---
title: "THORN Product Concepts — Get-Me-Home Last Mile"
tags: [product-concepts, last-mile, get-me-home, thorn]
status: active
created: 2026-08-09
---

# THORN — Product Concepts (Get-Me-Home, Last-Mile Stranded)

**Agent:** THORN (Product Strategist)
**Date:** 2026-08-09
**Note:** These are THORN's four product concepts as actually shipped to the channel (post VEX process-flag correction), with flows, revenue, BOM and certification. Concept names: **TapRide**, **Anchor**, **Standing Order**, **Concierge Dispatch**.

---

## Strategic Frame (THORN)

**Build the summoner, not a payment product.** The research shows payment is already redundant (tap/cash/Opal/Cabcharge). The gap is *zero-device summoning* — the person CAN pay, they CANNOT initiate a ride because ride apps are phone-only.

**Design rules drawn from research:**
- No mandatory subscription (failure mode #2).
- Human-operator dispatch over nonexistent public ride APIs (13CABS/Uber/DiDi have no public booking API).
- LTE-M/NB-IoT (survives carrier sunsets better than 3G-era gear; iSIM = no SIM slot) IF hardware is used.
- Pay-without-phone at the point of ride.
- Zero-device on the user's side, at the station, with wallet + cash + Opal.

---

## Concept A: TapRide — Station Card-Tap Kiosk

**Core Mechanism:** A touchscreen kiosk on the platform holds the connectivity the rider lacks; tap a contactless card → kiosk dispatches a taxi and settles it.

**User Flow (5 steps):**
1. Tap contactless card at station exit.
2. Enter/select home suburb (or saved default route per card).
3. Kiosk books over the 13CABS phone line, shows driver ETA/plate/booking code.
4. Driver verifies code; fare pre-authorised to the regulated rank/hail max (no surge).
5. Ride; card settles.

**What the user needs:** a wallet card + Opal for the transit leg. No keychain, no device carried.

**Revenue Model:** ~A$1.50/dispatch take-rate + station placement fees + premium guarantee tier.

**Key Risk:** capital per hub, vandalism/upkeep (Moochies graveyard), thin late-night taxi supply (the exact risk hour).

**MVP Scope:** one station, NFC reader + tablet + payment SDK + 13CABS call-out. ~3 weeks.

**Cert:** the *kiosk* needs ACMA EMC + PCI-compliant POS; **no consumer device, no carrier type-approval** — dramatically lighter than a keychain.

---

## Concept B: Anchor — Keychain LTE-M/NB-IoT SOS Button  *(v2, not v1)*

**Core Mechanism:** the user **carries** the button on their keys; one press pings our backend over a Telstra IoT rail, which books a home taxi via the 13CABS phone line and charges a card already on file. Button initiates; backend summons.

**User Flow (5 steps):**
1. Pair once on a working phone (iSIM → account/card/home).
2. Carry daily, opt-in. No charger drama (long standby, but see risk).
3. Hold 2s at the station.
4. Device SMS-es backend over Telstra LTE-M/SMS rails.
5. Backend books home fare via 13CABS; driver picks up; card on file settles.

**What the user needs:** the keychain + a card already on file.

**Revenue Model:** A$29 one-off (no forced sub) + ~A$1.50/dispatch.

**Key Risk:** **co-lost object** (keys/wallet/phone vanish together), dead battery on a rarely-charged button (PERS/watch graveyard), carrier sunset = brick (Telstra 3G-2024 lesson). Honest place = v2.

**MVP Scope:** stock dev board (ESP32-S3 + Sequans GM02SP LTE-M/NB-IoT + GNSS), one button, SMS → backend → 13CABS. ~4 weeks.

**BOM (indicative AUD, ~50–100k units):** Sequans Monarch 2 GM02S-class module (iSIM, EAL5+, 2.2V single-rail) A$15–25 · MCU A$3–6 · battery A$2–5 · PCB+antenna+button+enclosure A$10–18 · assembly/test A$8–12 → **≈ A$40–60 landed**.

**Cert (AU):** ACMA General Equipment Rule + RCM + TLC Labelling Notice + **carrier iSIM type-approval** (Telstra/Optus/Vodafone) + UN38.3 battery → **🔴 A$15–50k + months**. This gate, not the BOM, is the cost.

---

## Concept C: Standing Order — Pre-Committed Home Route *(ON-DEMAND, non-hardware)*

**Core Mechanism:** commit a default station→home route + funding once (when a phone works); the trigger is **physical and on-demand** — walk to a rank and quote a code, or use any landline. No app, no auto-dispatch, fires only when invoked.

**User Flow (5 steps):**
1. Set up once online (card + home + fixed regulated fare).
2. Phone lost → walk to rank (zero-device summon).
3. Hand a physical card / quote a memorized code (the *brain-credential*).
4. Driver verifies against the standing order.
5. Fixed fare charged to the pre-authorized account, no phone.

**What the user needs:** wallet + a pre-registered account.

**Revenue Model:** A$4–6/mo membership (guarantee-fee economics).

**Key Risk:** rank-density outside the CBD/night; verification needs a surviving credential (co-lost trap). Needs a rank-coverage map + a **no-credential fallback** before pricing. Brain-credential is co-lost-proof but NOT **panic-proof** (see stress-test: second-party-held code fix).

**MVP Scope:** no hardware; account + card-linking + 13CABS pre-book + one landline + driver code check. ~2 weeks.

---

## Concept D: Concierge Dispatch — Phone-Line-First (travellers/visitors)

**Core Mechanism:** a pre-funded get-home account; summoning over *any* reachable voice line; operator fixes fare + dispatches to the account, payment entirely off-phone.

**User Flow (5 steps):**
1. Pre-fund + save address.
2. Phone lost → reach any payphone/public line.
3. Call concierge number.
4. Operator dispatches a cab to the pre-funded account.
5. Ride home; settles from account.

**What the user needs:** pre-funded account + any working voice line.

**Revenue Model:** A$5–8/use + 5% mark-up; natural for corporate/travel expense programs.

**Key Risk:** **depends on a line/device existing** — fails strict no-help test; public-payphone infra in decline.

**MVP Scope:** no hardware; calls-in → fixed-fare routing → payment wrapping 13CABS. ~3 weeks.

---

## THORN Internal Ranking (after stress-test)

1. **Standing Order (C)** — lead product: the only concept clearing **no-help + co-lost (brain-credential) + zero-cert** simultaneously. Rebuilt with a **second-party-held code** (panic-proof) after VEX's cognitive-fragility objection.
2. **TapRide (A)** — zero-prep / co-lost-resistant companion; parked as infrastructure, not a launch wedge.
3. **Anchor (B)** — keychain, v2 only behind the A$15–50k cert gate.
4. **Concierge (D)** — a layer of Stranded Fund, not stand-alone; fails strict no-help.
