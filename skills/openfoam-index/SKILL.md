---
name: openfoam-index
description: This skill should be used when users ask how to use openfoam and the correct generated documentation skill must be selected before going deeper into source code.
---

# openfoam Skills Index

## Route the request
- Classify the request into one topic skill before diving into source.
- Prefer workflow-level and behavior-level guidance first; go function-by-function only when requested.

## Generated topic skills
- `openfoam-examples-and-tutorials`: runnable tutorial workflows and validation datasets.
- `openfoam-inputs-and-modeling`: case inputs, model/BC setup, and physical parameterization.
- `openfoam-applications`: `applications/test/*` behavior checks and utility-style test apps.

## Fast startup from repo root
1. Load environment: `source etc/bashrc`.
2. Choose the topic skill and open its playbook:
- `skills/openfoam-examples-and-tutorials/SKILL.md`
- `skills/openfoam-inputs-and-modeling/SKILL.md`
- `skills/openfoam-applications/SKILL.md`
3. Run case-local `Allrun` when present, then validate with that skill's checkpoints.

## Escalation order
1. Start with the topic skill `SKILL.md`.
2. Use the same topic `doc_map.md` for exact runnable docs/scripts:
- `skills/openfoam-examples-and-tutorials/references/doc_map.md`
- `skills/openfoam-inputs-and-modeling/references/doc_map.md`
- `skills/openfoam-applications/references/doc_map.md`
3. If behavior is still ambiguous, inspect the same topic `source_map.md`:
- `skills/openfoam-examples-and-tutorials/references/source_map.md`
- `skills/openfoam-inputs-and-modeling/references/source_map.md`
- `skills/openfoam-applications/references/source_map.md`
4. Use targeted source lookup from repo root: `rg -n "<symbol_or_keyword>" applications src tutorials wmake`.

## Core source directories for deep inspection
- `applications`
- `src`
- `wmake`
