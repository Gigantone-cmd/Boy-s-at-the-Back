# UML Component Diagram — e-TODA API / Web Application

**Scope:** Components inside the application container and their provided/required interfaces.  
**Key:** Component boxes identify responsibilities; interface labels name contracts between components.

```mermaid

flowchart LR
  browser["Browser UI"]
  auth["Authentication Component"]
  booking["Booking Management Component"]
  dispatch["Dispatch / Driver Queue Component"]
  status["Booking Status Component"]
  notify["In-App Notification Component"]
  repo[("Persistence Interface<br/>Booking / User / Driver repositories")]
  db[("MySQL Database")]
  browser -->|"HTTPS forms/pages"| auth
  browser -->|"HTTPS booking requests"| booking
  browser -->|"HTTPS status requests"| status
  booking -->|"requires: IBookingRepository"| repo
  dispatch -->|"requires: IBookingRepository / IDriverRepository"| repo
  status -->|"requires: IBookingRepository"| repo
  booking -->|"requires: INotificationService"| notify
  dispatch -->|"requires: INotificationService"| notify
  auth -->|"requires: IUserRepository"| repo
  repo -->|"SQL"| db
```

**Interfaces:** Booking Management provides booking create/cancel operations; Dispatch provides driver assignment and availability updates; Status provides booking status queries; Authentication provides sign-in and role checks; Notification provides in-app messages. Persistence is shown as a repository boundary. There are no external services in the proposed MVP; if SMS/email is later added, place it behind an adapter interface.
