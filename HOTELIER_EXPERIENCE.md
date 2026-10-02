# Allhourdesk — Hotelier Experience

**Status:** Product experience specification  
**Audience:** Product, Design, Engineering, Sales, Customer Success  
**Primary goal:** A hotel owner should be able to sign up, connect the hotel, test the AI front desk, and go live with minimal technical knowledge.

---

## 1. Experience Principle

Allhourdesk should feel like activating a service, not integrating a collection of APIs.

The hotelier should never need to understand Apaleo tokens, Twilio, ElevenLabs, SIP, Stripe Connect, webhooks, merchant IDs, or payment routing.

The product experience is:

> **Connect PMS → Connect Payments → Connect Phone → Test → Go Live**

Allhourdesk owns the orchestration. The hotel owns its operational and financial accounts.

### Core promise

> **Your guests pay you directly. Allhourdesk never holds your reservation revenue.**

---

## 2. Payment Architecture Decision

Use **Stripe Connect** with a **hotel-owned connected account** and create reservation payments on the hotel's Stripe account.

### Target model

```text
Guest
  ↓
Stripe Checkout
  ↓
Hotel's Stripe connected account
  ↓
Hotel's bank account
```

Allhourdesk creates and tracks the payment as the software platform, but the hotel remains the merchant.

### Do not use this model

```text
Guest
  ↓
Allhourdesk Stripe account
  ↓
Allhourdesk balance
  ↓
Transfer to hotel
```

Allhourdesk should not become the settlement layer for hotel reservation revenue.

### Why

The hotel-owned merchant model gives us the desired separation:

- The hotel owns its Stripe/payment relationship.
- Guest payments are associated with the hotel.
- The hotel's merchant identity and statement descriptor can be used.
- Funds settle to the hotel's configured bank account.
- Allhourdesk does not hold hotel reservation revenue.
- Refunds, disputes, payouts, and financial verification remain associated with the hotel's Stripe account.
- Allhourdesk can still orchestrate payments and synchronize their status with reservations.
- Future platform/application fees remain possible without changing the core merchant ownership model.

---

## 3. Hotelier Onboarding

### Entry point

After account creation, show one clear objective:

# Get your AI Front Desk live

Use a persistent progress indicator:

```text
1. Hotel       ✓
2. Reservations
3. Payments
4. Phone
5. Go Live
```

The hotelier should always know:

1. What is complete.
2. What needs attention.
3. What happens next.
4. Whether the system can already be tested.
5. What prevents production activation.

---

## 4. Step 1 — Your Hotel

Collect only information needed to establish the property.

### Required

- Hotel/property name
- Legal/business name where required
- Address
- Country
- Timezone
- Website
- Primary contact name
- Primary contact email
- Front desk phone number

### Optional / later

Avoid front-loading configuration that can be discovered from the PMS or completed after activation.

### Completion state

```text
✓ Hotel created
The Kildare Hotel
Naas, Ireland
```

CTA:

**Continue to reservations**

---

## 5. Step 2 — Connect Your Reservation System

Do not ask the hotelier for generic "PMS credentials."

First ask:

> **Which reservation system do you use?**

Display supported PMS providers as branded connection options.

Initial example:

### Apaleo

CTA:

**Connect Apaleo**

Use OAuth whenever available. If an integration token/API credential is required, provide a guided provider-specific flow showing exactly where to obtain it.

### Connection validation

Saving credentials is not enough. Allhourdesk must immediately validate the integration and show useful evidence.

Example:

```text
✓ Apaleo connected

87 rooms found
14 room types found
Availability access verified
Reservation creation verified
```

Where possible, test:

- Property access
- Inventory/room access
- Availability lookup
- Rate lookup
- Reservation read
- Reservation creation permission
- Reservation modification/cancellation permission

### Failure UX

Never display raw API errors.

Example:

> **We connected to Apaleo, but reservation creation is not enabled.**
>
> Update the integration permissions and try again.

CTA:

**Fix connection**

---

## 6. Step 3 — Receive Guest Payments

This should be one of the simplest screens in the entire onboarding.

### Customer-facing copy

# Receive guest payments

Connect your hotel's Stripe account so guests can securely pay for reservations.

**Payments go directly to your business. Allhourdesk never holds your reservation revenue.**

CTA:

**Connect Stripe**

Supporting copy:

> Already use Stripe? Connect your existing account.  
> New to Stripe? You can create an account during setup.

### Implementation

Use **Stripe Connect**.

The hotel should complete Stripe's hosted or embedded onboarding for:

- Business identity
- KYC/KYB
- Bank account
- Payout configuration
- Required financial information

Allhourdesk should not collect or store sensitive bank/KYC information that Stripe can collect directly.

### Connected state

After return from Stripe:

```text
✓ Payments connected

The Kildare Hotel Ltd
Currency: EUR
Payments: Enabled
Payouts: Enabled
Bank account: •••• 8421
```

CTA:

**Test payment**

### Activation state

Internally track at minimum:

```text
stripe.account_connected
stripe.details_submitted
stripe.charges_enabled
stripe.payouts_enabled
```

