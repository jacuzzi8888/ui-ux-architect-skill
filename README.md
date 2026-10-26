# UI/UX Architect Skill

A portable AI skill for planning, auditing, improving, and implementing digital interfaces.

This repository contains a reusable instruction file designed for AI agents that help with UI and UX work. The skill is written to be useful across different tools and workflows, with a strong beginner-friendly bias and a clear rule that the user remains the final decision maker on design direction.

## What This Skill Does

The skill helps an AI agent:

- turn vague UI requests into concrete design decisions
- review existing interfaces and prioritize the most important issues
- recommend practical layout, spacing, typography, color, navigation, and accessibility improvements
- explain design reasoning in plain English instead of heavy jargon
- distinguish between review-only requests, scoped implementation requests, and broader redesign requests
- work in a way that is useful for beginners without becoming overly simplistic

## Who It Is For

This skill is useful for:

- developers who want an AI assistant to give better UI and UX guidance
- beginners who need design help explained clearly
- frontend builders who want more structured design reviews
- teams who want a reusable design-oriented prompt or skill file
- people publishing agent instructions that need to work across more than one platform

## Repository Contents

- `ui-ux-architect/SKILL.md`: the main skill definition, following the [Agent Skills specification](https://agentskills.io/specification)

## Design Philosophy

This skill is built around a few practical rules:

- recommend one strong default before listing alternatives
- explain why a recommendation helps the user experience
- optimize for clarity before novelty
- load only the minimum context needed
- inspect the smallest useful surface before expanding
- avoid repeating audits, theory, or file reads without a concrete reason
- keep accessibility and ethical design as baseline quality
- preserve user control over major design decisions

The skill is written as a standard [Agent Skill](https://agentskills.io): a skill folder containing a `SKILL.md` file with YAML frontmatter (`name`, `description`, `license`) followed by the instruction body. This is the format natively supported by OpenCode, Claude Code, Codex, and other agent platforms, while the Markdown body itself still works as a plain prompt template in any tool.

## How The Skill Behaves

The skill handles three common request types differently:

### 1. Review or Audit Requests

If the user asks for a review, audit, usability check, accessibility pass, or redesign plan, the skill is expected to:

- inspect the smallest useful surface first
- state what already works
- identify the top `3` issues by impact by default
- explain why each issue matters
- recommend focused fixes
- stop at analysis unless the user explicitly asks for implementation
- end with a compact handoff memo if implementation is likely to follow in the same session

### 2. Explicit Scoped Change Requests

If the user already asked for a specific UI change such as improving spacing, hierarchy, form clarity, or accessibility in a defined area, the skill is expected to:

- treat the request as approved within that scope
- avoid asking for redundant permission
- implement or guide the requested fix directly
- avoid a broad second-pass audit before making the approved change
- avoid expanding the task into a full redesign unless necessary

### 3. Open-Ended Redesign Requests

If the user asks for a redesign without clearly defining the direction, the skill is expected to:

- recommend one strong direction
- explain why it fits the product or user need
- define the scope of change
- ask for approval before making major structural or visual changes

## Two Working Modes

The skill uses two operating modes.

### New Project Mode

Use this mode when the user has:

- a fresh idea
- a rough concept
- an empty codebase
- no settled UI direction yet

Expected output:

- goal and target user
- assumptions
- main flow
- page or screen structure
- components and design system
- visual direction
- approval needed
- implementation order

### Existing Project Mode

Use this mode when the user provides:

- an existing codebase
- a screenshot
- a mockup
- a prototype
- a live flow that needs improvement

Expected output:

- what works
- top issues
- why they matter
- recommended fixes
- accessibility concerns
- approval needed, if any
- handoff memo, when implementation may follow
- implementation plan, if changes are requested

## Low-Token Usage Patterns

The skill is standalone, but it is also written to support lower-token workflows when users apply it deliberately.

### Minimal Surface First

For existing projects, start with:

- the directly affected page or screen
- the local layout or container
- nearby components
- local styles

Expand to shared components, global styles, navigation, or design tokens only when the issue clearly points there or a blocker appears.

### Top 3 Issues Default

For audits, the skill defaults to the top `3` issues by impact unless the user asks for a broader pass. This keeps findings focused and reduces unnecessary exploration and output.

### Same-Session Handoff

If an audit is likely to be followed by implementation in the same session, end the audit with a compact handoff memo and use that memo as the source of truth for the implementation phase.

This avoids:

- repeating the full audit
- reopening already-understood files without a reason
- doing a broad second-pass review before an approved scoped fix

## Low-Token Prompt Patterns

These patterns help GitHub users get better token efficiency while still using the standalone `SKILL.md` body.

### Audit Prompt Pattern

```text
Use this UI/UX skill to audit an existing project.
Inspect only the smallest useful surface first.
Return what already works, the top 3 issues by impact, why they matter, recommended fixes, and a compact handoff memo.
Do not broaden the audit unless the evidence points there.
```

### Implementation Prompt Pattern

```text
Use this UI/UX skill to implement the approved existing-project fixes below.
Treat the listed scope as approved.
Do not repeat the prior audit or do a broad second-pass review.
Open additional files only if blocked or if the root cause clearly lies elsewhere.
```

### Same-Session Handoff Pattern

After the audit, carry forward only a compact memo like this:

```text
scope: Settings page form clarity and spacing
approved_changes: Improve field grouping, label clarity, error visibility
affected_surfaces: Settings screen, local form component, local styles
approval_status: Scoped fixes approved; no navigation redesign approved
blockers: Need to confirm whether validation copy is shared across forms
```

Then start implementation with:

```text
Use the handoff memo below as the source of truth.
Do not repeat the audit unless a blocker or new evidence appears.

scope: ...
approved_changes: ...
affected_surfaces: ...
approval_status: ...
blockers: ...
```

## Beginner-Friendly Defaults

The skill includes safe defaults for users who do not have strong design instincts yet. These defaults include:

- simple layouts that are easy to scan
- one primary goal per page or screen
- a clear primary and secondary button style
- a limited color palette
- readable body text sizes
- consistent spacing
- single-column forms with labels above inputs
- short and obvious navigation
- generous spacing before decorative extras

These defaults are meant to reduce clutter, improve readability, and make interfaces easier to build and maintain.

## Accessibility and Ethics

The skill treats accessibility and ethical design as baseline quality, not optional polish.

It explicitly checks for:

- readable text contrast
- visible keyboard focus
- usable keyboard navigation
- clear labels and form guidance
- clear error states
- adequate touch target size
- non-color-only meaning
- avoidance of dark patterns such as fake urgency or misleading defaults

## Example Prompts

You can use the skill with prompts like these:

- "Audit my dashboard UX and tell me what to fix first."
- "Clean up the spacing and hierarchy on this landing page."
- "Improve accessibility on this settings screen."
- "I am new to frontend design. Help me make this form look more professional."
- "Design a simple onboarding flow for a budgeting app."
- "Review this UI and tell me what already works before suggesting changes."
- "Make this page feel less cluttered without redesigning everything."

## How To Use This Repository

### Option 1: Install It As A Skill

Clone the repository and copy the skill folder into your agent's skills directory:

- **OpenCode**: `~/.config/opencode/skills/ui-ux-architect/` (or `.opencode/skills/ui-ux-architect/` inside a project)
- **Claude Code**: `~/.claude/skills/ui-ux-architect/`
- **Codex / other platforms**: follow your platform's skill discovery path; most scan for `SKILL.md` files with `name` and `description` frontmatter

### Option 2: Use It As A Prompt Template

Copy the body of `SKILL.md` (everything below the frontmatter) into your AI tool as a system prompt, reusable instruction block, or agent behavior file.

For lower token cost on existing-project work, pair the skill with the prompt patterns above so the model starts narrow, defaults to the top `3` issues, and uses a handoff memo between audit and implementation.

### Option 3: Use It As A Team Standard

You can also use this repository as a reference for how your team wants AI agents to handle UI and UX tasks. In that setup, the skill acts as a behavior contract rather than a direct installable package.

## Standards Compliance

This skill follows the [Agent Skills specification](https://agentskills.io/specification):

- `SKILL.md` (uppercase) with YAML frontmatter containing the required `name` and `description` fields
- `name` matches the parent directory name and uses lowercase letters and hyphens only
- `description` describes both what the skill does and when to use it, so agents can discover and activate it correctly from metadata alone
- the body stays under the recommended 500-line limit and follows progressive disclosure

## Recommended GitHub Presentation

```text
.
|-- README.md
|-- LICENSE
`-- ui-ux-architect/
    `-- SKILL.md
```

That keeps the repository easy to understand:

- `README.md` explains the purpose, usage, and install path
- `ui-ux-architect/SKILL.md` contains the actual reusable instruction set

## Suggested Future Improvements

If you want to expand the repository later, useful additions would be:

- example before-and-after prompts
- sample review outputs
- framework-specific adaptations for React, Vue, or design-heavy frontend workflows
- a `references/` folder with UI review checklists, loaded on demand for progressive disclosure
- benchmark results comparing low-token and unrestricted workflows

## Contributing

If you adapt or improve this skill, keep the core principles intact:

- stay practical
- stay clear
- keep the user in control
- avoid unnecessary jargon
- optimize for useful decisions, not abstract design theory

## License

This project is released under the MIT License. See `LICENSE` for details.
