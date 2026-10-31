# Super Autopilot

**The lazy workflow for developers: give your AI agent a task once and let it take care of the rest.**

Super Autopilot helps your agent turn a request into a verified result. It plans the work, follows the plan, checks the outcome, fixes problems, and repeats the checks until the required work is verified or it hits a genuine blocker.

## Why use it?

- **One request, less micromanagement:** Describe the outcome and let your agent work through the plan without routine check-ins.
- **A built-in feedback loop:** Plan → build → check → fix → check again. Failed checks lead to investigation and another pass, not a premature finish.
- **Progress that stays on track:** The agent records progress, revisits unfinished tasks, and checks the result against your original request.
- **A useful final report:** See what changed, what was verified, and any blockers or checks that could not be completed.

You stay involved when an essential decision, permission, or a blocker requires your input. The goal is less busywork—not skipping verification or pretending every task can run without limits.

## Install

For the intended workflow, first install [Superpowers](https://github.com/obra/superpowers):

```sh
npx skills add obra/superpowers
```

Then install Super Autopilot:

```sh
npx skills add ChinJow/super-autopilot --skill super-autopilot
```

The installer is `skills`, with an **s**. It requires Node.js 22.20 or newer and supports multiple coding agents. Follow the prompts to choose your agent and installation scope. For details, see the [skills CLI documentation](https://github.com/vercel-labs/skills).

Superpowers provides the planning, execution, debugging, and verification skills used by this workflow. If a required skill or tool is unavailable, Super Autopilot instructs the agent to use the closest safe alternative and disclose the limitation; installing this skill alone does not install Superpowers.

## Usage

Invoke `super-autopilot` in your agent and describe the task. In Zed, attach `@super-autopilot` to your message. For example:

> Use super-autopilot to add an export button to the settings page. Keep the existing layout, add tests, and do not deploy.

Super Autopilot will inspect the project, make or resume a plan, implement the tasks, verify the result, and report what happened. Its built-in loop checks the work, fixes issues, and verifies the changes again.

It is designed to keep working without routine approval pauses. It will still need your input for essential decisions, required permissions, or blockers it cannot safely resolve.

## Good to know

- Your agent may create plan and progress files for implementation work. Strictly read-only requests do not write files.
- It instructs the agent to preserve existing work and not deploy, push, merge, create commits or branches, or delete user data without authorization.
- It borrows ideas from other workflows but does not automatically run OMX.
- Agent behavior depends on the host, available tools, permissions, and instruction priority. A skill is not a security sandbox and cannot guarantee a particular accuracy rate or defect-free output.
- The skill includes Zed's `disable-model-invocation` frontmatter for manual invocation. Support varies, and strict Agent Skills validators may reject this extra field.
- The `skills` CLI uses network access and documents [telemetry and security-audit requests](https://github.com/vercel-labs/skills/blob/main/docs/troubleshooting.md#telemetry).

## License

[MIT](LICENSE)
