# Vaelis — Privacy Policy

**Effective date:** May 8, 2026

This policy explains what data we collect, why, who we share it with and your rights when using the Vaelis mobile app. Written to align with Turkey's Personal Data Protection Law (KVKK) and the EU General Data Protection Regulation (GDPR).

## 1. Data controller

Eren Yalçın — Turkey  
Contact: **eren-yalcin2010@hotmail.com**

## 2. Data we collect

### a. Account data (when you sign up)
- Email address
- Secure hash of your password (PBKDF2-HMAC-SHA256; plaintext is never stored)
- Account creation + last sign-in timestamps

### b. User content (when you upload)
- Photos uploaded for style analysis
- Wardrobe item photos and metadata (name, category, color, brand, size)
- Saved looks (photo + analysis output)
- Journal entries (photo + optional note)
- Style profile (gender, undertone, preferred archetypes)

### c. AI-generated data
- AI-produced analyses, outfit suggestions, briefs and weekly digests for your uploaded visuals and text
- Stored alongside the prompt version (for quality tracking)

### d. Usage analytics
- Anonymous event logs (e.g. screen opens, paywall views, subscription conversions) via PostHog (EU region)
- No personal data; each user is identified via a one-way hashed pseudo-id

### e. Crash reports
- App crash stack traces, device model, iOS version, Vaelis version via Sentry
- No raw user data (passwords, photos, etc.) is sent

### f. Subscription state
- Subscription status received from Apple StoreKit (active, trial, lapsed)
- Apple `original_transaction_id` (for subscription tracking)

## 3. How we use the data

- We send your photos + text context to **OpenAI** API for AI generation (analysis, outfits, briefs, weekly digest)
- Account management, sign-in, subscription verification
- Cross-device sync (Cloudflare D1 + R2)
- Service quality tracking (anonymous analytics)
- Crash diagnosis and fix (anonymous error reports)

We do not use your data for advertising, third-party marketing or sale.

## 4. Third-party services

| Service | Purpose | Data location | Policy |
|---|---|---|---|
| **OpenAI** | AI generation (vision + text) | USA | openai.com/policies |
| **Cloudflare** (Workers, D1, R2, KV) | Backend, database, photo storage | Global edge | cloudflare.com/privacypolicy |
| **PostHog** | Anonymous usage analytics | EU (eu.i.posthog.com) | posthog.com/privacy |
| **Sentry** | Crash reports | EU (sentry.de) | sentry.io/privacy |
| **Apple App Store** | Subscription management | USA / Apple infrastructure | apple.com/privacy |

OpenAI does not use API-submitted data for model training (default opt-out per user agreement).

## 5. Data retention

- **Account data:** retained until you delete your account, then immediately erased.
- **User content (photos, wardrobe, looks, journal):** all server copies (D1 + R2) immediately erased when you delete your account; local copies are removed when you uninstall the app.
- **Anonymous analytics:** retained 12 months in PostHog, then aggregated.
- **Crash reports:** retained 30 days in Sentry, then deleted.

## 6. Account + data deletion

You can delete your account in-app with one tap: **Profile → Account → Delete Account**. After confirmation all your data on D1 + R2 is wiped from servers, your KV session is revoked, and local device data is cleared. The action is irreversible.

## 7. User rights (KVKK + GDPR)

You have the right to:
- **Access** information about your data
- **Rectify** incorrect data
- **Erase** your data (one tap in-app)
- **Portability** of your data (request via email)
- **Object** to certain processing
- **Complain** to Turkey's Data Protection Authority (KVKK) or your EU member state's data protection authority

Requests: **eren-yalcin2010@hotmail.com** — answered within 30 days.

## 8. Children's privacy

Vaelis does not accept users under 13 years of age. If you discover a child under 13 has uploaded data, please notify us; we will erase the data.

## 9. Security

- End-to-end TLS 1.2+ encrypted connections
- Passwords hashed with PBKDF2-HMAC-SHA256, 100,000 iterations
- Photos stored in Cloudflare R2 behind access control; user authorization checked on every request
- Token-based session management (90-day TTL)

Absolute security can't be guaranteed; in the event of a breach we will notify KVKK and affected users within 72 hours.

## 10. Policy changes

If we update this policy we'll change the effective date and notify you in-app. Material changes require explicit consent.

## 11. Contact

Questions and requests: **eren-yalcin2010@hotmail.com**
