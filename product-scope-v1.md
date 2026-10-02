# Allhourdesk Product Scope & Vision — V1

**Status:** Latest agreed product direction  
**Decision date:** 2 October 2026  
**Supersedes:** The broader initial assumption that direct PMS integration is required for the core Allhourdesk launch experience.

## Decision

The initial Allhourdesk scope and vision is being deliberately narrowed to optimize for **time to market, simplicity, reliability, and market validation**.

For V1, Allhourdesk will primarily operate as an **AI-powered hotel reservation channel**, rather than attempting to become a complete AI front-desk/PMS operations layer.

The primary hotel-system integration for this scope should be the **channel manager / distribution layer**. Direct PMS integrations are deferred as a later product expansion and will be prioritized based on actual customer demand.

The existing Apaleo integration remains valuable and should not be discarded. It becomes the foundation/proof point for a future PMS Operations capability rather than a prerequisite for the core V1 reservation product.

## V1 Product Promise

Allhourdesk provides an AI reservations desk that can:

1. Answer hotel and property questions using the hotel's configured knowledge base / RAG.
2. Search real-time room availability.
3. Retrieve room types and applicable rates/rate plans.
4. Understand relevant booking restrictions and policies exposed through the reservation/distribution layer.
5. Present suitable booking options conversationally.
6. Capture guest and reservation details.
7. Complete the configured payment flow.
8. Create a new reservation and deliver it through the channel manager into the hotel's PMS.
9. Manage the lifecycle of **Allhourdesk-originated reservations** where the connected channel-manager API and booking terms permit it:
   - cancellation according to the booked cancellation policy;
   - amendment according to the booked terms, availability, rates and supported channel functionality.

Allhourdesk does **not** promise general PMS/front-desk operations in V1.

## Product Boundary

### In Scope — Knowledge

Hotel/property questions can be handled through Allhourdesk RAG, for example:

- facilities and amenities;
- parking;
- breakfast;
- pet policy;
- check-in/check-out times as information;
- location and directions;
- room descriptions;
- hotel policies;
- restaurant/spa/facility information;
- other hotel-provided FAQs and knowledge.

Providing information does not imply that Allhourdesk can execute a corresponding PMS operation.

For example, Allhourdesk may tell a guest that normal check-in begins at 15:00, but V1 does not promise to approve or register an early check-in request in the PMS.

### In Scope — Reservation Commerce

The channel-manager integration should support the reservation transaction surface required by Allhourdesk:

- availability;
- inventory;
- room/rate mapping;
- rates and rate plans;
- restrictions such as minimum stay, closed-to-arrival and stop-sell where exposed;
- creation of new reservations;
- guest/contact information required for the reservation;
- reservation identifiers and status;
- cancellation/amendment of Allhourdesk-originated reservations where supported and permitted by the booking terms.

Payment remains a separate Allhourdesk/Stripe workflow and should not require Allhourdesk to become the hotel's merchant of record where avoidable.

## Reservation Ownership Boundary

V1 should distinguish between reservations **originated by Allhourdesk** and reservations originating elsewhere.

### Allhourdesk-originated reservation

Allhourdesk may support:

- retrieving the reservation;
- explaining its booked terms;
- checking amendment availability/rates;
- amending it where permitted;
- cancelling it where permitted;
- initiating the applicable payment/refund workflow where supported by the agreed payment architecture.

The agent must follow the actual booking terms and system rules. It must not independently decide to waive a non-refundable policy or grant an exception.

### Reservation from another channel

Examples include Booking.com, Expedia, direct website bookings not created by Allhourdesk, travel-agent reservations, or reservations manually entered by the hotel.

V1 should **not promise to manage these reservations**.

The guest should be directed to the hotel and/or originating booking channel according to the hotel's configured escalation policy.

## Explicitly Out of Scope for V1

Direct PMS operational workflows are deferred, including examples such as:

- check-in/check-out execution;
- room assignment;
- housekeeping operations;
- folio/invoice operations;
- general guest-profile management;
- arbitrary modifications to reservations originating through other channels;
- minibar or in-stay charges;
- adding PMS-specific products/services to an existing stay;
- executing early/late check-in requests;
- executing room upgrades outside the reservation-channel workflow;
- other PMS-specific operational actions.

