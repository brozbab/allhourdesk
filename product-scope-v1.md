# Allhourdesk Product Scope & Vision — V1

**Status:** Latest agreed product direction  
**Decision date:** 2 October 2026  
**Supersedes:** The broader initial assumption that direct PMS integration is required for the core Allhourdesk launch experience.

## Decision

The initial Allhourdesk scope and vision is being deliberately narrowed to optimize for **time to market, simplicity, reliability, and market validation**.

For V1, Allhourdesk will primarily operate as an **AI-powered hotel reservation channel**, rather than attempting to become a complete AI front-desk/PMS operations layer.

The primary hotel-system integration for this scope should be the **channel manager / hotel distribution and connectivity layer**. This includes both traditional channel managers and broader distribution networks that can expose hotel inventory to Allhourdesk as an authorized booking/demand partner. Direct PMS integrations are deferred as a later product expansion and will be prioritized based on actual customer demand.

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

The channel manager / distribution network is the primary abstraction for reservation commerce.

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

## Channel Partnership & Go-to-Market Strategy

Channel-manager and hotel-distribution relationships are not only an integration strategy. They are also a potential **customer-acquisition and expansion channel** for Allhourdesk.

Allhourdesk should pursue commercial partnerships with selected channel managers and hotel distribution/connectivity networks. The desired partnership combines two elements:

1. **Connectivity** — Allhourdesk is approved as a booking/demand channel and can access authorized hotel availability, rates, restrictions and reservation operations.
2. **Distribution / GTM** — the partner helps Allhourdesk reach eligible hotels in its network through an agreed referral, marketplace, co-selling, co-marketing, opt-in introduction or similar partner model.

Allhourdesk should not assume that a partner will transfer or expose its raw hotel customer database. The preferred model is an authorized, privacy-compliant route to the partner's hotel ecosystem in which the hotel opts in to engage with or activate Allhourdesk.

### Partner-led customer acquisition

The target flow is:

```text
Channel Manager / Distribution Network
                |
        eligible hotel network
                |
     referral / marketplace /
   co-selling / opt-in introduction
                |
                v
           Allhourdesk
                |
        engages hotelier
                |
                v
      Hotel buys Allhourdesk
                |
                +---- enables Allhourdesk
                |     as booking channel
                |
                +---- partner receives agreed
                      referral / revenue-share
                      commission
```

Where commercially viable, Allhourdesk is willing to pay the partner an agreed commission or recurring revenue share for hotel customers sourced through that partner.

This aligns incentives: the partner is not merely certifying another technical integration; it has a commercial reason to introduce and promote Allhourdesk across its hotel ecosystem.

### Customer acquisition engines

The V1 growth strategy therefore has two immediate acquisition engines and one future engine:

**1. Direct hotel sales**

Allhourdesk acquires a hotel directly. During onboarding, the hotel connects a supported channel manager/distribution platform and enables Allhourdesk as an authorized booking channel.

**2. Channel-partner-led acquisition**

A channel manager or distribution partner introduces, markets or makes Allhourdesk discoverable to eligible hotels in its network. Allhourdesk converts and onboards the hotel and pays the agreed partner commission/revenue share.

**3. PMS ecosystem acquisition — later**

When the PMS Operations package is introduced, direct PMS integrations, PMS marketplaces and PMS partner programs become an additional acquisition engine.

### Initial partnership targets

The first commercial/technical discovery wave should engage:

- **SiteMinder** — investigate Channels Plus / SiteConnect and partner-led hotel activation;
- **RateGain** — investigate travel-seller/demand connectivity and access to its hotel supply network;
- **HyperGuest** — investigate demand-partner connectivity and hotel-network distribution;
- **Travelgate** — investigate buyer/connectivity APIs and whether its network can provide a scalable abstraction across multiple supply/channel-manager relationships.

Additional channel managers and distribution networks should be evaluated based on geographic coverage, hotel demand and commercial opportunity, especially in **Europe and the Middle East**.

### Partner evaluation criteria

Each prospective partner should be evaluated on both technical and commercial dimensions:

- addressable hotel footprint in Europe;
- addressable hotel footprint in the Middle East/GCC;
- independent hotel vs chain coverage;
- ability for Allhourdesk to operate as a booking/demand channel;
- real-time availability, inventory, rates and restrictions;
- reservation creation;
- amendment/cancellation of Allhourdesk-originated reservations;
- hotel authorization/activation flow;
- hotel self-service onboarding potential;
- API quality and webhook/event support;
- certification and time to production;
- payment and PCI implications;
- reservation ownership and guest-data rules;
- partner fees;
- hotel fees or commissions;
- referral/revenue-share expectations;
- marketplace/listing opportunities;
- willingness to co-sell/co-market;
- ability to introduce Allhourdesk to eligible hotel customers;
- restrictions on direct commercial engagement with hotels.

### Commercial principle

Allhourdesk should optimize for **distribution leverage, not only API coverage**.

A technically excellent integration with little access to hotel customers may be less valuable at this stage than a partner that provides strong reservation APIs plus an efficient path to hundreds or thousands of potential hotel customers.

The preferred relationship is therefore:

> **One integration + access to a meaningful hotel ecosystem + a mutually beneficial commercial incentive.**

### Multi-partner strategy

Allhourdesk should not make the business dependent on a single channel-manager vendor.

The long-term reservation connectivity layer should support multiple channel managers/distribution networks behind a normalized Allhourdesk reservation interface.

Conceptually:

```text
                    SiteMinder
                        |
                    RateGain
                        |
Hotels ---------- HyperGuest --------+
                        |             |
                    Travelgate        |
                        |             v
                     Others     Allhourdesk
                                   Reservation
                                     Layer
```

This allows Allhourdesk to expand geographic coverage, reduce platform dependency and select the best connectivity/GTM route for each hotel segment.

The immediate objective is **commercial and technical discovery with the leading candidates before committing to unnecessary direct PMS integrations**.

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

**Channel-manager/distribution connectivity + channel-partner GTM relationships + excellent RAG + reliable conversational reservation flow + payments + telephony + simple hotel onboarding + clear escalation.**

Broad PMS operational coverage comes after product-market evidence.
