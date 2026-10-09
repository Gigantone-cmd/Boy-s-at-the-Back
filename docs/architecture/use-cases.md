# UML Use Case Diagram — e-TODA MVP

**Scope:** Goal-level use cases for the roles identified in the system context.  
**Key:** Actors are roles; ovals are user goals inside the e-TODA system boundary.

```mermaid

flowchart LR
    student["Student / Boarder"]
    driver["Tricycle Driver"]
    admin["TODA Dispatcher / Admin"]
    subgraph system["e-TODA MVP"]
      UC1(["Create account / sign in"])
      UC2(["Submit advance booking"])
      UC3(["View booking status"])
      UC4(["Cancel pending booking"])
      UC5(["View assigned bookings"])
      UC6(["Update trip status"])
      UC7(["Manage driver availability"])
      UC8(["Assign driver to booking"])
      UC9(["Monitor queue and bookings"])
      UC10(["Manage user and driver records"])
    end
    student --- UC1
    student --- UC2
    student --- UC3
    student --- UC4
    driver --- UC1
    driver --- UC5
    driver --- UC6
    admin --- UC1
    admin --- UC7
    admin --- UC8
    admin --- UC9
    admin --- UC10
```

**Audience and risk reduced:** Product owner, students and developers; reduces the risk of missing a user role or a must-have user goal. Confirm the final must-have list with the MVP feature list before coding.