Do not treat "returned from Stripe onboarding" as equivalent to "ready for live payments."

---

## 7. Test Before Financial Verification Is Complete

A hotel should be able to experience Allhourdesk before every production dependency is complete.

Do not expose "test mode" as technical terminology unless necessary.

Instead show:

> # Your AI Front Desk is ready to test
>
> ✓ Hotel connected  
> ✓ Reservation system connected  
> ✓ AI receptionist configured  
> ⏳ Payment verification in progress
>
> You can test the complete reservation experience now. Real guest payments will become available when payment verification is complete.

Provide a safe demo/test reservation flow using Stripe test capabilities.

### Principle

**Time-to-wow must not depend on KYC completion.**

A hotelier should be able to:

1. Call the AI receptionist.
2. Ask for availability.
3. Select a room.
4. Create a test reservation.
5. Receive a test payment request.
6. Complete a test payment.
7. See the resulting reservation flow.

---

## 8. Step 4 — Connect Your Front Desk Phone

The fastest initial experience is **call forwarding**, not number porting.

The hotel's existing public phone number remains unchanged.

Allhourdesk provides the destination number.

### Customer-facing copy

# Connect your front desk

Keep your existing hotel number.

Forward the calls you want Allhourdesk to answer to:

**+353 XX XXX XXXX**

### Answering options

- When the front desk does not answer
- Outside business hours
- During selected hours
- Always

For scheduled forwarding:

```text
Allhourdesk answers:
18:00 → 08:00
Monday → Sunday
```

Allow different schedules by day.

### Setup assistance

Provide carrier/provider-specific forwarding instructions when possible.

### Verification

CTA:

**Test my hotel phone**

The system should place or guide an end-to-end test and verify that the call reaches the correct Allhourdesk property.

Success:

```text
✓ Phone connected
Test call received successfully
```

Number porting can be offered later as an advanced option, not as an onboarding dependency.

---

## 9. Step 5 — Go Live

Provide one activation dashboard.

# Ready to go live?

| Service | Status |
| --- | --- |
| Hotel information | 🟢 Ready |
| Reservation system | 🟢 Connected |
| Payments | 🟢 Ready |
| Front desk phone | 🟢 Connected |
| AI receptionist | 🟢 Ready |

Primary CTA:

**Test a reservation**

After successful test:

**Go live**

### Production activation gates

At minimum:

```text
hotel.configuration_complete = true
pms.connected = true
pms.availability_verified = true
pms.reservation_creation_verified = true
phone.verified = true
stripe.charges_enabled = true
stripe.payouts_enabled = true
ai_agent.ready = true
```

A failed gate should explain exactly what needs to be fixed.

Never show a generic "configuration incomplete."

---

## 10. Golden Path — Guest Reservation

```text
Guest calls hotel
        │
        ▼
Hotel forwards selected call
        │
        ▼
Allhourdesk AI Front Desk
        │
        ├──── PMS: check live availability
        │
        ├──── PMS: retrieve rooms/rates/policies
        │
        ▼
Guest selects reservation
        │
        ▼
Allhourdesk creates reservation/payment context
        │
        ▼
Payment request created
ON HOTEL'S STRIPE ACCOUNT
        │
        ▼
Guest receives secure link
SMS / WhatsApp
        │
        ▼
Stripe Checkout
        │
        ├──── Funds → hotel's Stripe account
        │
        └──── Webhook → Allhourdesk
                          │
                          ▼
                   Payment successful
                          │
                          ▼
                     PMS reservation
                       confirmed
                          │
                          ▼
                  Guest confirmation
```

---

## 11. Reservation Payment UX

Prefer a reservation-specific **Stripe Checkout Session** over a reusable generic payment link where it provides better lifecycle control.

Each payment should be correlated with:

- Allhourdesk property ID
- PMS property ID
- Reservation ID / provisional reservation ID
- Guest ID where appropriate
- Amount
- Currency
- Expiration time
- Payment status
- Reservation status

### Guest message example

> **The Kildare Hotel**
>
> Complete your reservation payment of **€487.00** securely.
>
> **Pay now**
>
> Your reservation will be confirmed after successful payment.

The hotel—not Allhourdesk—should be the financial identity presented to the guest wherever Stripe configuration supports it.

---

## 12. Payment and Reservation State Machine

Do not model payment as a boolean.

Suggested states:

```text
NOT_REQUIRED
PENDING
LINK_SENT
PROCESSING
PAID
FAILED
EXPIRED
CANCELLED
PARTIALLY_REFUNDED
REFUNDED
DISPUTED
```

Reservation state must be separately tracked.

Example:

```text
INQUIRY
HELD
PENDING_PAYMENT
CONFIRMED
CANCELLED
EXPIRED
```

Allhourdesk should explicitly reconcile PMS and Stripe states.

---

## 13. Refunds and Cancellations

Allhourdesk should avoid being the financial owner while still providing an integrated operational experience.

Preferred future UX:

