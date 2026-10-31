# Super Autopilot

An AI agent skill that helps you go from a development request to a verified result. It plans the work, follows the plan, and checks and fixes issues along the way.

## Why use it?

- **One starting point:** Give your agent a task and let it work through the full plan.
- **Less back-and-forth:** It asks only when a decision or permission is genuinely needed.
- **Verification built in:** It checks the result, investigates failures, and repeats affected checks after fixes.
- **Honest results:** It reports what was verified and identifies blockers instead of claiming unfinished work is done.

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

Super Autopilot will inspect the project, make or resume a plan, implement the tasks, verify the result, and report what happened. The verification loop is included; you do not need to install `iterate-until-verified` separately.

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
