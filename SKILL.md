---
name: super-autopilot
description: Autonomously complete a software development task from repository analysis through planning, implementation, verification, and reporting.
disable-model-invocation: true
---

# Super Autopilot

Complete the user's development task end-to-end within the requested scope. This skill incorporates the task-preserving verification loop from `iterate-until-verified`; the user does not need to invoke that skill separately. Continue autonomously through safe, reversible steps.

Keep the original request authoritative: preserve its deliverables, constraints, exclusions, and authorization boundaries. For a strictly read-only request, do not write files; keep any necessary plan and progress in memory. For a plan-only request, do not implement. Use the Superpowers skills below when available; if a required skill or tool is unavailable, use the closest safe manual equivalent and disclose the limitation.

This is one workflow: it borrows useful OMX techniques without starting a second orchestrator. Do not nest or automatically invoke an OMX mode because a subskill references it; use a safe manual equivalent or report a required-capability conflict. A separate, explicit request for a native OMX workflow must follow its real runtime, handoffs, gates, and stop conditions. Never claim an OMX mode, native role, consensus, state, hook, or review ran unless it actually did.

## Phase 1: Analyze

- Inspect the repository, existing architecture, relevant instructions, current changes, and relevant plans before modifying files.
- Use `brainstorming` to clarify requirements. Separate established facts, assumptions, and decisions that belong to the user; inspect discoverable facts before asking. For ambiguous or risky work, pressure-test important assumptions and boundaries with concrete scenarios or counterexamples.
- Ask a focused question when a missing decision would materially change the outcome and cannot be resolved safely from context, or when authorization is required. Wait for the answer before taking the affected action, but continue other safe, independent in-scope work. Otherwise make a reasonable in-scope decision and proceed without routine approval pauses. Do not fabricate interview scores or label this analysis as a completed native `deep-interview`.
- Identify the desired outcome, scope, non-goals, constraints, preserved behavior, and testable acceptance criteria. Translate subjective goals into observable checks; do not invent a benchmark or expand the request.

## Phase 2: Plan

- Reuse the active plan when identifiable; otherwise use `writing-plans` to create a right-sized implementation plan with concrete, dependency-ordered tasks, acceptance criteria, and verification steps. When resuming, read the plan and progress, reconcile completion markers with actual changes, evidence, and parked findings, reopen invalid or incomplete tasks, and continue from the first unfinished task. If the active plan cannot be identified reliably, ask rather than guessing.
- Record compact quality gates for the requested outcome: for each gate, specify its verification method, observable pass condition, and evidence. Include relevant normal, failure, and regression paths without adding checks solely for ceremony.
- For nontrivial or risky work, review the plan before execution: compare genuine alternatives and tradeoffs, check dependencies and interfaces, and consider relevant failure and recovery scenarios. Use a separate reviewer when useful and available; otherwise label the review as self-review, not consensus.
- Aim for at least 95% accuracy and at least 95% quality where meaningful, defensible task-specific percentage measures exist; never invent an accuracy percentage or claim a universal guarantee. For a measurable accuracy or quality target, define the metric, evaluator, threshold, and representative population, numerator and denominator or scoring rubric as applicable; report actual evidence and limitations. If a required numeric metric cannot be measured reliably, mark that gate blocked; when an aspirational score is unmeasurable, report it as unverified. A percentage never excuses a failed required criterion or blocking finding; `perfect` means passing all specified gates, not proof that defects are impossible.
- Track the plan and task progress in files, using the repository's established location when available. Do not overwrite unrelated plans or existing user work.
- The user's request authorizes execution within its scope; do not pause for routine design or plan approval. Do not claim an unseen design or plan was reviewed or approved by the user. Ask when a decision requires authorization or the scope materially changes.

## Phase 3: Execute

