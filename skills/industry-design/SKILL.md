---
name: industry-design
description: >-
  Directs product and marketing design so the result matches the project's
  industry and goals instead of a generic modern template. Use when creating,
  redesigning, styling, or reviewing a landing page, marketing site, app
  screen, dashboard, flow, design system, hero, or faux product UI, and when
  the user mentions design, UI, UX, visual direction, conversion, or a look
  that should feel current for the industry. Researches Refero Styles first,
  then routes page structure to landing-page-design, product shots to
  stageshow, distinctiveness to frontend-design, and the ship check to
  web-design-guidelines.
---

# Industry Design

Design for this product's industry and the job the screen has to do. "Modern" is whatever strong products in that category ship now, kept only where it serves the goal. It is not a personal default, a purple SaaS kit, or a fixed font list.

This skill is the director. Companion skills are specialists. Read them before the step they own. When they disagree, [precedence.md](references/precedence.md) wins.

## Start

1. Read [precedence.md](references/precedence.md) before choosing type, color, layout, or motion.
2. If a core companion is not already available, install only the missing ones from [companions.md](references/companions.md), then read that companion's own `SKILL.md`. Do not copy companion text into this repo or into `AGENTS.md`.
3. Ask for everything that is still missing in **one message**, using [brief.md](references/brief.md). Then wait. If the invoking message already answers an item, do not ask it again. If the user says to proceed, or cannot answer, state each assumption in one line and continue.

## Decide the direction

Write this brief, then research. Do not open the editor yet.

```text
Designing [WHAT] for [WHO] on [PLATFORM].
Industry: [CATEGORY IT WILL BE JUDGED AGAINST].
Goal: [ONE PRIMARY OUTCOME].
Tone: [ONLY IF THE USER GAVE ONE; otherwise "decide from the industry"].
Main objection: [OBJECTION].
Must remember: [HOOK].
Constraints: [BRAND, STACK, PROOF YOU ACTUALLY HAVE].
Research: [styles / screens / flows].
```

Research with Refero before any visual decision:

1. Styles first. Run 3 to 5 `refero_search_styles` queries from [industry-queries.md](references/industry-queries.md): one broad aesthetic, one industry query, one goal query, and one strong product in that industry when you know one. Open 3 or 4 with `refero_get_style`.
2. Screens when the task needs a real screen's contents: dashboard, pricing, settings, empty state, form. Use `refero_search_screens`, then `refero_get_screen`.
3. Flows when the user moves through steps: onboarding, checkout, upgrade, cancel. Use `refero_search_flows`, then `refero_get_flow`.
4. Styles cover marketing and product sites, not in-app systems. For app UI, take taste from styles, then structure from screens and flows.

If `refero_search_styles` is missing, search [Refero Styles](https://styles.refero.design/) and open each chosen style's `DESIGN.md`. If you cannot reach Refero at all, ask the user once to connect `https://api.refero.design/mcp`. Do not invent a palette and call it research.

Lock one direction before building. Do not average the references.

```text
Primary reference: [one style or brand system]
Preserve: [3-5 traits: canvas, type, accent role, density, media]
Borrow only: [1-2 details, each with a role]
Role rules: [what may not leak, e.g. accent is CTA-only]
Media: [product shot / photo / diagram / placeholder, and how it is framed]
Reject: [the industry cliché and the AI default you will not use]
Tokens: [background, type, accent, radius, border, shadow — with roles]
Why this is current here: [what the references are doing now, and what this industry has moved past]
```

Name the references. Say what you adapted. Do not present the result as a copy of the source site.

An existing brand or design system in the repo replaces this lock for those tokens. Refero then guides layout, hierarchy, and imagery only.

## Build

Read the companion that owns the artifact, then build. Match depth to the task: a section tweak does not need a five-style study; a new page or a new visual language does.

| Artifact | Read first | Then |
| --- | --- | --- |
| Landing page, marketing site, pricing, campaign | `landing-page-design` | Part A in full. Part B tokens only when the lock has no type and color. Return its pre-code outline, then build section by section. |
| Hero or feature needs to show the product | `stageshow` | After the lock. Map locked tokens into the kit. Plan the story, start from the closest gold example, film, and fix before placing it. |
| App screen, dashboard, settings, component | Refero screens | Style lock for taste. `ui-ux-pro-max` only to find a pattern, never to pick a second palette. |
| Multi-step journey | Refero flows | Then the screens inside the journey. |
| Existing site that should be brought up to standard | `redesign-existing-projects` | Diagnose first. New values still come from the lock, not from a generic cleanup. |
| Real interface motion | `emil-design-eng` | Only for motion decisions. Do not also run stageshow on the same element. |
| Figma file | `figma-designer` | Same lock. Build variables and states, not a flat mock. |

Landing pages still follow `landing-page-design` Part A: one offer, one audience, one primary action, proof next to the claim it supports, no invented prices, stats, logos, or testimonials. Missing facts stay marked placeholders such as `{{price}}`.

Product shots follow stageshow's failures list: too much, wireframe, boxed, flat, bland. Simplify the words, not the structure. The page's locked look is the brief's style.

## Check

Before handoff, in this order:

1. Compare the built screen with the lock. If density, type, accent role, or media drifted toward a safer default, fix that first.
2. Run the `frontend-design` anti-slop check. A trait that appears on the locked reference because this industry still uses it can stay. A trait that appears on every AI page and not in the references goes.
3. Review the changed UI files with `web-design-guidelines`. Fetch the current guidelines and fix accessibility and interaction findings.
4. Check a 390px-wide layout: no horizontal overflow, the primary action is visible on the first screen, text stays inside controls.

For a marketing page, also complete the content and ship checks in `landing-page-design` (states, real copy, legal links, meta, alt text). Skip a check only when the artifact does not have that surface.

## Additional resources

- [brief.md](references/brief.md) — the single question batch
- [industry-queries.md](references/industry-queries.md) — how to search Refero for a category and a goal
- [precedence.md](references/precedence.md) — which skill wins a conflict
- [companions.md](references/companions.md) — install commands and the skills that stay optional