```text
Reservation cancelled
        ↓
Cancellation policy evaluated
        ↓
Refund amount determined
        ↓
Hotel confirms refund if approval required
        ↓
Refund executed against
HOTEL'S STRIPE ACCOUNT
        ↓
Stripe webhook
        ↓
Allhourdesk + PMS synchronized
```

Do not require the hotelier to manually perform a refund in Stripe and then separately update Allhourdesk/PMS if this can be safely automated.

### Principle

**Allhourdesk orchestrates. The hotel owns the transaction.**

Dispute information should be visible where operationally useful, but Stripe remains the financial system of record.

---

## 14. Hotelier Dashboard After Activation

After onboarding, replace the setup wizard with an operational dashboard.

Suggested top-level status:

```text
AI Front Desk                  LIVE

Calls today                     31
Handled by Allhourdesk          24
Reservations created             7
Reservation value           €2,840
Payments collected          €2,190
Needs attention                  2
```

### Needs attention

Surface actionable exceptions rather than integration logs:

- Payment failed
- Payment link expired
- PMS unavailable
- Reservation requires review
- Stripe verification required
- Phone forwarding test failed
- Guest requested human assistance

---

## 15. Settings Structure

After onboarding, integrations should remain manageable without exposing unnecessary infrastructure.

### Hotel
Property information, timezone, contacts.

### Reservations
PMS connection, property mapping, reservation policies.

### Payments
Stripe connection, payment status, payout readiness, payment rules.

### Phone & Hours
Hotel number, forwarding destination, answering schedule, fallback behavior.

### AI Front Desk
Voice, languages, greeting, escalation rules, operational instructions.

### Notifications
Email, SMS, WhatsApp, reservation alerts, payment alerts.

### Team
Users, roles, permissions.

Do not create separate customer-facing settings for Twilio, ElevenLabs, webhooks, API endpoints, or other Allhourdesk infrastructure.

---

## 16. Design Principles

### Hide infrastructure

Never make customers configure implementation components that Allhourdesk can own.

### Verify, don't merely save

Every integration step should end with a real validation.

Bad:

> Credentials saved.

Good:

> ✓ Apaleo connected — availability and reservation creation verified.

### Progressive activation

The customer can test before every production dependency is ready.

### One primary action per screen

Each onboarding screen should have a single obvious next step.

### Human language

Prefer:

> Receive guest payments

over:

> Configure payment gateway.

Prefer:

> Connect your reservation system

over:

> Configure PMS API integration.

Prefer:

> Connect your front desk

over:

> Configure telephony routing.

### Explain ownership clearly

Especially for payments:

> Payments go directly to your business. Allhourdesk never holds your reservation revenue.

### Exceptions over logs

Hotel owners should see problems they can act on, not infrastructure diagnostics.

---

## 17. Recommended MVP

### Required for first production release

- Allhourdesk account creation
- Property setup
- Apaleo connection
- PMS validation
- Stripe Connect onboarding
- Stripe account readiness/status synchronization
- Hotel-owned reservation payments
- Stripe Checkout payment flow
- Stripe webhook processing
- Twilio destination number assignment
- Call-forwarding setup
- Configurable answering hours
- Phone verification/test
- AI agent configuration
- End-to-end test reservation
- Production activation gates
- Operational exception states

### Later

- Additional PMS providers
- Embedded Stripe account management
- Automated cancellation/refund workflow
- Number porting
- Multi-property management
- Multiple merchant accounts per hotel group
- Advanced payment/deposit policies
- Application/transaction fees
- Automated carrier-specific phone configuration
- Team roles and approval policies
- Rich payment/dispute dashboards

---

## 18. Success Metrics

Measure onboarding as a funnel:

```text
Account created
    ↓
Hotel configured
    ↓
PMS connected
    ↓
First availability query succeeds
    ↓
First AI test call
    ↓
First test reservation
    ↓
Stripe connected
    ↓
Stripe live-ready
    ↓
Phone verified
    ↓
GO LIVE
    ↓
First real call
    ↓
First real reservation
    ↓
First successful guest payment
```

Key product metrics:

- Median time from signup → first successful test call
- Median time from signup → first test reservation
- Median time from signup → live-ready
- PMS connection completion rate
- Stripe onboarding completion rate
- Phone setup completion rate
- End-to-end test success rate
- Activation rate
- First-week reservation success rate
- Payment-link conversion rate
- Percentage of onboarding requiring human support

### North-star onboarding metric

> **Percentage of new hotels that complete an end-to-end test reservation without Allhourdesk staff assistance.**

---

## 19. Product Positioning Result

The onboarding experience should reinforce the Allhourdesk proposition:

> **Your hotel. Your number. Your reservation system. Your payments. Your guests.**
>
> **Allhourdesk simply makes your front desk available when you need it.**

The architecture should preserve that same ownership model:

- Hotel owns the PMS relationship.
- Hotel owns its phone identity.
- Hotel owns the Stripe merchant/payment relationship.
- Hotel receives its reservation revenue.
- Allhourdesk provides the intelligence, orchestration, automation, and guest experience.