- Use `subagent-driven-development` when supported and appropriate; otherwise use `executing-plans` when available or execute directly. Delegate only genuinely independent work with clear context and non-overlapping ownership; the lead integrates the result. Give each worker the original task and applicable constraints, including preservation of user work and no commits or branches unless explicitly authorized; replace conflicting template instructions. Give any reviewer the task, gates, artifact, real references, and necessary test evidence without the implementer's verdict or rationale unless needed to reproduce a check.
- Implement every task and acceptance criterion within the requested scope. Use `test-driven-development` where appropriate. Do not stop at a phase boundary, ask whether to continue, or end a turn merely to summarize progress.
- Persist progress after each task, including status, verification evidence, decisions, and blockers. Mark a task complete only when its acceptance criteria and all task-specific required gates pass and no in-scope blocking finding remains, even if a review-round cap permits deferral. Otherwise record it as pending or blocked; reopen it if later verification invalidates it.
- If the plan is wrong, make and record the smallest safe in-scope correction, then continue. If a task is blocked, continue independent tasks when safe; do not claim dependent tasks are complete.
- Preserve existing user changes and do not create commits or branches unless explicitly requested. Unless project instructions or the user require isolation, work in the current checkout, including `main` or `master`; do not pause for an integration menu when no integration action was requested. If required isolation cannot be achieved safely, report the blocker.
- Replace commit-only review helpers with a safe task-scoped baseline and review of staged, unstaged, and untracked task changes without changing the index. Do not use a helper that records a task complete before its required gates pass.
- Before running helpers that create or overwrite files, verify destination ownership. Treat pre-existing markerless or mismatched workspaces as unowned; use a fresh collision-free location or a safe manual equivalent.

## Phase 4: Verify

- Run relevant checks starting with the smallest targeted test, then expand to applicable integration, regression, typecheck, lint, build, or end-to-end checks. Inspect command side effects and isolate test data and output before running anything that could affect existing user work.
- For runnable flows where risk warrants it, exercise adversarial dynamic scenarios such as malformed input, interruption, stale state, timeouts, and recovery. Record expected versus actual behavior and clean up only task-owned artifacts. Use safe substitutes when needed, but do not call ordinary checks `ultraqa` or pretend a blocked required scenario passed.
- For every applicable gate, record `pass`, `fail`, or `blocked` with actual evidence, including relevant commands, exit status, failures, skips, and timeouts. Verify consequential factual claims against appropriate sources or direct evidence. A test result, rendered artifact, source, or other task-appropriate check is evidence; confidence or a self-rating is not.
- For a failed gate, use `systematic-debugging` when available, identify the cause, make the smallest in-scope fix, and rerun that gate and affected regression checks. Continue this loop while a safe action can make meaningful progress. Do not repeat the same failing action unchanged or weaken a required gate to claim success. A review or QA cycle cap is a circuit breaker, not a pass; do not restart the same capped loop unchanged or mark unresolved work complete.
- Review the integrated changes against the original request and plan. When an independent reviewer is available and useful, provide the original task, gates, artifact, and real reference without the implementer's self-assessment. Otherwise perform and disclose a separate self-review; if independent verification is required but unavailable, mark that gate blocked.
- If verification invalidates the plan, update the plan and continue through the affected tasks and checks. Report unrelated failures and unavailable checks without claiming they passed.

## Phase 5: Finish

- Use `verification-before-completion` when available. Claim fully verified completion only when every requested task and required gate passes with fresh evidence and no in-scope blocking finding remains. Failed, skipped, timed-out, or unavailable required checks are verification gaps.
- Give one concise final report covering changes, actual checks and results, and any unresolved issues, blockers, or remaining tasks. Never claim an independent review, test, or outcome that did not occur.

## Safety

- Do not deploy, publish, push, merge, delete user data, or change secrets without authorization. Do not create commits or branches unless explicitly requested.
- When a necessary decision or authorization is missing, do not perform the affected action; continue other safe, independent in-scope work. Stop when the user requests it or no safe in-scope action can make progress. Explain the exact blocker, required decision or authorization, and minimum next step.
- Preserve plan and progress records and unrelated state. Do not repeatedly retry the same failing action without new evidence or a meaningful change.
