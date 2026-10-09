# UML Activity Diagram — Student Advance Booking and Dispatch

**Scope:** Core workflow from booking submission to trip completion.  
**Key:** Swimlanes show responsibility; diamonds are decisions; guards appear in brackets.

```mermaid

flowchart TD
  subgraph S["Student / Boarder"]
    A([Start]) --> B["Enter pickup point, date/time and contact details"]
    H["Review booking status"]
  end
  subgraph SYS["e-TODA System"]
    C["Validate required fields and booking time"]
    D{"[Valid booking details?]"}
    E["Save booking as Pending"]
    F["Show validation error"]
    I["Notify dispatcher in dashboard"]
    J{"[Driver available?]"}
    K["Keep booking Pending and show waiting status"]
    L["Record assigned driver; set Confirmed / Assigned"]
    P["Show assignment confirmation"]
    Q["Record trip completion"]
    R([End])
  end
  subgraph T["TODA Dispatcher / Admin"]
    M["Review pending bookings and driver queue"]
    N["Select available driver"]
    O["Assign driver"]
  end
  subgraph DRI["Tricycle Driver"]
    U["View assignment and pick up student"]
    V["Update trip to In Progress"]
    W["Complete trip"]
  end
  B --> C --> D
  D -->|"[No]"| F --> B
  D -->|"[Yes]"| E --> I --> M --> J
  J -->|"[No]"| K --> H
  J -->|"[Yes]"| N --> O --> L --> P --> H
  P --> U --> V --> W --> Q --> R
```

**Audience and risk reduced:** Developers and dispatch staff; exposes validation, no-driver-available handling and status handoffs. Status transitions must be kept consistent with `state-machine.md`.
