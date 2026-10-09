# UML Class Diagram — e-TODA Domain Model

**Scope:** Core domain classes, typed attributes, association multiplicities and status enumerations.  
**Key:** `1` and `0..*` denote multiplicity; enums constrain status values.

```mermaid
classDiagram
class User {
  +int id
  +string fullName
  +string email
  +string passwordHash
  +UserRole role
  +datetime createdAt
}
class StudentProfile {
  +int id
  +int userId
  +string studentNumber
  +string pickupAddress
}
class Driver {
  +int id
  +int userId
  +string licenseNumber
  +DriverAvailability availability
}
class Booking {
  +int id
  +int studentId
  +int assignedDriverId
  +string pickupPoint
  +datetime scheduledAt
  +string contactNumber
  +BookingStatus status
  +datetime createdAt
}
class Trip {
  +int id
  +int bookingId
  +datetime startedAt
  +datetime completedAt
  +TripStatus status
}
class InAppNotification {
  +int id
  +int userId
  +int bookingId
  +string message
  +datetime createdAt
  +bool isRead
}
class UserRole {
  <<enumeration>>
  STUDENT
  DRIVER
  DISPATCHER
}
class DriverAvailability {
  <<enumeration>>
  AVAILABLE
  UNAVAILABLE
}
class BookingStatus {
  <<enumeration>>
  PENDING
  ASSIGNED
  IN_PROGRESS
  COMPLETED
  CANCELLED
  REJECTED
}
class TripStatus {
  <<enumeration>>
  SCHEDULED
  IN_PROGRESS
  COMPLETED
  CANCELLED
}
User "1" --> "0..1" StudentProfile : has profile
User "1" --> "0..1" Driver : driver account
StudentProfile "1" --> "0..*" Booking : requests
Driver "0..1" --> "0..*" Booking : assigned to
Booking "1" --> "0..1" Trip : creates
User "1" --> "0..*" InAppNotification : receives
Booking "1" --> "0..*" InAppNotification : triggers
```

**Audience and risk reduced:** Developers and database designers; reduces risk of ambiguous ownership, missing relationships and inconsistent status values. Passwords are stored as hashes, never plaintext. Confirm whether student number and license number are required before final schema design.
