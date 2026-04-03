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

- `skill.md`: the main portable skill definition

## Design Philosophy

This skill is built around a few practical rules:

- recommend one strong default before listing alternatives
- explain why a recommendation helps the user experience
- optimize for clarity before novelty
- load only the minimum context needed
- keep accessibility and ethical design as baseline quality
- preserve user control over major design decisions

The skill is intentionally written as a body-only Markdown document rather than a platform-specific package. That makes it easier to adapt to different AI systems, prompt runners, or custom agent frameworks.

## How The Skill Behaves

The skill handles three common request types differently:

### 1. Review or Audit Requests

If the user asks for a review, audit, usability check, accessibility pass, or redesign plan, the skill is expected to:

- inspect the smallest useful surface first
- state what already works
- identify the top issues by impact
- explain why each issue matters
- recommend focused fixes
- stop at analysis unless the user explicitly asks for implementation

### 2. Explicit Scoped Change Requests

If the user already asked for a specific UI change such as improving spacing, hierarchy, form clarity, or accessibility in a defined area, the skill is expected to:

- treat the request as approved within that scope
- avoid asking for redundant permission
- implement or guide the requested fix directly
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
- implementation plan, if changes are requested

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

### Option 1: Use It As A Prompt Template

Copy the contents of `skill.md` into your AI tool as a system prompt, reusable instruction block, or agent behavior file.

### Option 2: Adapt It To A Platform-Specific Skill Format

If your agent framework expects metadata, manifests, or frontmatter, wrap `skill.md` with whatever your platform requires.

Examples:

- add YAML frontmatter for systems that use `name` and `description`
- rename the file to `SKILL.md` if your tool expects that convention
- place it inside a skill folder if your agent framework uses folder-based discovery
- add platform-specific metadata files only if that tool actually needs them

### Option 3: Use It As A Team Standard

You can also use this repository as a reference for how your team wants AI agents to handle UI and UX tasks. In that setup, the skill acts as a behavior contract rather than a direct installable package.

## Why There Is No YAML Frontmatter

This repository keeps the skill body-only on purpose.

Some agent systems require YAML frontmatter or a specific manifest format, but others do not. Keeping the file portable makes it easier for people to adapt the skill to their own environment instead of forcing one ecosystem's packaging rules onto everyone else.

If you want a Codex-specific version later, you can add frontmatter and any required metadata in a separate variant without changing the core instruction body.

## Recommended GitHub Presentation

If you publish this repository for others to use, a simple structure is enough:

```text
.
|-- README.md
`-- skill.md
```

That keeps the repository easy to understand:

- `README.md` explains the purpose, usage, and adaptation path
- `skill.md` contains the actual reusable instruction set

## Suggested Future Improvements

If you want to expand the repository later, useful additions would be:

- a Codex-ready variant with frontmatter
- example before-and-after prompts
- sample review outputs
- framework-specific adaptations for React, Vue, or design-heavy frontend workflows
- a companion reference file with UI review checklists

## Contributing

If you adapt or improve this skill, keep the core principles intact:

- stay practical
- stay clear
- keep the user in control
- avoid unnecessary jargon
- optimize for useful decisions, not abstract design theory

## License

Add the license of your choice before publishing to GitHub so other people know how they can reuse or modify the skill.
