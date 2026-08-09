---
title: "Product Concepts: Phone-Loss, Stranded, Last-Mile Get-Home"
tags: [product-concepts, last-mile, sos-hardware, get-me-home]
status: active
created: 2026-08-09
---

# Product Concepts — "Stranded at the Last Mile" (post-research ideation)

**Basis:** `RESEARCH/PHONE_LOSS_STRANDED_LASTMILE.md` (2026-08-09). Concepts build on the *documented* channels that already work phone-less (taxi ranks/hail with regulated fares; phone booking 13 2227 / 131008; 24/7 monitoring centres), the documented infrastructure (Telstra IoT SIM + SMS API, contactless/cash/Cabcharge payment, Opal for transit only), and on the *documented* failure modes to avoid (carrier sunsets like Telstra 3G 2024; subscription/ PERS churn; redundancy vs smartphones; hardware/SIM reliability failures à la Moochies).

Design rules drawn from the research:
1. **No mandatory recurring subscription** — the #2 repeated failure mode (churn, PERS/wearable graveyard).
2. **Prefer human-operator dispatch** over a public ride API (none exists for 13CABS; Uber/DiDi APIs assume a rider account + payment the stranded user may not have).
3. **Telecom future-proofing** — design on LTE-M/NB-IoT (survives 3G-style sunsets; iSIM = no SIM slot).
4. **Pay without a phone** at the point of ride: pre-paid wallet / Cabcharge account / contactless / cash.
5. **Include a human with a phone** as first-resort authority where possible (caregiver/family/employer).

Prices are indicative AUD; dev-board ancho: DPTechnics Walter (ESP32-S3 + Sequans GM02SP LTE-M/NB-IoT + GNSS) A$120.85 retail inc GST (core-electronics.com.au). Volume/supplier/BOM numbers need quotes.

---

## Concept 1 — "Key-Ride" keychain Last-Mile SOS button (hardware + operator dispatch) — FLAGSHIP

**What:** A keychain-sized LTE-M/NB-IoT button. One press = GPS position + pre-stored Home address goes to a 24/7 human dispatch hub that books a taxi to the station rank and pays via the user's pre-paid ride wallet. No phone, no app-at-scene, no subscription.

**User flow**
1. **Setup (5 min, at home, once):** pair via companion app/web owned by the user (or caregiver). Store Home address + typical destination; link a payment method (pre-paid "ride wallet", Cabcharge account, or saved card).
2. **Daily commute** as normal; phone in pocket or lost.
3. **Stranded at station:** press-and-hold button 2s (short press cancels). LED + vibration confirm.
4. **Transmit:** device sends GPS fix + destination + ride preference over LTE-M (tiny data) to dispatch hub. Telstra IoT/NB-IoT + SMS API are the documented rails.
5. **Dispatch:** human operator (medical-alert model) confirms, books a taxi to the station rank via phone network (13CABS 13 2227 / 131008 / partner), charged to the pre-paid wallet.
6. **Ride + pay:** user walks to rank, boarded by account/name, pays at the terminal via wallet/contactless — no device needed.
7. **Notify:** completion + fare SMS/notify to the user's registered contact (Telstra SMS API). Caregiver optionally copied.

**Revenue model:** hardware margin (retail ~A$140–190) + per-ride dispatch fee (flat ~A$5–8 or ~8–12% of fare, drawn from the wallet) + float on pre-paid balance. Optional low-cost priority tier. **No mandatory monthly fee.**

**BOM (indicative AUD, volume ~50–100k units):**
- LTE-M/NB-IoT + GNSS + iSIM module (Sequans Monarch 2 GM02S class) — A$15–25
- Low-power MCU + flash — A$3–6
- Battery (coin/LiPo) — A$2–5
- PCB + antenna + button + enclosure + split-ring/strap — A$10–18
- Assembly + test — A$8–12
- **Total landed BOM + assembly ≈ A$40–60/unit.** Proto (Walter dev-board based) ≈ A$120–150. Volume quotes required.

**Certification (Australia):** ACMA — EMC + radio testing (Radiocommunications (General Equipment Rule)) + RCM labelling + supplier registration; Telecommunications Labelling Notice if connecting to a network; **carrier type-approval** (Telstra/Optus/Vodafone) for an iSIM device; battery transport/safety (UN38.3). Indicative cert + registration budget A$15–50k, lab quotes needed.

**Risk notes:** same device shape as Moochies (reliability/SIM/support must be engineered out); LTE-M long-term (offset 3G lesson); operator cost per ride is the margin risk.

---

## Concept 2 — "Stranded Fund": Opal-for-taxis pre-paid wallet + SMS dispatch (service-only, ZERO hardware/cert)

**What:** A prepaid ride wallet + a phone-number (SMS/short code) that dispatches a taxi to a location and pays from the wallet. Pure service layer on top of existing phone-booking + payment rails. Reaches people who don't want/carry a device.

**User flow**
1. **Top up** (app/web/physical top-up card/transfer): pre-load funds into the "Stranded Fund" ride account (think pre-paid opal / transportnsw pre-paid fare model, but for taxis).
2. **Stranded, no phone:** use the service's **SMS short code** from *any* working phone (a bystander's, a payphone, a landline at the station) — text pick-up location, or simply call the operator line.
3. **Dispatch + pay:** operator books via the phone network to the rank; fare taken from wallet; no terminal payment needed.
4. Notify contacts; top up again anytime.

