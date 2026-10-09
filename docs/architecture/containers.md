# C4 Container Diagram — e-TODA MVP

**Scope:** Deployable/runtime containers and their communication paths.  
**Key:** Browser = client; Web Application = server-side application; Database = persistent storage.

```mermaid


flowchart TB
    student["Student / Boarder"]
    driver["Tricycle Driver"]
    admin["TODA Dispatcher / Admin"]
    browser["Container: Web Browser<br/>HTML, CSS, JavaScript"]
    app["Container: e-TODA Web Application<br/>Provisional: Laravel / PHP"]
    db[("Container: Relational Database<br/>Provisional: MySQL")]
    student -->|"Uses booking/status pages — HTTPS"| browser
    driver -->|"Uses assigned-trip pages — HTTPS"| browser
    admin -->|"Uses dispatch/dashboard pages — HTTPS"| browser
    browser -->|"Requests pages and submits forms — HTTPS"| app
    app -->|"Reads/writes users, drivers, bookings and notifications — SQL/TCP on private network"| db
```

**Container decision:** The browser UI and Laravel application are shown as separate containers because the browser runs on the user's device while the application runs on a server. MySQL is a separate data container. The stack is provisional and must be confirmed by the team before implementation.
