# UML Sequence Diagram — Advance Booking and Driver Assignment

**Scope:** Riskiest MVP flow: submitting a booking and receiving a driver assignment.  
**Key:** Lifelines are participants; solid arrows are synchronous requests; dashed arrows are replies; `alt` shows branches.

```mermaid
sequenceDiagram
    actor Student
    participant Page as Browser Booking Page
    participant API as Laravel Web App / Controller
    participant DB as MySQL Database
    participant Dispatch as TODA Dispatcher
    Student->>Page: Enter pickup, schedule and contact
    Student->>Page: Submit booking
    Page->>API: POST booking form (HTTPS)
    API->>API: Validate fields and scheduled time
    alt Invalid details
        API-->>Page: Validation errors
        Page-->>Student: Show errors and request correction
    else Valid details
        API->>DB: Insert booking with Pending status
        DB-->>API: Booking ID and saved record
        API-->>Page: Booking received / Pending
        Page-->>Student: Show booking reference and status
        API-->>Dispatch: Add pending booking to dispatcher dashboard
        Dispatch->>API: Assign available driver
        API->>DB: Update driver_id and status = Assigned
        DB-->>API: Updated booking
        API-->>Page: Updated status available on refresh
        Page-->>Student: Show assigned driver and confirmation
    end
```

**Audience and risk reduced:** Backend developers and testers; reduces risks of duplicate/missing persistence, unclear validation feedback and booking status not matching the database. Dispatcher assignment is modeled as a dashboard action, not an automatic dispatch integration.
