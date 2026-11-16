# Optional controls for external changes

Use this extension when a task affects services, shared infrastructure state, data, identities, releases, or other controlled external systems. The core method still applies. A code-only task does not need irrelevant operational fields.

## Before a controlled checkpoint

Record the action, exact target/environment, effective executor, affected consumers, expected effect, scope limits, and existing authorization. Include meaningful failure/stop conditions, cost or maintenance constraints, and a recovery path. Separate preparation, execution, verification, and cleanup only when those boundaries matter.

Produce the candidate and needed evidence before requesting a decision. Record source revision, artifact digest where applicable, execution inputs and tool versions, access boundaries, evidence location, and freshness conditions. Use [the checkpoint template](../templates/checkpoint.md).

## Domain-specific evidence

| Domain | Additional facts to record |
| --- | --- |
| Infrastructure as code | Resolved backend/key/workspace, state identity/version, resource scope, plan artifact, effective provider/backend identities, lock owner, and relevant live observations |
| Application release | Immutable build or release revision, configuration version, environments, migrations, health checks, traffic transition, and rollback limits |
| Database or data migration | Data authority, compatibility, reversible/irreversible steps, recovery evidence, consumers, verification queries, and cutover/rollback conditions |
| Access or credentials | Principal, allowed actions/resources, duration, consumers, retained recovery access, and removal/expiry verification for temporary access |
| Cross-repository work | Owning repository for each change, compatibility sequence, integration evidence, and shared-resource executor |

A planning command may write a lock or upload artifacts. A connection probe may open a session. A repository trigger may deploy. Include those effects in the scope instead of calling every preparatory action read-only.

## Execution and interruption

Verify the exact reviewed artifact, source, inputs, identities, target, ownership, authorization, and required freshness immediately before execution. For saved-plan systems, execute the reviewed saved plan where supported. If the candidate must be regenerated, apply the review rules to the replacement; an equivalence exception must be deliberately specified and validated for its bounded use.

Use native locking or a serialized executor for shared state. A local note cannot exclude other clients. Unchanged state metadata alone does not prove unchanged live resources.

When a step fails or its result is uncertain, reconcile the actual system before retrying. Record completed effects, running processes, state changes, and the next safe action. A restored configuration or old state file does not prove data or runtime recovery.

Verify the intended service/data/access result, required recovery behavior, and cleanup. If live checks are outstanding, the task remains incomplete unless an authorized scope change moves that outcome to a separately tracked task. Evidence uploads must use authorized storage with appropriate readership and retention; public issues receive only sanitized summaries.
