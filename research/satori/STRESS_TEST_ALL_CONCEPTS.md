---
title: "Stress-Test: All Get-Me-Home Product Concepts (SATORI + THORN sets)"
tags: [stress-test, product-concepts, no-help-test, get-me-home]
status: active
created: 2026-08-09
---

# Stress-Test of All Concepts (requested 2026-08-09 by NaSy)

Scope: apply a **verdict (SHIP NOW / NEEDS WORK / ABANDON)** to all 9 concepts (SATORI: 5, THORN: 4), with specific failure modes, the **no-help test**, and ACMA/cert burden for anything hardware.

Basis: `RESEARCH/PHONE_LOSS_STRANDED_LASTMILE.md` + `PLANS/PRODUCT_CONCEPTS_LASTMILE.md`. THORN's four (TapRide, Anchor, Standing Order, Concierge Dispatch) are stress-tested **provisionally from their names + the shared research**, because THORN's full write-up was **not retrievable from my session's relay history** — flagged per concept, THORN to confirm.

## The "no-help" test (applied to every concept)
A concept **passes** the no-help test only if, in the *exact* incident (person at station, **zero internet devices**, wallet with cash/cards + Opal), it provides help they **could not already get by walking to a taxi rank and paying with cash/card**. A concept **fails** it if it requires, at the moment of need, any one of: the person's own device, an app, a pre-staged subscription/set-up they may not have done, a working phone (even someone else's absent), a reachable connected third party, or infrastructure that is not present where they are.

---

## SATORI set (full-fidelity — I own these)

### C1 — Key-Ride: keychain LTE-M/NB-IoT SOS + operator dispatch
- **Verdict: NEEDS WORK.** Not SHIP (hardware+cert+reliability are heavy and the marginal value over a rank+cash is narrow); not ABANDON (it is the only concept that genuinely serves the *literal* zero-device case at scale once set up).
- **Failure modes:** (a) **loss-coupling** — it's a *keychain*; if the phone was lost/stolen the keychain is often too, and if the wallet was stolen the ride-wallet goes with it → device fails in exactly the scenario it targets; (b) **battery flat** on a rarely-charged button; (c) **zero-preparation** — a user who never paired/funded gets no help; (d) operator cost/quality + accountability; (e) LTE-M coverage gaps + the carrier-sunset lesson (Telstra 3G 2024, RESEARCH §2); (f) iSIM provisioning friction; (g) **Moochies-class reliability/SIM/support risk** (RESEARCH §2).
- **No-help test:** **Partially fails.** Without the pre-paired, charged, funded device on their person, the user is no better off than rank+cash. With it, it adds value only where there is no rank, no cash, night, or disabled/isolated — a real but narrow sliver.
- **ACMA/cert burden:** **Heavy.** ACMA EMC + radio (General Equipment Rule) + **RCM** labelling + supplier reg; Telecommunications Labelling Notice; **carrier type-approval** (Telstra/Optus/Vodafone) for the iSIM; battery UN38.3. Indicative A$15–50k + recurring, plus carrier engineering time (RESEARCH §5).

### C2 — Stranded Fund: pre-paid ride wallet + SMS/operator dispatch (service-only)
- **Verdict: SHIP NOW (as the service MVP).** Lowest cost, zero hardware/cert, and it covers the most common real-world case. Should be the back-end service that hardware concepts later ride on.
- **Failure modes:** (a) needs **any working phone** at T=0 for the SMS leg — a bystander's/payphone/landline — so it does **not** serve a truly phone-free perimeter (self-acknowledged in my C2 write-up); (b) **financial-auth/fraud**: an SMS "I'm stranded" that dispatches a paid ride must be authenticated or a stolen passcode/wallet can be drained → needs caller-pin / velocity controls; (c) **stored-value regulation** (pre-paid float may carry consumer-credit/stored-value obligations, cf. Cabcharge/regulated prepaid models); (d) terminal payment or operator-funded account bridge still needs a defined rail.
- **No-help test:** **Passes the common case** (bystander/landline/call-box exist), **fails the literal zero-device perimeter.** Frame as broad coverage, not total.
- **ACMA/cert burden:** **None** for hardware. Service-layer compliance only (payments/stored-value, privacy). Fastest path to revenue and to proving demand.

