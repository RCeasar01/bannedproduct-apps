# BannedProduct Media — Master App Submission Guide

**Owner:** BannedProduct Media Inc. | 100% Veteran-Owned  
**Developer:** Robert Ceasar  
**Contact:** support@bannedproductmedia.com  
**Governing Law:** North Carolina, USA  
**Last Updated:** June 2026

---

## Before You Pay Anything — Read This First

You have **7 apps** to submit (GridDown is already live). Below is everything you need to do, in order, before spending a dollar on submission fees. Set up the free infrastructure first, then build, then submit.

---

## Section 1 — Accounts You Need (One-Time Setup)

| Service | Cost | URL | Notes |
|---------|------|-----|-------|
| **Apple Developer Program** | $99/year | https://developer.apple.com/programs/enroll/ | Required for iOS App Store. Must match your legal entity name. Allow 24–48 hrs for approval. |
| **Google Play Developer** | $25 one-time | https://play.google.com/console/about/ | Required for Android Play Store. Instant-ish approval. |
| **RevenueCat** | Free up to $2.5k MRR | https://app.revenuecat.com | Manages subscriptions for FitnessAI and TacMed. No cost to start. |
| **Supabase** | Free up to 50k MAU | https://supabase.com | Backend database for 7 of 8 apps. Free tier is generous. |
| **Expo Application Services (EAS)** | Free personal tier | https://expo.dev | Builds your iOS/Android binaries in the cloud. Free for personal projects. |

> **Total to start: $99 (Apple) + $25 (Google) = $124**  
> RevenueCat, Supabase, and EAS are all free to start.

---

## Section 2 — Per-App Pre-Submission Checklist

Repeat this entire checklist for each app. Check each box before paying the submission fee.

### App Order (suggested — easiest to hardest)
1. TacMed (no account/Supabase needed for basic submit)
2. HolyBook
3. GridDown *(already live on iOS — just add Android)*
4. RangeLog
5. RuckLog
6. ZeroHour
7. FitnessAI
8. VetTrack *(most complex; do last)*

---

### For Each App — Complete Checklist

**Supabase Setup**
- [ ] Go to https://supabase.com → New Project → name it after the app
- [ ] Copy the **Project URL** and **anon public key** from Settings → API
- [ ] Open the app folder: `E:\Apps\[AppName]\`
- [ ] Add to `.env` file:
  ```
  EXPO_PUBLIC_SUPABASE_URL=https://xxxxxxxxxxxx.supabase.co
  EXPO_PUBLIC_SUPABASE_ANON_KEY=eyJhbGciOi...
  ```
- [ ] Run schema: open Supabase Dashboard → SQL Editor → paste contents of `supabase/schema.sql` from the app folder → Run

**RevenueCat Setup** *(FitnessAI and TacMed only)*
- [ ] Go to https://app.revenuecat.com → New Project → name it after the app
- [ ] Add iOS app (bundle ID from `app.json`) and Android app (package name)
- [ ] In App Store Connect: create the subscription product(s) — see Section 4 for IDs
- [ ] In Play Console: create the subscription product(s)
- [ ] In RevenueCat: add the products and create Entitlement matching the ID in code
- [ ] Copy RevenueCat API key → add to `.env`:
  ```
  EXPO_PUBLIC_REVENUECAT_API_KEY_IOS=appl_xxxx
  EXPO_PUBLIC_REVENUECAT_API_KEY_ANDROID=goog_xxxx
  ```

**EAS Build**
- [ ] Ensure EAS CLI is installed: `npm install -g eas-cli`
- [ ] Log into EAS: `eas login`
- [ ] From the app directory: `eas build --platform all --profile production`
- [ ] First build will prompt for Apple credentials (use your Apple Developer account)
- [ ] Build takes 15–30 minutes. Download the `.ipa` (iOS) and `.aab` (Android) when done.

**App Store Connect (iOS)**
- [ ] Log into https://appstoreconnect.apple.com
- [ ] Apps → `+` → New App → iOS → select Bundle ID
- [ ] Fill in store listing from `store-assets/STORE_LISTING.md` in the app folder
- [ ] Upload screenshots from `store-assets/screenshots/` (see Section 5)
- [ ] Set Support URL: `https://rceasar01.github.io/bannedproduct-apps/[appslug]/`
- [ ] Set Privacy Policy URL: `https://rceasar01.github.io/bannedproduct-apps/[appslug]/privacy.html`
- [ ] Upload the `.ipa` build under TestFlight or direct submission
- [ ] Submit for Review

