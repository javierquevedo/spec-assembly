# Spec Assembly

A Codex software factory where coordinated agents turn specs into tested applications, with your approval of the design and implementation plan before building.

This repository versions the Codex workflow. Open a separate application repository as your working directory for each factory run. Application code, dependencies, and tests belong to that project.

## Try it in an application repository

Clone this repository, then open a Codex chat in your application directory. Replace `<absolute-path-to-spec-assembly>` in the example below with the absolute path to your clone and describe your feature.

> Use the software-factory skill at <absolute-path-to-spec-assembly>/skills/software-factory/SKILL.md. Build a CLI in this project that counts nonblank lines from stdin. Show me the design and implementation plan for approval.

The coordinator pauses for explicit approval of both the design and the implementation plan before dispatching builders. You can approve one part and request revisions to the other.

To share the workflow, push this repository to your own Git remote. Other users can clone it alongside their application repositories and reference their local copy of the skill.