Allhourdesk can still **answer informational questions** about these subjects when the answer exists in the hotel's knowledge base. Execution is the boundary.

## Why the Scope Is Changing

The original direction assumed that broad direct PMS integration would be central to the initial product.

That introduces substantial complexity before market validation.

Different PMS products expose different capabilities, concepts and workflows. A capability such as early check-in may be represented as a native operation in one PMS, an attribute or note in another, require a different workflow in another, or not be available through the API at all.

Therefore direct PMS support is not merely an adapter problem. It can change:

- agent workflows;
- tool definitions;
- prompts;
- RAG context;
- capability detection;
- hotel configuration;
- onboarding;
- exception handling;
- testing;
- support;
- security and permissions.

Building and maintaining these differences across multiple PMS platforms would increase development time and operational risk before Allhourdesk has sufficient market evidence to justify the investment.

## V1 Architecture

```text
Guest
  |
  v
Allhourdesk AI
  |
  +---------------- Hotel questions ----------------+
  |                                                  |
  |                                                 RAG
  |
  +---------------- Reservation intent
                         |
                         v
                 Reservation workflow
                         |
             +-----------+-----------+
             |                       |
          Payment               Channel Manager
          (Stripe)                    |
                                      v
                                     PMS
```

The channel manager is the primary abstraction for reservation commerce.

The underlying PMS should, as far as possible, be irrelevant to the V1 reservation workflow.

## Strategic Benefit

This approach deliberately trades some initial feature breadth for:

- faster time to market;
- a smaller integration surface;
- simpler hotel onboarding;
- more consistent AI behavior;
- easier testing and certification;
- lower maintenance burden;
- clearer customer expectations;
- broader potential hotel coverage through channel-manager connectivity;
- the ability to validate demand before investing in PMS-specific workflows.

This is an intentional product decision, not simply a technical limitation.

## Future Product Expansion

After Allhourdesk gains market traction, direct PMS integrations can be introduced as a separate capability/package.

A possible future packaging model is:

### Allhourdesk Reservations

Channel-manager based:

- AI phone/communications handling;
- hotel knowledge/RAG;
- availability and rate search;
- new reservations;
- payment workflow;
- management of eligible Allhourdesk-originated reservations.

### Allhourdesk PMS Operations / Front Desk

Direct PMS integrations:

- existing reservation servicing;
- PMS-native guest operations;
- early/late check-in workflows;
- extras and service management;
- guest profiles;
- folio-related workflows;
- check-in/check-out;
- other PMS-specific operational capabilities.

PMS integrations should then be added **one by one based on demonstrated customer demand**, rather than attempting to predict the entire market before launch.

For example, if early customers disproportionately use Mews, Mews becomes a priority. If enterprise demand creates a strong OPERA requirement, OPERA/OHIP can be prioritized accordingly.

## Capability-Based PMS Design

When direct PMS integrations are introduced, Allhourdesk should not assume every PMS provides identical functionality.

Each PMS adapter should expose an explicit capability model, conceptually:

```text
PMS: Example

Capabilities
  reservation_lookup:       yes
  reservation_amendment:    yes
  reservation_cancellation: yes
  early_checkin_request:    no
  room_assignment:          yes
  guest_profile_update:     limited
  folio_access:             no
```

Agent workflows should be enabled from capabilities rather than hard-coded assumptions about what every PMS can do.

This keeps PMS-specific behavior outside the core conversational/reservation engine as much as possible.

## Existing Apaleo Integration

The existing Apaleo integration remains an asset.

It should be treated as:

1. an existing direct-PMS capability;
2. a reference implementation for the future PMS abstraction/capability model;
3. potentially an enhanced integration for Apaleo customers;
4. the starting point for the future PMS Operations package.

However, **additional direct PMS integrations are not a launch dependency for V1**.

## Current Product Principle

> **First prove that hotels want Allhourdesk to answer their calls, answer guest questions, and convert those conversations into reservations. Then let real customer demand determine which front-desk/PMS operations we build.**

The near-term engineering priority is therefore:

**Channel-manager connectivity + excellent RAG + reliable conversational reservation flow + payments + telephony + simple hotel onboarding + clear escalation.**

Broad PMS operational coverage comes after product-market evidence.
