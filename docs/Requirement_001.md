# Requirement 001 — Shipment Progress Monitoring

**As an** operations coordinator,

**I want to** see the current progress of each shipment and identify shipments that have missed expected milestones,

**So that** I can proactively investigate delays before they affect our customers.

## Acceptance Criteria

- An operator can register a shipment with its origin, destination, carrier and expected milestones.
- The system can receive tracking events associated with a shipment.
- The system maintains the current shipment status based on available events.
- Repeated tracking events do not produce duplicate business effects.
- Late or out-of-order events do not incorrectly regress shipment status.
- The system identifies milestones that have passed their expected completion time without confirmation.
- Operators can retrieve the shipment's event history and outstanding exceptions.