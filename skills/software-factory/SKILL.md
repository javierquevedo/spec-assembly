---
name: software-factory
description: Build an application or feature from a spec using a coordinator and parallel Codex subagents for spec review, design, implementation, and acceptance testing. Use for end-to-end software factory runs.
---

# Software factory

The main agent owns the feature from spec to working software. Use the session's native subagent tools to run independent assignments concurrently. Keep coordination in the main chat. Workers execute their assigned slice and report back. If delegation is unavailable, disclose the limitation and carry out the stages locally unless parallel execution is a strict requirement.

## Review the spec and plan

Run in the application workspace selected by the user. Treat the skill checkout as a read-only source of workflow instructions. Read the supplied spec, target workspace, project instructions, and existing run/test commands. In an empty project, infer the smallest suitable stack from the intended platform and record the choice. If no feature or spec was supplied, ask for the behavior to build.

Dispatch independent read-only reviews in parallel. Have one agent turn the spec into observable acceptance criteria and flag consequential ambiguities. Have another inspect the codebase and propose an implementation plan with dependencies and checks. For UI work, assign a design pass covering the primary journey, layout, component reuse, responsive behavior, keyboard interaction, and relevant empty, loading and error states. Prepare an inspectable mockup or isolated prototype for UI features. For a CLI or API, show representative inputs, outputs, and error behavior. Keep review artifacts separate from production code.

Reconcile the proposals into a short plan in the main chat. Identify what the user can do when the feature is complete, how each outcome will be checked, and which changes can proceed together. Resolve reversible details using project conventions. Ask about conflicting requirements only when the answer affects the product materially. Continue independent planning while awaiting an answer.

## Required user checkpoint

Present the design and implementation plan together, each with its own revision and approval status. Include the design artifact or examples, task owners, dependencies, parallel work, and how each acceptance criterion will be tested. Ask the user to approve both or identify changes. End the turn at this checkpoint.

Begin implementation only after the user explicitly approves both current revisions. Before then, limit every assignment to review, design, or planning. Hold off on scaffolding the app, installing its dependencies, writing production code or tests, and dispatching builders. Preserve approval of an unchanged part when the other is revised. If a requested change affects both, show both revised parts for approval. Silence or a general request to try the factory does not approve a feature proposal.

## Build and integrate

For each worker, supply the relevant spec excerpt, acceptance criteria, owned files or component boundary, shared interfaces, dependencies, and expected evidence. Assign one writer per shared file, including manifests and lockfiles. Agree on contracts before launching dependent implementations. Run independent slices in parallel up to available capacity. When there is only one code slice, pair its implementer with a worker designing acceptance checks.

Maintain a compact list of assignments, owners and status in the main chat. Record both approved revisions in the feature brief. If a discovery materially changes the approved design, scope, or plan, pause affected workers, show the revision and its impact, and obtain renewed approval before resuming that work. Ordinary fixes within the approved plan can proceed. Require each worker to return changes, checks actually run, and unresolved issues. When a worker stalls or fails, inspect partial edits and end or reassign its ownership before another writer takes over.

The coordinator owns integration. Inspect the combined diff (or new files in an empty workspace), resolve interface mismatches, and exercise the feature through the same entry point a user would use.

## Verify and finish

Give a reviewer the original spec and integrated implementation. Ask for independent verification of each acceptance criterion and reproducible findings. For UI work, launch and inspect the rendered flow at relevant viewport sizes and exercise its primary interactions when tools permit. Run applicable project checks against the integrated result.

Route failures back to the responsible owner, integrate the fix, and rerun the failing check plus affected regressions. Continue while a concrete next step can improve the result. If progress requires credentials, a product decision, or an unavailable environment, report the exact missing prerequisite and which criteria remain unverified.

Deliver the implemented behavior, how to run or try it, and the evidence for each acceptance criterion. Distinguish passing checks, observed failures, and checks that could not run. Claim completion only when the required behavior has been verified.
