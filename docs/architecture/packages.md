# UML Package Diagram — Provisional Laravel Project Structure

**Scope:** Proposed source folders and dependency direction for e-TODA.  
**Key:** Arrows indicate dependency/import direction.

```mermaid
flowchart TB
  subgraph UI["Presentation"]
    routes["routes/web.php"]
    views["resources/views"]
  end
  subgraph APP["Application"]
    controllers["app/Http/Controllers"]
    requests["app/Http/Requests"]
    services["app/Services"]
  end
  subgraph DOMAIN["Domain / Models"]
    models["app/Models"]
    enums["app/Enums"]
  end
  subgraph INFRA["Infrastructure"]
    migrations["database/migrations"]
    notifications["app/Notifications"]
  end
  routes --> controllers
  views --> routes
  controllers --> requests
  controllers --> services
  services --> models
  services --> notifications
  models --> enums
  migrations --> models
```

**Layering rule:** Views and routes must not query the database directly; controllers validate requests and call application services, which use models and infrastructure adapters. This is a proposed structure to confirm against the actual repository.