**Google Play Console (Android)**
- [ ] Log into https://play.google.com/console
- [ ] All Apps → Create App → fill in store listing
- [ ] Set Support Email: support@bannedproductmedia.com
- [ ] Set Privacy Policy URL: `https://rceasar01.github.io/bannedproduct-apps/[appslug]/privacy.html`
- [ ] Upload the `.aab` build → Production track
- [ ] Complete Data Safety questionnaire (see Section 6 for data mappings)
- [ ] Submit for Review

---

## Section 3 — App-Specific URLs (Live on GitHub Pages)

Once GitHub Pages is enabled, these URLs will be live. Use them in App Store Connect and Play Console.

| App | Support URL | Privacy Policy URL | Terms URL |
|-----|-------------|-------------------|-----------|
| FitnessAI | https://rceasar01.github.io/bannedproduct-apps/fitnessai/ | https://rceasar01.github.io/bannedproduct-apps/fitnessai/privacy.html | https://rceasar01.github.io/bannedproduct-apps/fitnessai/terms.html |
| VetTrack | https://rceasar01.github.io/bannedproduct-apps/vettrack/ | https://rceasar01.github.io/bannedproduct-apps/vettrack/privacy.html | https://rceasar01.github.io/bannedproduct-apps/vettrack/terms.html |
| HolyBook | https://rceasar01.github.io/bannedproduct-apps/holybook/ | https://rceasar01.github.io/bannedproduct-apps/holybook/privacy.html | https://rceasar01.github.io/bannedproduct-apps/holybook/terms.html |
| RangeLog | https://rceasar01.github.io/bannedproduct-apps/rangelog/ | https://rceasar01.github.io/bannedproduct-apps/rangelog/privacy.html | https://rceasar01.github.io/bannedproduct-apps/rangelog/terms.html |
| TacMed | https://rceasar01.github.io/bannedproduct-apps/tacmed/ | https://rceasar01.github.io/bannedproduct-apps/tacmed/privacy.html | https://rceasar01.github.io/bannedproduct-apps/tacmed/terms.html |
| RuckLog | https://rceasar01.github.io/bannedproduct-apps/rucklog/ | https://rceasar01.github.io/bannedproduct-apps/rucklog/privacy.html | https://rceasar01.github.io/bannedproduct-apps/rucklog/terms.html |
| ZeroHour | https://rceasar01.github.io/bannedproduct-apps/zerohour/ | https://rceasar01.github.io/bannedproduct-apps/zerohour/privacy.html | https://rceasar01.github.io/bannedproduct-apps/zerohour/terms.html |
| GridDown | https://rceasar01.github.io/bannedproduct-apps/griddown/ | https://rceasar01.github.io/bannedproduct-apps/griddown/privacy.html | https://rceasar01.github.io/bannedproduct-apps/griddown/terms.html |

---

## Section 4 — RevenueCat Product IDs to Create

### FitnessAI
- Entitlement ID in code: check `E:\Apps\FitnessAI\` for `ENTITLEMENT_ID` constant
- Suggested product IDs:
  - `fitnessai_pro_monthly` — $4.99/month
  - `fitnessai_pro_annual` — $39.99/year
  - `fitnessai_pro_lifetime` — $69.99 one-time (if offered)

### TacMed
- Entitlement ID in code: check `E:\Apps\TacMed\` for `ENTITLEMENT_ID` constant
- Suggested product IDs:
  - `tacmed_pro_monthly` — $2.99/month
  - `tacmed_pro_annual` — $19.99/year
  - `tacmed_pro_lifetime` — $49.99 one-time (if offered)

> **Note:** Create products in App Store Connect and Play Console FIRST, then add them to RevenueCat. RevenueCat syncs from the stores.

---

## Section 5 — EAS Build Commands

Run from each app's directory. Ensure `.env` is populated before building.

```bash
# FitnessAI
cd E:\Apps\FitnessAI
eas build --platform all --profile production

# VetTrack
cd E:\Apps\VetTrack
eas build --platform all --profile production

# HolyBook  ← IMPORTANT: add Supabase URL/key to .env first
cd E:\Apps\HolyBookApp
eas build --platform all --profile production

# RangeLog
cd E:\Apps\RangeLog
eas build --platform all --profile production

# TacMed
cd E:\Apps\TacMed
eas build --platform all --profile production

# RuckLog
cd E:\Apps\RuckLog
eas build --platform all --profile production

# ZeroHour
cd E:\Apps\ZeroHour
eas build --platform all --profile production

