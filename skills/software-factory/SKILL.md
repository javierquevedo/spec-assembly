---
name: software-factory
description: Build an application or feature from a spec using a coordinator and parallel Codex subagents for spec review, design, implementation, and acceptance testing. Use for end-to-end software factory runs.
---

# Software factory

The main agent owns the feature from spec to working software. Use the session's native subagent tools to run independent assignments concurrently. Keep coordination in the main chat. Workers execute their assigned slice and report back. If delegation is unavailable, disclose the limitation and carry out the stages locally unless parallel execution is a strict requirement.

## Git workflow

Always work on a feature branch in the target application repository. Before editing project files, create or select a branch for the task. Use `feature/<short-description>` for new branches.

Ask the user for explicit approval before every commit, every push, and every PR creation. This includes pushes that update an existing PR. Present the changes, validation results, and intended action before asking. Approval of the design or implementation plan authorizes implementation work. Git and PR approvals must explicitly cover each stated action. When requesting several actions together, obtain approval for each.

Include these rules in every worker assignment. The coordinator owns commits, pushes, and PR creation. Workers return their changes and evidence to the coordinator.

## Review the spec and plan

Run in the application workspace selected by the user. Treat the skill checkout as a read-only source of workflow instructions. Read the supplied spec, target workspace, project instructions, and existing run/test commands. In an empty project, infer the smallest suitable stack from the intended platform and record the choice. If no feature or spec was supplied, ask for the behavior to build.

Dispatch independent read-only reviews in parallel. Have one agent turn the spec into observable acceptance criteria and flag consequential ambiguities. Have another inspect the codebase and propose an implementation plan with dependencies and checks. For UI work, assign a design pass covering the primary journey, layout, component reuse, responsive behavior, keyboard interaction, and relevant empty, loading and error states. Prepare an inspectable mockup or isolated prototype for UI features. For a CLI or API, show representative inputs, outputs, and error behavior. Keep review artifacts separate from production code.

Reconcile the proposals into a short plan in the main chat. Give each acceptance criterion an identifier and an observable result. Identify what the user can do when the feature is complete, how each outcome will be checked, and which changes can proceed together. Resolve reversible details using project conventions. Ask about conflicting requirements only when the answer affects the product materially. Continue independent planning while awaiting an answer.

Keep a feature brief in `.spec-assembly/features/<feature-slug>/brief.md` in the application repository. Record the spec, design and plan revisions, acceptance criteria, decisions, task owners and dependencies, approval status, and verification evidence. Update it as the run progresses so another chat can resume from it. Before approval, this file and isolated design artifacts are the only project files the factory may create.

## Required user checkpoint

Present the design and implementation plan together, each with its own revision and approval status. Include the inspectable design artifact or examples, architecture decisions, task owners, shared interfaces, dependencies, parallel work, and how each acceptance criterion will be tested. State unresolved product questions. On a revision, identify what changed and whether it affects either prior approval. Ask the user to approve both or identify changes. End the turn at this checkpoint.

Begin implementation only after the user explicitly approves both current revisions. Before then, limit every assignment to review, design, or planning. Hold off on scaffolding the app, installing its dependencies, writing production code or tests, and dispatching builders. Preserve approval of an unchanged part when the other is revised. If a requested change affects both, show both revised parts for approval. Silence or a general request to try the factory does not approve a feature proposal.

## Build and integrate

For each worker, supply the relevant spec excerpt, acceptance criteria, owned files or component boundary, shared interfaces, dependencies, allowed actions, and expected evidence. Assign one writer per shared file, including manifests and lockfiles. Agree on contracts before launching dependent implementations. Dispatch a task only when its prerequisites are satisfied. Run ready independent slices in parallel up to available capacity. When there is only one code slice, pair its implementer with a worker designing acceptance checks. Only the coordinator changes shared contracts or assigns further workers.

Maintain a compact list of assignments, owners and status in the main chat and feature brief. Record both approved revisions in the brief. If a discovery materially changes the approved design, scope, or plan, pause affected workers, show the revision and its impact, and obtain renewed approval before resuming that work. Ordinary fixes within the approved plan can proceed. Require each worker to return changes, checks actually run, and unresolved issues. When a worker stalls, inspect partial edits, diagnose the cause, and end or reassign its ownership before another writer takes over. After repeated failed attempts, present the concrete blocker or decision needed instead of repeating the same assignment.

The coordinator owns integration. Inspect the combined diff (or new files in an empty workspace), resolve interface mismatches, and exercise the feature through the same entry point a user would use.

## Verify and finish

Give a reviewer the original spec and integrated implementation. Ask for independent verification of each acceptance criterion and reproducible findings. For every criterion, record the command or interaction, expected and observed results, and tested code revision in the feature brief. For UI work, launch and inspect the rendered flow at relevant viewport sizes and exercise its primary interactions when tools permit. Run applicable project checks against the integrated result.

Route failures back to the responsible owner, integrate the fix, and rerun the failing check plus affected regressions. Replace stale evidence after a fix. Continue while a concrete next step can improve the result. If progress requires credentials, a product decision, or an unavailable environment, report the exact missing prerequisite and which criteria remain unverified.

Deliver the implemented behavior, how to run or try it, and the evidence for each acceptance criterion. Distinguish passing checks, observed failures, and checks that could not run. Claim completion only when the required behavior has been verified.

## Review before publishing

When the task is ready for the user to review before a push or PR, present a concise summary of the key changes and their user-visible effect. Include the files or components changed, validation results, and any unresolved issues. Show the proposed commit message and PR title when relevant, and give the user a way to inspect the diff. Ask for explicit approval for each proposed commit, push, or PR creation. If the user requests changes, make them and refresh the summary and evidence before asking again. After an approved push, ask separately before creating the PR unless the user already approved that specific PR creation. Require fresh push approval for later updates to an existing PR.
