# MVP Spec — Stranded Fund + Concierge Dispatch

**Status:** Design phase (Aug 9, 2026)
**Build time:** ~2 weeks
**Hardware:** None
**Certification:** None
**Type:** Pure service, rides existing phone-booking rails (13CABS/131008)

## The Problem

Someone loses their phone. They have their wallet (cards, cash, Opal card). They can reach a station but can't cover the last mile home — ride apps are phone-only, and they have zero internet-connected devices.

## The Core Mechanism

A pre-funded ride wallet + a human-operated dispatch line. The user (or a third party with their own phone) calls the operator, who books a taxi via the existing phone network (13CABS/131008), and the fare is charged to the pre-funded wallet. No phone needed from the stranded person.

## User Flow

1. **Setup (once, while phone works):** Create an account. Link a payment card. Pre-fund a ride wallet (minimum $20). Save home address and one emergency contact.
2. **Incident:** Phone lost. At station. No internet. Wallet intact.
3. **Summon:** The stranded person asks a bystander to call the concierge number OR uses a station payphone/landline. The operator verifies the caller via a memorized PIN or the caller's pre-registered phone number.
4. **Dispatch:** Operator books a taxi via 13CABS/131008 to the station's taxi rank. Fare is quoted at the regulated rank/hail rate (no surge).
5. **Ride:** Person walks to the rank, boards the taxi, gives the destination to the driver.
6. **Payment:** Fare is charged to the pre-funded wallet. No tap, no card, no cash at the scene.
7. **Notify:** Completion SMS sent to the emergency contact (via Telstra SMS API).

## The Third-Party Live Funding Fix

The core innovation that unblocks the category:

**If the stranded person has no pre-funded wallet (zero prep), a third party with their own phone can call the operator and pay the fare live from their own account.** The operator books the ride, the third party pays, the stranded person just gets home.

This dissolves three objections at once:
- **No prep dependency** — someone else pays live
- **No scam suspicion** — the third party is a known ally (or the operator handles the trust)
- **No lost-wallet trap** — payment happens on the third party's phone, not at the scene

## Revenue Model

| Source | Amount | Notes |
|--------|--------|-------|
| Per-ride dispatch fee | ~$1.50–2.00 | Flat fee, added to the fare |
| Wallet float | ~3-5% | Interest on pre-funded balances |
| Monthly plan (optional) | $4-6/mo | No mandatory subscription |
| Corporate/insurer B2B | Per-seat licensing | Duty-of-care, employee benefits |

## Economics

- Last-mile fare (Sydney, regulated): ~A$19-21 for 5km
- Dispatch fee: ~$1.50-2.00
- Average monthly usage: Unknown (to be measured by the MVP)
- Break-even: ~$5-10 per user per year in dispatch fees

## MVP Scope (2-3 Weeks)

**Week 1:**
- Fleet partner onboarding (13CABS or a local taxi network)
- Operator phone line setup (Twilio or similar)
- Payment processing (Stripe/Pin Payments)
- Basic account creation (name, card, home address, emergency contact)

**Week 2:**
- Operator dispatch workflow (receive call → verify → book via phone → confirm)
- SMS notification to emergency contacts
- Third-party live funding flow
- Landing page + beta signup

## Key Risks

| Risk | Mitigation |
|------|-----------|
| No 13CABS API (phone-only booking) | Operator calls 13CABS manually — old-school, reliable |
| Stranded person can't reach a phone | Station payphones, landlines, or a bystander — the MVP assumes this is the common case |
| Operator staffing cost | Start with limited hours (peak commute) or a single operator; scale with volume |
| Fraud (someone else using your wallet) | PIN-based verification; SMS alerts on every ride |
| Fleet partner availability | Manual taxi booking via phone line works with ANY taxi company, not just one partner |

## Missing Datapoint

**"How many people are actually stranded at a station after losing their phone?"**

No public data exists. The MVP itself is the measurement tool — track:
- Signups
- Incidents triggered
- Rides completed
- Repeat usage rate

If the funnel is empty after 2 months, the TAM is smaller than estimated. If it grows, the product validates.