### C3 — Home Button / caregiver-linked SOS (family model)
- **Verdict: NEEDS WORK.** Strongest social-consumer story (the paying/dispatching party reliably has a device) but two-sided provisioning + hardware + cert make it heavier than C2 and it depends on an ally being reachable.
- **Failure modes:** (a) **ally unavailability** — asleep, away, their phone also dead/flat, or no answer → stranded user fails in the moment; (b) same loss-coupling/battery/set-up failures as C1 for the worn device; (c) two-user onboarding friction and family pricing; (d) reliability of the worn device (Moochies lesson); (e) who pays if ally hasn't funded.
- **No-help test:** **Partially passes** — robust *if and only if* the designated ally answers and has funded. Fails if the ally is unreachable (a realistic failure exactly at the moment of need).
- **ACMA/cert burden:** **Heavy** (same ACMA/RCM + carrier type-approval + battery path as C1), though a simpler device (no on-device payment capture) gives a smaller battery/lower cost. Same A$15–50k class estimate.

### C4 — Last-Mile Assist: station kiosk + landline operator hub
- **Verdict: NEEDS WORK — as a stand-alone startup it is the closest to ABANDON.** Genuinely passes the no-help test (zero-preparation, zero-device) but it is capital-heavy, venue-dependent infrastructure that is really a **public-transport/PSO program or partnership play**, not a venture-rate product (thin unit economics, high capex, long procurement).
- **Failure modes:** (a) only helps where a hub exists (not at every station/stop); (b) capex + venue/landlord/transit-agency dependence; (c) PCI terminal + insurance + staffing or kiosk uptime; (d) usage lottery (low daily takers outside disruption events); (e) the pay-by-cash/contactless-at-terminal already exists at many ranks — hub must add operator-dispatch value, not just a terminal.
- **No-help test:** **Passes outright** where infrastructure exists — the only concept that serves the totally unprepared, zero-device person by design.
- **ACMA/cert burden:** **Minimal for the operator** — no consumer CE; commercial kiosk/landline/VoIP + PCI procurement, no ACMA consumer-class compliance tail.

### C5 — Ride-Home: corporate travel & insurer B2B add-on (Cabcharge rails)
- **Verdict: NEEDS WORK.** Viable, recurring B2B revenue and rides existing corporate rails, but it is partnership-dependent and low-frequency per member, and the trigger still needs a reachable phone/bystander.
- **Failure modes:** (a) **dependency on Cabcharge/corporate account rails** (not a product you own); (b) low event frequency per member undermines per-seat licence pricing; (c) **duty-of-care / insurer liability** when a dispatch fails; (d) the stranded member still needs a device (bystander/venue/phone line) to *initiate* — doesn't solve the zero-device perimeter alone.
- **No-help test:** **Partially fails** — needs a phone/bystander/venue contact to trigger; corporate account handles payment only after help is summoned.
- **ACMA/cert burden:** None (service; rides existing rails).

---

## THORN set (PROVISIONAL — from names + research only; THORN's write-up not retrievable in my session)

> Flag: I could not retrieve THORN's detailed concepts from the relay; these verdicts rest on the concept names and the shared research, not on THORN's actual specs (BOM/flows/revenue). THORN should confirm or correct.

### T1 — TapRide (name suggests: contactless/NFC tap-to-ride activation, Opal-style or via a physical card)
- **Verdict (provisional): NEEDS WORK.**
- **Read/intent:** likely a tap-a-card/kiosk to summon+pay a ride on existing contactless rails.
- **Failure modes (from research):** the **documented gap is that Opal/contactless pays transit but NOT taxis** (§7) — so a "tap to ride" only works if new tap readers are installed at ranks/hubs (infrastructure) or it re-uses a card the taxi industry already accepts (Cabcharge) — otherwise it has no payment rail to tap onto. If it still needs a phone to associate the tap, it fails the no-help test.
- **No-help test:** **Fails** if tapping requires a reader that isn't at the person's location, or a phone to complete the trip. Passes only as a physical-card + cab-charge-style account that a driver terminal already accepts.
- **ACMA/cert burden (provisional):** **Moderate if hardware/NFC** — contactless terminals/NFC devices need ACMA EMC/radio + RCM and PCI/PIN compliance if handling cards; negligible if it's purely the *existing* card-acceptance rail.

### T2 — Anchor (name suggests: a fixed home/work "anchor" base or device)
- **Verdict (provisional): NEEDS WORK.**
- **Read/intent:** likely a stationary base/anchor the user pre-configures (home location/wallet) that dispatches on their behalf.
- **Failure modes (from research):** a **fixed anchor can't travel with the stranded person** — the T=0 event is *away* from home/work (they're at a station), so a home-only anchor can't know where they are or summon from there unless paired with a worn/mobile element (which reintroduces C1's device burden). If the anchor is actually a worn/linked device, it inherits loss-coupling + battery + cert.
- **No-help test:** **Fails as a fixed-only device** (not on scene); **passes only as a base that coordinates a worn/mobile link**, i.e. it collapses into C1/C3.
- **ACMA/cert burden (provisional):** **Wi-Fi/BT home device** is a lighter ACMA class than cellular but still needs RCM EMC/radio; **any cellular link needs the full carrier type-approval + cert** as in C1.

