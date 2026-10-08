---
type: llm
---

PASS if a diagram shows all five components (load balancer, two app servers, Redis, Postgres primary, read replica) and how requests and data move between them (for example reads to the replica, writes to the primary, cache in front of the database), with at most a few short lines of text around it.
FAIL if there is no diagram, a component is missing, or the explanation is mainly long prose.
