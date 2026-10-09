# Draft ERD — e-TODA MVP

**Scope:** Stored entities, primary/foreign keys, PII marking and cardinalities corresponding to `class.md`.  
**Key:** `PK` = primary key; `FK` = foreign key; `[PII]` = personally identifiable information.

```mermaid
erDiagram
    USERS {
      int id PK
      string full_name "PII"
      string email "PII"
      string password_hash
      string role
      datetime created_at
    }
    STUDENT_PROFILES {
      int id PK
      int user_id FK
      string student_number "PII"
      string pickup_address "PII"
    }
    DRIVERS {
      int id PK
      int user_id FK
      string license_number "PII"
      string availability
    }
    BOOKINGS {
      int id PK
      int student_profile_id FK
      int assigned_driver_id FK
      string pickup_point "PII/location"
      datetime scheduled_at
      string contact_number "PII"
      string status
      datetime created_at
    }
    TRIPS {
      int id PK
      int booking_id FK
      datetime started_at
      datetime completed_at
      string status
    }
    IN_APP_NOTIFICATIONS {
      int id PK
      int user_id FK
      int booking_id FK
      string message
      datetime created_at
      boolean is_read
    }
    USERS ||--o| STUDENT_PROFILES : has
    USERS ||--o| DRIVERS : has
    STUDENT_PROFILES ||--o{ BOOKINGS : requests
    DRIVERS o|--o{ BOOKINGS : assigned_to
    BOOKINGS ||--o| TRIPS : creates
    USERS ||--o{ IN_APP_NOTIFICATIONS : receives
    BOOKINGS ||--o{ IN_APP_NOTIFICATIONS : triggers
```

**Design notes:** Every table has a primary key. `student_profile_id` references `STUDENT_PROFILES.id`; `assigned_driver_id` is nullable and references `DRIVERS.id`; `booking_id` in `TRIPS` should be unique to enforce at most one trip per booking. PII/location fields require access controls and should not be exposed to unauthorized users. Validate final column types and constraints against the actual MVP and repository.
