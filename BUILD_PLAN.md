# Build Plan — 2-Week Parallel Build

**Goal:** Stand up Stranded Fund + Concierge Dispatch in parallel, let adoption data pick the winner.

## Week 1: Foundation

### Critical Path: Fleet Partner
- [ ] Identify a taxi network willing to accept pre-paid/account bookings
- [ ] Establish the manual dispatch workflow (operator calls 13CABS or the partner)
- [ ] Get pricing confirmed (regulated rank/hail rates)
- [ ] Sign a simple partnership agreement
- **Gating dependency:** If no fleet partner takes the call, the build is blocked

### Payment Rails
- [ ] Stripe or Pin Payments account
- [ ] Pre-funded wallet mechanics (top-up, balance check, auto-deduct)
- [ ] Third-party live funding flow (ally pays from their own card)

### Operator Line
- [ ] Twilio or similar phone number (concierge line)
- [ ] Operator workflow: receive call → verify identity → book taxi → confirm ETA → notify contact
- [ ] PIN-based verification (so the operator can verify the stranded person without a phone)

### Basic Account
- [ ] Simple web form: name, card, home address, emergency contact, choose a PIN
- [ ] No app — works from any browser during setup (when you still have a phone)

## Week 2: Launch & Measure

### Go-Live
- [ ] Landing page explaining the service
- [ ] Beta signup (50 users, one station partnership)
- [ ] Operator training on the dispatch workflow
- [ ] SMS notification to emergency contacts (Telstra SMS API)

### Metrics to Track
- **Signups:** How many people pre-fund a wallet?
- **Incidents triggered:** How many actually use it?
- **Rides completed:** Did the taxi show up?
- **Repeat usage:** Do people come back?
- **Funnel drop-off:** Where do people abandon?
- **Cost per ride:** Operator time + dispatch fee vs revenue

### The Missing Datapoint
The official metric no one has: **"% of commuters who lose their phone and can't get home."** Running the MVP for 2 months produces this number. If it's low, the product is a niche. If it's high, scale.

## Tech Stack

| Component | Likely choice |
|-----------|---------------|
| Frontend | Simple HTML/CSS (no app) |
| Payment | Stripe / Pin Payments |
| Phone | Twilio |
| SMS | Telstra SMS API |
| Operator | Human (start with one) |
| Hosting | Vercel |

## Cost Estimate

| Item | Cost |
|------|------|
| Phone number + minutes | ~$50/mo |
| Operator (part-time) | ~$500-1000/mo |
| Payment processing | 1.75% + $0.30 per transaction |
| SMS API | ~$0.10 per SMS |
| Total monthly burn (MVP) | ~$600-1,100 |

## Future V2 (After Validation)

- Keychain SOS button (Key-Ride) — if the wallet model proves demand
- Standing Order membership — for recurring commuters
- Station kiosk partnership — if fleet partner interest is strong
- Corporate/insurer B2B — Cabcharge-style, duty-of-care