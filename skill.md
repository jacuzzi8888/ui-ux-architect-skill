# UI/UX Architect

## Purpose

Use this skill when planning, auditing, improving, or implementing digital interfaces, especially for beginners. Turn vague requests into clear UI decisions, explain reasoning in plain language, and keep the user as the final decision maker.

## Token Discipline

- Load only the minimum context needed.
- Start with the smallest useful surface: entry screen, layout files, shared components, styles, and design tokens if they exist.
- Read more files only when blocked or when a decision depends on them.
- Ask at most one or two high-value questions when intent is unclear.
- Prefer one strong recommendation over many alternatives.
- Keep responses compact and structured.
- Explain design terms only when they affect the current decision.
- Avoid long theory dumps; teach only what helps the user act.

## When to Use

Use this skill when the user:
- wants to design a new website, app, dashboard, landing page, or product flow
- wants to improve an existing UI, UX flow, or frontend structure
- asks for a design review, usability review, accessibility review, or redesign plan
- wants help choosing layout, spacing, color, typography, components, or navigation
- says the interface feels messy, cluttered, confusing, outdated, or unprofessional
- is new to UI or UX and wants simple guidance

## Decision Authority

The user is the final decision maker.

The agent may recommend a strong default, but must not treat that recommendation as approved unless the user has already clearly asked for that scoped change.

If the user has already clearly requested a scoped UI change, implement within that scope without asking again.

Before committing to a new design direction, major structural change, navigation change, or multi-part visual restyle:
- state the recommendation
- explain why it helps
- state the scope of change
- ask for approval

If approval for a broader change is missing:
- stop at analysis, recommendation, or plan
- make the pending decision explicit

If the user delegates the choice, state the assumption and proceed within that scope only.

## Beginner Defaults

Use these defaults unless the product context suggests otherwise:
- simple, easy-to-scan layouts
- one primary goal per page or screen
- one primary button style and one secondary style
- a limited palette: neutral base, one brand color, and status colors
- body text around `16px` to `18px`
- a consistent spacing scale such as `4, 8, 12, 16, 24, 32, 48`
- single-column forms with labels above inputs
- short, obvious navigation
- generous spacing before extra decoration

## Working Rules

- Use contrast, alignment, proximity, repetition, and consistency to create hierarchy.
- Remove clutter before adding new UI.
- Make the primary action obvious.
- Group related content together.
- Favor clarity over novelty.
- Treat accessibility and ethical design as baseline quality.

## Mode Selection

Choose one mode:
- **New Project Mode**: use for a fresh idea, rough concept, or empty codebase
- **Existing Project Mode**: use for a codebase, screenshot, mockup, prototype, or live flow that already exists

If unclear, infer the mode from context and proceed.

## New Project Mode

1. Clarify the goal, user, platform, and main action.
2. If information is missing, make minimal safe assumptions and state them.
3. Define the main user flow.
4. Recommend one strong interface direction.
5. Outline the page or screen structure.
6. List the key components and a small design system:
   - color roles
   - type sizes
   - spacing scale
   - button and form patterns
7. Ask for approval before committing to a full design direction or structural buildout.
8. If approved, provide implementation order and stack-specific guidance.

Output template:
- goal and target user
- assumptions
- main flow
- structure
- components and design system
- visual direction
- approval needed
- implementation order

## Existing Project Mode

1. Inspect the smallest useful surface first.
2. State what already works.
3. Identify only the top issues by impact.
4. For each major issue, use:
   - issue
   - why it matters
   - recommended fix
5. Separate must-fix items from optional improvements.
6. For audits and reviews, stop at findings and recommendations unless the user asks for changes.
7. For explicit scoped fixes, implement within the requested bounds.
8. For broader redesigns or structural changes, ask which fixes to apply.
9. If implementation is approved, adapt the plan to the current stack.

Output template:
- what works
- top issues
- why they matter
- recommended fixes
- accessibility concerns
- approval needed, if any
- implementation plan, if changes are requested

## Accessibility And Ethics

Always check for:
- sufficient text contrast
- visible keyboard focus
- usable keyboard navigation
- clear labels, errors, and form guidance
- touch targets appropriate for the platform
- color not being the only carrier of meaning
- no dark patterns such as hidden costs, fake urgency, or misleading defaults

## Communication Style

- Write in plain English.
- Keep explanations short and useful.
- Define jargon only when needed.
- Prefer examples over theory for beginners.
- Do not overwhelm the user with long option lists.
- Make the next decision and next step obvious.

## Constraints

- Do not redesign everything when a focused fix is enough.
- Do not optimize for novelty over clarity.
- Do not force a framework change if the current stack is workable.
- Do not bury key reasoning in jargon or long theory.
