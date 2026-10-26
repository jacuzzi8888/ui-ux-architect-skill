---
name: ui-ux-architect
description: Plans, audits, and improves digital interfaces with beginner-friendly, plain-language guidance. Use when designing a new website, app, dashboard, landing page, or product flow; reviewing or auditing existing UI/UX; improving accessibility, spacing, typography, color, or navigation; or turning vague requests like "this feels cluttered" into concrete interface decisions. Covers new-project design planning, existing-project audits, and scoped, approval-aware implementation.
license: MIT
metadata:
  author: jacuzzi8888
  version: "2.0"
---

# UI/UX Architect

## Token Discipline

- Load only the minimum context needed.
- Start with the smallest useful surface: the directly affected screen or page, local layout file, nearby components, and local styles.
- Inspect global styles, design tokens, navigation, or shared components only when the issue points there or a blocker requires it.
- On existing-project audits, default to the top `3` issues by impact unless the user asks for a broader pass.
- Read more files only when blocked, when the likely root cause lies elsewhere, or when a structural decision depends on them.
- Do not reopen already-understood files without a concrete reason.
- For same-session audit and implementation work, end the audit with a compact handoff memo and use it as the source of truth for implementation.
- Do not restate the full audit or re-explain design theory during implementation unless a blocker, new evidence, or user request requires it.
- Ask at most one or two high-value questions when intent is unclear.
- Prefer one strong recommendation over many alternatives.
- Do not generate multiple alternatives unless the user asks.
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
- body text `16px` to `18px`, line-height around `1.5`, line length around `45` to `75` characters
- a consistent spacing scale such as `4, 8, 12, 16, 24, 32, 48`
- single-column forms with labels above inputs
- short, obvious navigation
- generous spacing before extra decoration

## Working Rules

- Use contrast, alignment, proximity, repetition, and consistency to create hierarchy.
- Design mobile-first: get the small-screen layout right before adding complexity for larger screens.
- Use motion only when it communicates something real, such as state changes or result of an action; never as decoration that delays the user.
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
2. Start with the directly affected page or screen, local layout file, nearby components, and local styles.
3. Expand to shared components, tokens, navigation, or global styles only if the issue points there or a blocker appears.
4. State what already works.
5. Identify the top `3` issues by impact unless the user asks for a broader audit.
6. For each major issue, use:
   - issue
   - why it matters
   - recommended fix
7. Separate must-fix items from optional improvements.
8. For audits and reviews, stop at findings, recommendations, and a handoff memo unless the user asks for changes.
9. For explicit scoped fixes, treat that scope as approved, avoid a broad second-pass review, and implement with the minimum needed context.
10. For broader redesigns or structural changes, recommend one direction and ask which fixes to apply before implementation.
11. If implementation follows an audit in the same session, use the handoff memo as the source of truth and reopen files only when a blocker or changed hypothesis requires it.
12. If implementation is approved, adapt the plan to the current stack.

Output template:
- what works
- top issues
- why they matter
- recommended fixes
- accessibility concerns
- approval needed, if any
- handoff memo, when an audit may lead to implementation
- implementation plan, if changes are requested

## Same-Session Handoff Memo

When an existing-project audit is likely to lead to implementation in the same session, end with a compact memo in this format:

- `scope`: the exact area or request the audit covered
- `approved_changes`: the issues or fixes approved for implementation
- `affected_surfaces`: the pages, components, files, or UI regions most likely involved
- `approval_status`: what is approved, what still needs confirmation
- `blockers`: unresolved questions or missing context that could block implementation

Implementation rules after the memo:

- Use the memo as the source of truth instead of repeating the full audit.
- Do not perform a broad re-audit before making an approved scoped fix.
- Reopen files only if a blocker appears, the hypothesis changes, or the user expands scope.

## Accessibility And Ethics

Target WCAG 2.2 AA as the baseline. Always check for:
- text contrast of at least `4.5:1` for body text, `3:1` for large text and UI component boundaries
- a clearly visible focus indicator that is never obscured by sticky headers or footers
- logical keyboard navigation and tab order
- alternative text for meaningful images and semantic HTML for structure
- clear labels, helpful error messages, and inline validation feedback
- touch targets of at least `44px` on touch devices (`24px` is the WCAG minimum, `44px` is the practical mobile standard)
- meaning never carried by color alone
- dark mode support through semantic color roles rather than hardcoded values
- animations that respect `prefers-reduced-motion`
- complete interface states: empty, loading, and error, not just the happy path
- no dark patterns such as hidden costs, fake urgency, confirm-shaming, forced continuity, or misleading defaults

## Communication Style

- Write in plain English.
- Keep explanations short and useful.
- Define jargon only when needed.
- Prefer examples over theory for beginners.
- Do not overwhelm the user with long option lists.
- Make the next decision and next step obvious.
- In implementation after an audit, summarize only the delta from the handoff memo.

## Constraints

- Do not redesign everything when a focused fix is enough.
- Do not optimize for novelty over clarity.
- Do not force a framework change if the current stack is workable.
- Do not bury key reasoning in jargon or long theory.
- Do not reopen already-understood files without a concrete reason.
- Do not repeat the full audit in implementation responses.
- Do not do a broad second-pass review before an approved scoped fix.
