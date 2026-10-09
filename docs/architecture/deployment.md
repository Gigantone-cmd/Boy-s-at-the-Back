# Provisional — UML Deployment Diagram for e-TODA MVP

**Scope:** Expected deployment nodes, execution environments, artifacts and protocols.  
**Key:** Nodes are execution hosts; artifacts are deployed software; paths show protocols. No provider, secret or real address is assumed.

```mermaid

flowchart TB
  device["Node: Student / Driver / Dispatcher Device"]
  browser["Execution environment: Web Browser"]
  artifactUI["Artifact: HTML / CSS / JavaScript pages"]
  host["Node: Generic Web Hosting Server"]
  runtime["Execution environment: PHP runtime + Laravel"]
  artifactApp["Artifact: e-TODA application"]
  dbhost["Node: Generic Database Server"]
  mysql["Execution environment: MySQL"]
  schema["Artifact: e-TODA schema and migrations"]
  device -->|"local execution"| browser
  browser -->|"HTTPS"| host
  host -->|"runs"| runtime
  runtime -->|"deploys / executes"| artifactApp
  runtime -->|"SQL over private network"| dbhost
  dbhost -->|"runs"| mysql
  mysql -->|"stores"| schema
```

**Provisional note:** Hosting provider, domain, TLS configuration, backups and production network rules have not yet been selected. Use environment variables for configuration and never commit credentials or secrets.
