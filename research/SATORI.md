# SATORI — Full Research Output

**Agent:** SATORI (Researcher)
**Date:** 2026-08-09
**Task:** Research the problem: "Someone loses their phone and is stranded — they can't summon a ride, pay digitally, or contact anyone."

---

## 1. Existing Products (Help Someone Without a Phone)

- **Finding:** The senior SOS pendant/watch market already does "alert a human without a phone" today — standalone 4G cellular + GPS + SOS button + two-way voice, live and subscription-based in Australia.
- **Source:** LiveLife 4GX Watch Alarm → livelifealarms.com.au; SureSafeGO 'Anywhere' 4GX (Telstra SIM) → personalalarms.net.au; ADT Safe-N-Go pendant.
- **Details:** LiveLife 4GX is "designed in Australia, pre-programmed, no setup"; ADT Safe-N-Go = double-press SOS → 24/7 ADT monitoring pros, GPS/BLE/Wi-Fi/LBS location, two-way voice, IP67.

- **Finding:** Personal medical-alert (PERS) systems run entirely on the "press a pendant button with no phone" model.
- **Source:** MobileHelp → mobilehelp.com/pages/understanding-medical-alert-systems.
- **Details:** "Single press of the help button sends an alarm to a 24-hour emergency call center where an operator has your medical history and emergency contacts."

- **Finding:** Cellular smartwatches are the mainstream no-phone option — Apple Watch GPS+Cellular calls/texts/SOS "away from your phone", incl. Emergency SOS abroad and "Apple Watch For Your Kids" (own phone number, no iPhone).
- **Source:** apple.com/watch/cellular/ and /au/apple-watch-for-your-kids/.

- **Finding:** Satellite communicators/PLBs (Garmin InReach etc.) exist but serve off-grid wilderness, not urban last-mile, and are paid/subscription.
- **Source:** outdoorgearlab.com, backpacker.com.

## 2. Failed Attempts

- **Finding:** No startup is documented as *specifically* solving "phone loss → stranded last mile" and failing; the space is served by general connected-device categories, and the adjacent devoted-device failures show why.
- **Source:** Absence across multiple 2026 searches; adjacent cases below.