**Revenue model:** float on pre-loaded balance + small per-ride dispatch fee (flat or %). Recurring optional monthly plan (not required). No hardware cost; near-zero marginal per-ride cost.

**BOM/cert:** N/A — no device. Complies with none of the ACMA/carrier cost.

**Risk notes:** depends on the stranded person having *any reachable phone* for the SMS leg (addresses the "no *my* phone" case, not the "no phone at all" case); strong for the common case in the problem statement where bystanders/landlines exist.

---

## Concept 3 — "Home Button for the Phone-Less": caregiver-linked SOS (family model)

**What:** Like Concept 1 but with the **dispatch authority held by a designated human who HAS a phone** (parent/partner), not by the system's payment. Borrows the Apple-Watch-For-Your-Kids / Spacetalk parental model and the medical-alert operator model. Targets elderly, kids, and anyone whose ally always has a device.

**User flow**
1. **Pair** the phone-less person's keychain/pendant with an **ally's phone app**. Ally pre-sets home/work + linked payment.
2. **Press** → hub routes to **ally's phone** (SMS/call/app) + optionally to operator if ally unavailable.
3. **Ally confirms** the ride; taxi booked to the rank and paid from the **ally's account**.
4. Notify + receipts to ally; caregiver always in the loop.

**Why it survives:** the person who pays and dispatches reliably has a phone — removes the "stranded person must be provisioned" dependency; strong privacy story (ally = family).

**Revenue model:** per-ride fee or low-cost annual family plan (~A$30–60/yr), hardware margin.

**BOM:** simpler than Concept 1 — no payment capture on device → smaller battery, longer life. Same module family ≈ A$35–50/unit + assembly. **Cert:** same ACMA/RCM + carrier type-approval path as Concept 1.

---

## Concept 4 — "Last-Mile Assist" hub: station kiosk + landline operator (zero-preparation)

**What:** Infrastructure at/near transit hubs — a **landline/hi-volume kiosk, staffed or self-serve, that books a taxi charged to cash or contactless at the terminal** — leveraging the documented travel-consular assistance, subsidised-taxi scheme, and phone-booking rails. Serves the **zero-prep** stranded person (the one who never set up a wallet).

**User flow**
1. Stranded person walks to the "Last-Mile Assist" hub (station concourse, near taxi ranks).
2. Picks up a handset / kiosk screen → operator asks destination → quotes the regulated rank/hail fare.
3. Taxi booked to rank **from a financial standing start** — pay by **cash or contactless card at the kiosk terminal** (AusPayNet/eftpos rail), or request a Cabcharge/pre-paid redemption.
4. Boarded at rank; no app, no pre-registration.

**Revenue model:** per-use fee (~A$5) + subsidised/public-partnership model (transport agency / PSO / council funding — ties to NSW Taxi Transport Subsidy Scheme precedent); advertising on the hub.

**BOM/cert:** no consumer device — kiosk/landline infrastructure procurement + point-of-sale terminal (PCI) + telecom lines. No consumer ACMA/carrier-type-approval burden beyond sourcing a commercial device.

**Risk notes:** capital-heavy, venue-dependent; strongest as a public/partner play, weakest as a stand-alone consumer startup.

---

## Concept 5 — "Ride-Home" corporate travel & insurer add-on (B2B on existing rails)

**What:** A B2B service riding existing **Cabcharge-style corporate/account and insurer** rails. A member (employee/traveller/insured) who is stranded device-less gets a taxi dispatched by an operator and billed to the **company/insurer account** — no personal device or personal payment setup.

**User flow**
1. Employer/insurer enrols members; each member gets a corp ride account + crisis-dispatch line.
2. Stranded → member (or bystander/venue staff) calls the line / scans a member card at the hub → operator dispatches via the phone network, billed to the account.
3. Consolidated invoicing to client; duty-of-care/insurer log.

**Why it works:** rides the **existing corporate travel-payment infrastructure** (Cabcharge), low integration cost, recurring B2B revenue, and aligns with employer duty-of-care that already worries about stranded staff.

**Revenue model:** per-ride fee + monthly per-seat/licence to corporates; insurer-partnered premiums. Recurring B2B (contrasts with consumer churn risk).

**BOM/cert:** N/A (service); depends on corporate account rails, not new hardware.

---

## Selection summary (honest, documented basis)
- **Closest to the research's documented rails with the fewest new failure surfaces:** Concept 2 (pure service, zero cert cost) and Concept 5 (B2B, rides Cabcharge).
- **Highest fit to the *literal* problem ("zero internet devices, no phone")**: Concept 1 / Concept 3 (true device-independent dispatch) — at the cost of hardware BOM + ACMA/carrier cert (Concept 1) or reliance on an allied phone (Concept 3).
- **Zero-preparation / public-good:** Concept 4 (infrastructure/partnership).

All figures are indicative; BOM and certification need supplier/lab quotes. No concept asserts a public 13CABS/Uber/DiDi API that the research showed does not exist — dispatch is via phone-network booking + operator, which is documented to work phone-less.
