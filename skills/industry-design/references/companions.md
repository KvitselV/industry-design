# Companions

Install a missing skill into the project you are designing, not into this skill repo. If that skill is already on the agent's skill list, skip the install and read its `SKILL.md`.

Core skills are required for the matching step in the director workflow. Optional skills are installed only when the task needs that lane. Do not install the whole optional list "to be safe."

## Core

```bash
npx skills add benjitaylor/skills --skill stageshow
npx skills add elayadesign/ai-design-skills --skill landing-page-design
npx skills add https://github.com/referodesign/refero_skill --skill refero-design
npx skills add anthropics/skills --skill frontend-design
npx skills add vercel-labs/agent-skills --skill web-design-guidelines
```

Add `-y` to skip confirmations. Add `-a cursor`, `-a claude-code`, or `-a codex` when the installer would otherwise ask which agent.

| Skill | Owns |
| --- | --- |
| `refero-design` | Research order, reference lock, styles then screens then flows. Live tools need Refero MCP at `https://api.refero.design/mcp`. The style library is [styles.refero.design](https://styles.refero.design/). |
| `landing-page-design` | Offer, page structure, conversion copy, SEO, and the fallback visual system. |
| `stageshow` | Faux product UI: stills, heroes, feature cards, cursor demos. React and the kit in that skill. |
| `frontend-design` | Distinctiveness. Ground the work in the subject. Reject a layout that could belong to any company. |
| `web-design-guidelines` | Pre-ship review. Fetch `https://raw.githubusercontent.com/vercel-labs/web-interface-guidelines/main/command.md` and report `file:line` findings. |

### Claude Code

For `landing-page-design`, this is the install and use instruction, verbatim:

«Установи скилл `landing-page-design` из репозитория `elayadesign/ai-design-skills` на GitHub в `.claude/skills` этого проекта, а затем используй его для создания лендинга. Перед началом задай мне все вопросы одним сообщением».

Install the other core skills into `.claude/skills/<skill-name>/` the same way: the skill folder, with its `references/` beside `SKILL.md`. `stageshow` includes `kit/`, `examples/`, and `scripts/`; copy the whole skill folder or the kit will not resolve.

### Codex

Prefer the skills CLI with `-a codex`, which keeps each skill's folder intact.

When the client wants `landing-page-design` inline instead, use this instruction verbatim:

«добавь содержимое его `SKILL.md` в `AGENTS.md`»

Do that only for Codex, and only for that skill. Leave `stageshow` and `refero-design` as folders so their reference files remain one level beside `SKILL.md`.

## Optional

Install the one that matches the task.

| When | Command |
| --- | --- |
| An existing site needs diagnosis before a redesign | `npx skills add elayadesign/redesign-skill --skill redesign-existing-projects` |
| Motion inside the real interface, not a faux demo | `npx skills add emilkowalski/skills --skill emil-design-eng` |
| A complex app pattern, after the visual lock exists | `npx skills add nextlevelbuilder/ui-ux-pro-max-skill --skill ui-ux-pro-max` |
| A last craft pass that must keep the lock | `npx skills add pbakaus/impeccable --skill impeccable` then `--skill polish` |
| A ranked review across accessibility, layout, writing, type, and color | `npx skills add jakubkrehel/skills --skill better-interface` |
| The deliverable is a Figma file | `npx skills add elayadesign/ai-design-skills --skill figma-designer` |
| Native interface principles, including iOS | `npx skills add emilkowalski/skills --skill apple-design` |
| Mobile web that should feel native | `npx skills add emilkowalski/skills --skill mobile-native` |

`ui-ux-pro-max` is a catalog of styles, palettes, and UX rules. Use it to find a pattern. Do not let it replace the Refero lock.

`polish` keeps the current look; it is not a new direction. It expects the `impeccable` skill in the same project. Do not install `pbakaus/impeccable`'s `frontend-design`: that copy is a deprecated alias and collides with Anthropic's `frontend-design`.

`sleek-design-mobile-apps` (`sleekdotdesign/agent-skills`) is a paid Sleek API client and needs `SLEEK_API_KEY`. It does not teach interface judgment. For native craft, use `apple-design`.

## Checked and left out of the core

These improve adjacent work. They are not a second design director.

| Skill | Why it stays out of the core |
| --- | --- |
| `design-taste-frontend`, `high-end-visual-design` | `landing-page-design` already adapted taste-skill. A third taste system fights the lock. |
| `canvas-design` | For canvas artifacts, not a product interface. |
| `vercel-composition-patterns` | React composition, not visual or UX judgment. |
| `vercel-react-best-practices` | Rendering performance. Use it when the page is slow, not when choosing a direction. |
| `extract-design-system` | Useful only to read tokens out of an existing codebase before you lock anything new. |
| `impeccable` skills other than a single final pass (`bolder`, `quieter`, `delight`, `distill`, `critique`) | They push the same screen in opposite directions. Pick one pass if the lock is already met and something still feels unfinished. |

## Refero MCP

The style library is the source of what is current. The skill `refero-design` is how to use it without copying one site.

Cursor project config:

```json
{
  "mcpServers": {
    "refero": {
      "url": "https://api.refero.design/mcp"
    }
  }
}
```

Sign in when the client asks. The server is read-only research. If it is not connected, use the website and each style's `DESIGN.md`, and say that the research was manual.