- **Finding:** Moochies (kids' SOS/GPS smartwatch) went into liquidation (Dec 2024) after GPS/support/SIM billing failures.
- **Source:** ABC News → abc.net.au/news/2024-12-16/moochies-smartwatch-claims-liquidation/104721530.

- **Finding:** Humane AI Pin, a standalone (phone-less) wearable, wound down Feb 2025 (~$230M raised), IP sold to HP.
- **Source:** Reuters 2025-02-19.

- **Finding:** Australia's Telstra 3G shutdown (2024) functionally bricked installed 3G SOS pendants, forcing mass forced-upgrade churn — a structural failure mode for any cellular SOS device.
- **Source:** personalalarms.net.au/telstra-3g-network-closure.

- **Finding:** Broader wearable-safety fashion-tech graveyard (Ringly, Wisewear, Athos…) failed commercially vs the smartphone — subscription lock-in, redundancy, reliability.
- **Source:** Wareable, Gizmodo.

## 3. Adjacent Industries

- **Finding (medical):** Pendant → 24/7 monitoring centre operator, with optional auto-fall detection + GPS; the operator path needs NO device of the user's own.
- **Source:** MobileHelp, Medical Guardian, and AU: Personal Alert Victoria (health.vic.gov.au), Tunstall AU.

- **Finding (travel):** Travel/consular handling of lost phones = report → block → replace identity documents; there is NO established product that physically summons transport when you are device-less.
- **Source:** passports.gov.au, DFAT consular services.

- **Finding (kids):** Parents manage kids via 4G GPS SOS kids' smartwatches + companion app + call whitelist — Spacetalk claims "#1 kids smartwatch in AU retail" (Telstra network).
- **Source:** spacetalk.co, JB Hi-Fi, Apple Watch For Your Kids. Caveat: reliability failure record (Moochies).

## 4. Australia-Specific

- **Finding:** Phone-less taxis work today via **phone booking (13CABS 13 2227, 24/7 live operator; national 131008)**, **taxi ranks**, and street hail; ranks/hail fares are **regulated maximums** (no surge).
- **Source:** 13CABS /locations/sydney (footer "24/7… speak to a real person! Pay with cash, card or account", "booked 7 days in advance"), Transport for NSW rank/hail fares page.
- **Details:** 13CABS explicitly uses the phone line for things not on the app (e.g. baby-seat taxis).

- **Finding:** Pre-booked/account rides exist — 13CABS web pre-booking (7 days), Fixed-Fare Taxi, Cabcharge eTICKET/account.
- **Source:** Cabcharge.com.au, transportnsw.info pre-paid taxi fares.

- **Finding:** Opal cards and contactless bank cards are valid on Metro/train/bus/ferry/light rail **but not on taxis** — Opal does NOT close the taxi last mile.
- **Source:** transportnsw.info/tickets-fares/contactless-payments, opal.com.au.

- **Finding:** NSW runs a **Taxi Transport Subsidy Scheme** (regulated, subsidised fares).
- **Source:** transportnsw.info/taxi-transport-subsidy-scheme.

## 5. Keychain Hardware (LTE-M / NB-IoT)

- **Finding:** Small LTE-M/NB-IoT SoMs with GNSS + app MCU + iSIM exist and are the building block for a keychain SOS button; AU dev-board retail ≈ A$121 inc GST.
- **Source:** DPTechnics Walter (ESP32-S3 + Sequans GM02SP LTE-M/NB-IoT + GNSS) → core-electronics.com.au, **$120.85 AUD inc GST** ($109.86 exc, volume lower).

- **Finding:** Sequans Monarch 2 GM02S is production-grade: single worldwide-band SKU, **iSIM**, EAL5+ secure, low-power MCU, 2.2V single-rail.
- **Source:** DigiKey (Sequans Monarch 2 GM02S), sequans.com. Bare-module pricing needs a supplier quote.

- **Finding (ACMA):** Supplying radio/telecom gear in AU requires ACMA compliance (General Equipment Rule + Telecommunications Labelling Notice) and RCM marking; breaches are offences with penalties up to 100–500 penalty units.
- **Source:** acma.gov.au (Step 1 check the rules; equipment compliance).

## 6. Data

- **Finding:** Australians lose ~**1,370 smartphones/day, ~A$755M/yr** in replacements; a US-datum baseline is ~**5% of phones lost yearly**.
- **Source:** news.com.au (1370/day, $755M), McAfee (5%). AMTA runs IMEI loss-blocking but publishes no national loss count (amta.org.au).

- **Finding:** Average Australian commute ~**37 km / ~64 min/day**, **30% now by train**.
- **Source:** Real Insurance Commute Report 2025 (n=2,000, Aug 2025); ABS "Australia's journey to work". No reliable public figure exists for "stranded at the station after losing a phone."

- **Finding:** Last-mile cab cost (Sydney, rank/hail): **$5.17 hire + $2.61/km first 12km then $2.37/km**; +$2.65 peak (10pm–6am Fri/Sat & night before public holidays); **~A$19 for 5km**, ~A$37 for 12km, ~A$21 late-night 5km. Airport→CBD fixed fare = **A$60** (since Nov 2025).
- **Source:** Transport for NSW rank/hail fares; taxi-fare.com.au/sydney.

## 7. Leverageable Infrastructure

- **Finding:** **Uber Ride Request API** exists (deep-link button + custom integration, 70+ countries) but assumes the rider has an Uber account + payment.
- **Source:** developer.uber.com/products/ride-requests.

- **Finding:** **DiDi** exposes a Fleet Open API for corporate bookings, not a public unauthenticated summon API.
- **Source:** fleet-api.didiglobal.com/fms-book.

- **Finding:** **13CABS does not publish a public booking API**; the phone line (13 2227) is the integration point.
- **Source:** 13cabs.com.au.

- **Finding (telco):** **Telstra** sells IoT data SIMs and a carrier-direct **Messaging/SMS API** (Australian-hosted) — the raw rails for a keychain device to send ride/help messages over legacy SMS/data.
- **Source:** telstra.com.au (IoT Data SIM plans; Messaging API).

- **Finding (payment):** Paying without a phone = **contactless debit/credit tap (eftpos/payWave), cash, or Cabcharge/account**; Opal/contactless covers the public-transport leg only, not the taxi.
- **Source:** AusPayNet/eftpos, 13CABS (cash/card/account), Cabcharge.

## Cross-Cutting Summary

The channels that already work **zero-device** are taxi ranks/hail (regulated), phone lines (13 2227 / 131008), and 24/7 monitoring centres. Structural failure modes for any new device = carrier sunsets (Telstra 3G 2024), subscription lock-in, redundancy vs phones, reliability/SIM failures (Moochies). Payments divergence: Opal gets you to the station; the taxi last mile is still cash/card/account/fixed-fare — a documented gap.