# Precedence

Use this order when two instructions disagree. The higher one wins.

1. **The user's explicit request** in this conversation, including an approved reference lock they already accepted.
2. **The project's existing brand or design system.** Tokens, components, and voice already in the repo stay. Use research to improve hierarchy, states, and imagery. Do not reskin a product that already has a system unless the user asked for a new direction.
3. **The Refero reference lock** from this skill. One primary style. Secondary sources lend a detail, not a second personality.
4. **The specialist skill for this artifact**, read in full for that step:
   - marketing structure, offer, and copy: `landing-page-design` Part A
   - faux product stills and cursor demos: `stageshow`
   - real product motion: `emil-design-eng`
   - an existing site's generic patterns: `redesign-existing-projects`
5. **Craft fallback.** `landing-page-design` Part B (approved fonts, the fixed dark palette, no background gradients, named text styles, the spacing table) applies only when items 2 and 3 produced no type and no color. It is a closed system for an undesigned page, not the look of every industry.
6. **Review skills never direct the look.** `frontend-design` checks whether the result could be swapped onto another company. `web-design-guidelines` checks accessibility and interaction. `ui-ux-pro-max` names patterns. If one of them proposes a font, palette, or mood that fights the lock, ignore that proposal.

## Overrides of companion self-rules

Companion files tell the agent they outrank other skills. While this skill is in use, they outrank each other only as the table above says.

- `refero-design` is the research method. It does not forbid `frontend-design` or `landing-page-design`. Those run after the lock, in their lane.
- `landing-page-design` Part A applies to marketing pages even when a Refero style replaced Part B.
- The tagline-reveal section is required only when it fits the locked direction. A quiet product-led page does not grow a full-viewport word animation just because a fallback rule says so. If you omit it, say why in one line.
- Italics, serif type, and background imagery are allowed when the locked style uses them for a defined role. The Part B bans on italics, Inter, and background gradients bind the fallback system, not a locked editorial or photographic style.
- Do not import Inter, Roboto, Arial, Open Sans, or a default purple gradient as a convenience. Pick the lock's faces, or the Part B faces when there is no lock.
- `stageshow` kit defaults (light, accent, standard fidelity) give way to the lock. Framing, restraint, and "every motion has a cause" still hold.
- `frontend-design` cluster warnings (cream and terracotta, acid green on black, newspaper hairlines, identical rounded cards) are warnings. Keep the trait only when the chosen references in this industry actually use it, and say so in the lock.
- Never invent proof. No placeholder Latin, no shared stock face used twice, no banned filler ("revolutionize", "seamless", "next-generation", "supercharge"). Specific beats vague.

## What "current" means

Current is a claim about the references, not about the calendar.

After reading styles, answer four lines:

- What the stronger references in this industry are doing now.
- What they have dropped.
- Which of those moves serves this page's goal.
- Which move you will not borrow, because it belongs to a different category or fights the goal.

A fintech page can be dense and proof-heavy. A studio site can be sparse and photographic. A developer tool can lead with the product. Applying one of those looks to the others is a miss even when each look is fashionable somewhere.
