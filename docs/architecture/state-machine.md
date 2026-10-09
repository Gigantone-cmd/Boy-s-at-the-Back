# UML State Machine — Booking Lifecycle

**Scope:** State transitions for the main status-bearing entity, `Booking`.  
**Key:** Arrows are events that trigger a transition; initial/final nodes show lifecycle boundaries.

```mermaid
stateDiagram-v2
    [*] --> Pending: submit valid booking
    Pending --> Assigned: dispatcher assigns available driver
    Pending --> Cancelled: student cancels pending booking
    Pending --> Rejected: dispatcher rejects booking
    Assigned --> InProgress: driver starts trip
    Assigned --> Cancelled: dispatcher cancels assignment
    InProgress --> Completed: driver marks trip complete
    Completed --> [*]
    Cancelled --> [*]
    Rejected --> [*]
```

**Audience and risk reduced:** Developers, dispatchers and QA; reduces inconsistent booking status transitions. The exact state names must match the `BookingStatus` enumeration in `class.md`. `TripStatus` records trip execution separately and should not replace booking status.