# GridDown (Android only — iOS already live)
cd E:\Apps\GridDown
eas build --platform android --profile production
```

---

## Section 6 — App Store Connect Required Fields

For each app, you'll fill these fields. Source: `store-assets/STORE_LISTING.md` in each app folder.

| Field | Source | Notes |
|-------|--------|-------|
| **Name** | STORE_LISTING.md | Max 30 chars |
| **Subtitle** | STORE_LISTING.md | Max 30 chars |
| **Description** | STORE_LISTING.md | Max 4000 chars |
| **Keywords** | STORE_LISTING.md | Max 100 chars, comma-separated |
| **Support URL** | Section 3 above | Required |
| **Privacy Policy URL** | Section 3 above | Required |
| **Age Rating** | STORE_LISTING.md | Complete the questionnaire |
| **Primary Category** | STORE_LISTING.md | e.g., Health & Fitness, Utilities |
| **Secondary Category** | STORE_LISTING.md | Optional but recommended |
| **Developer Name** | BannedProduct Media Inc. | Must match Apple Developer account |

---

## Section 7 — Google Play Data Safety Questionnaire

When completing the Play Console Data Safety section, use these answers per app:

| App | Data Collected | Data Shared | User-Deletable |
|-----|---------------|-------------|----------------|
| FitnessAI | Email, fitness activity, health data | No (RevenueCat handles purchases only) | Yes |
| VetTrack | Email, app activity | No | Yes |
| HolyBook | Email (optional), location (not stored) | No | Yes |
| RangeLog | Email, app activity | No | Yes |
| TacMed | None (no account for basic use) | No | N/A |
| RuckLog | Email, location (during sessions) | No | Yes |
| ZeroHour | Email, health/fitness data | No | Yes |
| GridDown | Email, location (when posting alerts) | Yes (location shared with other users via Supabase) | Yes |

For "Data encrypted in transit": **Yes** (Supabase uses TLS)  
For "Data deletion request": **Yes** — email support@bannedproductmedia.com

---

## Section 8 — HolyBook Special Note

**Before building or submitting HolyBook:**

1. Create a Supabase project for HolyBook at https://supabase.com
2. Open `E:\Apps\HolyBookApp\.env` and add:
   ```
   EXPO_PUBLIC_SUPABASE_URL=https://[your-project].supabase.co
   EXPO_PUBLIC_SUPABASE_ANON_KEY=[your-anon-key]
   ```
3. Run the schema from `E:\Apps\HolyBookApp\supabase\schema.sql` in the Supabase SQL editor
4. Then run `eas build`

HolyBook fetches Quran content from `alquran.cloud` — no API key required. Ensure the app handles network errors gracefully (already implemented via offline cache).

**App Store category note:** Submit under **Reference** (primary) and **Books** (secondary). In the age rating questionnaire, mark it as 4+ — no violent or mature content.

---

## Section 9 — VetTrack Special Notes

- VetTrack handles **sensitive veteran data**. During App Store review, Apple may ask how data is protected. Answer: encrypted via Supabase TLS; biometric lock via iOS Secure Enclave; document vault stored locally.
- The **VA disclaimer** on the Privacy Policy and Terms is important — Apple reviewers for this category look for it.
- Age rating: **4+**
- Primary Category: **Utilities**, Secondary: **Finance** or **Medical**

---

## Section 10 — TacMed Special Notes

- TacMed will be reviewed under **Medical** category. Apple scrutinizes medical apps closely.
- The **TCCC disclaimer** must be visible in the app itself (not just the Terms page). Ensure it appears on first launch or in a prominent About screen.
- Age rating: **12+** (mature/intense content may apply due to medical trauma content)
- Primary Category: **Medical**, Secondary: **Reference**
- Apple may request you demonstrate that the app clearly states it is for **educational purposes only**

---

## Section 11 — Submission Costs Summary

| Cost | When | Who |
|------|------|-----|
| Apple Developer Program — $99/year | Before first iOS build | You (apple.com) |
| Google Play — $25 one-time | Before first Android submit | You (play.google.com) |
| RevenueCat | $0 to start | N/A |
| Supabase | $0 to start | N/A |
| EAS Build | $0 personal tier | N/A |
| **Total to get started** | **$124** | |

After $2.5k MRR on RevenueCat or 50k MAU on Supabase, you'll need paid tiers — but that's a good problem to have.

---

## Appendix — Repo Structure Reference

```
bannedproduct-apps/          ← GitHub repo root
  docs/                      ← GitHub Pages root
    index.html               ← Landing page (all apps)
    fitnessai/
      index.html             ← Support page
      privacy.html           ← Privacy Policy
      terms.html             ← Terms of Use
    vettrack/  [same structure]
    holybook/  [same structure]
    rangelog/  [same structure]
    tacmed/    [same structure]
    rucklog/   [same structure]
    zerohour/  [same structure]
    griddown/  [same structure]
  MASTER_SUBMISSION_GUIDE.md ← This file
```

---

*BannedProduct Media Inc. — 100% Veteran-Owned — Built with purpose.*
