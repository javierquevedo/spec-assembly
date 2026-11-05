# Software factory

This repository versions the Codex workflow. Open a separate application repository as your working directory for each factory run. Application code, dependencies, and tests belong to that project.

## Try it in an application repository

In a Codex chat opened in the application directory, give the absolute path to the skill in your factory checkout and describe your feature. For example:

> Use the software-factory skill at /Users/senc/dev/factory/skills/software-factory/SKILL.md. Build a CLI in this project that counts nonblank lines from stdin. Show me the design and implementation plan for approval.

On another machine, substitute the path to your factory checkout. The coordinator pauses for explicit approval of both the design and the implementation plan before dispatching builders. You can approve one part and request revisions to the other.

To share the workflow, push this repository to your own Git remote. Other users can clone it alongside their application repositories and reference their local copy of the skill.
