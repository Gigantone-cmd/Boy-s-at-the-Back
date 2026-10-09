# C4 System Context — e-TODA MVP

**Scope:** People and external systems interacting with the e-TODA tricycle queuing and advance-booking system.  
**Key:** Person = user role; System = software system; arrows = purpose of interaction.

```mermaid
flowchart TB
    student["Person: Student / Boarder<br/>Requests a tricycle booking and checks booking status"]
    driver["Person: Tricycle Driver<br/>Views assigned bookings and updates trip status"]
    dispatcher["Person: TODA Dispatcher / Administrator<br/>Manages driver availability, queue and booking assignments"]
    etoda["System: e-TODA MVP<br/>Web application for advance booking, queue visibility and driver dispatch"]
    student -->|"Submit booking; view confirmation and status (HTTPS)"| etoda
    driver -->|"View assigned trips; accept/update trip status (HTTPS)"| etoda
    dispatcher -->|"Maintain driver records; assign bookings; monitor queue (HTTPS)"| etoda
```

**Assumptions to verify:** The MVP is a browser-based web app; students, drivers and an authorized TODA dispatcher/admin are its roles. No payment gateway, maps API or third-party messaging service is required in the first MVP. Notifications are displayed in the application.
