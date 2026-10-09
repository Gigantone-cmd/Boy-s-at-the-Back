# e-TODA Architecture Views — Activity 7

**Team:** Boy’s at the Back  
**Project:** e-TODA: Tricycle Queuing & Advance Booking App for Students of Sorsogon State University – Bulan Campus  
**Block:** 4-2  
**Date:** October 9, 2026  
**Members:** Niño Gigantone, Arwin Gojo, Julius Glomar, Jamel Bitancor

## Diagram index and owners

| # | Diagram | File | Draft owner | Reviewer |
|---:|---|---|---|---|
| 1 | C4 System Context | `context.md` | Niño Gigantone | Arwin Gojo |
| 2 | C4 Container | `containers.md` | Niño Gigantone | Julius Glomar |
| 3 | Use Case | `use-cases.md` | Arwin Gojo | Jamel Bitancor |
| 4 | Activity | `activity.md` | Arwin Gojo | Julius Glomar |
| 5 | Sequence | `sequence.md` | Jamel Bitancor | Niño Gigantone |
| 6 | Class | `class.md` | Julius Glomar | Arwin Gojo |
| 7 | State Machine | `state-machine.md` | Julius Glomar | Jamel Bitancor |
| 8 | Package | `packages.md` | Niño Gigantone | Jamel Bitancor |
| 9 | UML Component | `components.md` | Jamel Bitancor | Julius Glomar |
| 10 | Provisional Deployment | `deployment.md` | Niño Gigantone | Arwin Gojo |
| 11 | Draft ERD | `erd.md` | Julius Glomar | Jamel Bitancor |

Owners/reviewers are a proposed balanced assignment; the team must confirm actual responsibility and review each diagram before submission.

## Provisional architecture decisions

- Browser-based web application for students/boarders, tricycle drivers and a TODA dispatcher/administrator.
- Provisional stack: Laravel/PHP application and MySQL database; confirm against the team's repository.
- Core workflow: student submits an advance booking, dispatcher assigns an available driver, driver updates trip status.
- In-app notifications only for the MVP; no payment gateway, maps integration or third-party SMS/email is assumed.
- Booking status values are `PENDING`, `ASSIGNED`, `IN_PROGRESS`, `COMPLETED`, `CANCELLED`, and `REJECTED` in both the class and state-machine views.

## Cross-view consistency checklist

- [ ] Actors in `use-cases.md` match `context.md`.
- [ ] Browser, web application and database in `containers.md` match `deployment.md`.
- [ ] Booking statuses in `class.md` match `state-machine.md`.
- [ ] Class associations and ERD foreign keys/cardinalities match.
- [ ] Every Mermaid diagram renders in Mermaid Live Editor or GitHub.
- [ ] Team has confirmed all assumptions against its final MVP feature list and repository.
- [ ] Another team has reviewed the diagram set; record real findings and corrections in the worksheet.