### T3 — Standing Order (name suggests: recurring/pre-scheduled standing ride order)
- **Verdict (provisional): NEEDS WORK / lightweight — closest to SHIP if it's a pre-scheduled service.**
- **Read/intent:** likely a standing pre-booked ride pattern so a fallback is scheduled when stranded.
- **Failure modes (from research):** a **standing order only helps if it was pre-arranged and still holds at the time of stranding** (e.g. same-time daily), which is brittle for an unplanned event; if unexpected stranding, no standing order covers it → fails the no-help test for the *unplanned* incident that defines the problem. Low/recurring revenue per user; cap on addressable moments.
- **No-help test:** **Partially fails** — covers only pre-scheduled/regular moments, not the spontaneous phone-loss event.
- **ACMA/cert burden (provisional):** **None if service-only** (recurring booking on phone rails); moderate if bundled with any device.

### T4 — Concierge Dispatch (name suggests: human operator/concierge service)
- **Verdict (provisional): SHIP NOW as a service layer.** Identical in spirit to my C2 operator model; the human-dispatch + phone-network rail is the documented, working, phone-less channel (§4, §7) and needs no hardware.
- **Failure modes (from research):** needs a trigger that is reachable without the user's device (SMS/bystander/landline/venue) and an authenticated payment intent (fraud/chargeback); operator cost per ride is the margin risk; scaling a real 24/7 concierge is labour-heavy.
- **No-help test:** **Passes the common case** (a ready channel to a human who can dispatch+pay), **fails the literal zero-device perimeter** unless the concierge can also be reached by the user's sole remaining asset (cash/rank) — which is rank+hail, not concierge.
- **ACMA/cert burden:** **None** (service; telecom + payments compliance only).

---

## Verdict tallies & cross-cutting
- **SHIP NOW:** C2 (Stranded Fund) — and **T4 (Concierge Dispatch)** as provisional, on the same service-layer logic. **Recommendation: merge C2 and T4 into one dispatch service MVP.**
- **NEEDS WORK:** C1 (Key-Ride), C3 (Home Button), C5 (Ride-Home), and provisionally T1 (TapRide), T2 (Anchor), T3 (Standing Order).
- **ABANDON:** none outright; **C4 (Last-Mile Assist)** is the closest — it is a public-infrastructure program, not a venture product.
- **Cross-cutting (documented):** every hardware concept carries the **ACMA/RCM + carrier type-approval + battery (UN38.3)** burden (A$15–50k class) and the **reliability/SIM/support risk that killed Moochies** (RESEARCH §2), plus **loss-coupling** (device stolen with the phone) and **battery** — the honest reasons no "keychain SOS" has won alone. Every service concept depends on **a reachable channel (phone/bystander/landline) or pre-staged setup** — which is why the **service layer (dispatch + pay, C2/T4) should ship first** and any hardware (C1/C3) should attach to it later, not lead.

---

## REVISION 2026-08-09 (after VEX rebuttal — thread root 695e06)
VEX pushed back on Stranded Fund's "SHIP NOW": (1) **trust acquisition is the real blocker** — an unknown brand presented in a crisis triggers a scam response; (2) **adverse selection** in the "third party pays live" fix — a random stranger won't front money, only an ally will → collapses to a relational care-network product; (3) **fraud/liability moves, not dies** — unverifiable caller, chargeback, uncollectable invoicing.

**Resolution (SATORI):** Concede **SHIP NOW → NEEDS WORK**. The three objections reduce to **one fork: ally vs stranger**. The **stranger** fork dies on incentives and needs institutional trust to bootstrap. The **ally** fork is the build path: the ally has incentive (resolves #2) AND is a KYC'd/vouching payer the operator already verified at setup (largely resolves #3's identity/chargeback). The remaining hard 80% (#1) is distribution: get the care network established pre-crisis (aging-in-place / kids / carers / insurer channels). **Honest narrowing:** the ally model — like every model — needs a T=0 access link and serves people *with* a care network, not the truly isolated; and the literal problem statement (reach station, have cash+Opal, can't cover last mile) is largely **already served today by cash-at-rank** (the incumbent C4 was abandoned for). True product gap = no cash / no rank / isolation / assurance-value. Verdict: **Stranded Fund NEEDS WORK** with the ally-fork committed; VEX's definition of done endorsed.
