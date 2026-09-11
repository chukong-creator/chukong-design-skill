---
name: chukong-design
description: Apply a method-first design loop to product interface work. Use it for context, visual exploration, critique, subtraction, and verification; do not impose a brand, component library, or visual palette.
---

# Chukong Design Method

This is a method-only skill. It teaches an agent how to understand a design task, explore a direction, build a rendered surface, critique it, remove unnecessary complexity, and verify the delivered path. It does not prescribe a brand, color palette, component library, or product-specific visual result.

## Scope

Use the method with the target project's existing rules, platform patterns, assets, and technical constraints. If the project has no established language, make the smallest explicit decisions needed for the task and label them as proposals. Do not treat external screenshots or model memory as product facts.

## Route only the references the task needs

Read the public [reference map](https://github.com/chukong-creator/chukong-design-skill#参考地图), then choose the smallest useful source:

| Need | First source |
| --- | --- |
| User, task, constraints, direction, hierarchy, completion | This method and the user's product context |
| Existing visual or interaction rules | The target project's source, documentation, and real implementation |
| HTML prototype, rendered preview, or browser debugging | The target project's tooling and the public workflow references, if relevant |
| Claude Design loop details or Claude Code tool mapping | Public [`ai-design-loop.md`](https://github.com/chukong-creator/chukong-design/blob/main/skills/chukong-design/references/ai-design-loop.md) and [`claude.md`](https://github.com/chukong-creator/chukong-design/blob/main/skills/chukong-design/references/claude.md) |
| Accessibility or platform behavior | The relevant platform and accessibility guidance |

External research is comparison input, never an automatic visual authority.

## The design method

For a new visual direction, important surface, high-fidelity prototype, or quality-sensitive redesign, use this loop. Skip the full loop for a small bug, token-only change, accessibility-only audit, or tightly scoped copy edit.

`Context → Discover → Define → Build → Critique → Deliver → Verify`

- **Context:** establish the user, situation, primary task, fixed constraints, open decisions, important states, platform, and acceptance check. Describe an existing identity from evidence before changing it.
- **Discover:** explore a small set of genuinely different directions (usually 2–3), each with a feeling, composition, material/type language, memorable choice, and reason it could fit. Let the user steer taste; do not make variants only to fill a catalog.
- **Define:** freeze the chosen direction into a brief with emotional intent, layout topology, roles for type/color/surface/imagery/motion, content density, one primary action, anti-references, and a stable rubric.
- **Build:** follow the target project's existing rules and real components when available; otherwise use clear layouts and accessible platform primitives. Render with representative sanitized data. Add imagery, 3D, shader, video, or other enrichment only when it communicates meaning that structure and type cannot.
- **Critique:** keep implementation and visual critique independent when possible. The critic judges the fresh rendered surface, not the code or implementation effort, and reports `what works → biggest gaps → concrete fixes in priority order → score with evidence → unverified questions`.
- **Deliver:** run a subtraction pass. Remove or simplify elements that do not improve understanding, action, trust, orientation, feedback, or the intended feeling; do not mistake decoration for polish.
- **Verify:** check the delivered browser/app path, runtime errors, responsive hierarchy, mouse/touch/keyboard behavior, focus, contrast, reduced-motion, relevant states, and the 5-second primary-message check. Static mocks and critic scores are signals, not proof of usability or production readiness.

If quality is not converging after one or two focused iterations, revisit the direction or rubric instead of accumulating micro-tweaks. Read the longer public [`ai-design-loop.md`](https://github.com/chukong-creator/chukong-design/blob/main/skills/chukong-design/references/ai-design-loop.md) and Claude Code [`claude.md`](https://github.com/chukong-creator/chukong-design/blob/main/skills/chukong-design/references/claude.md) only when their detail is needed.

## Working contract

1. Establish the user, situation, primary task, entry point, important states, platform, and acceptance check before styling. Ask only about decisions that materially change the result.
2. Preserve explicit product rules, existing components, content constraints, platform conventions, and accessibility requirements. Do not introduce a competing visual language without a clear product reason.
3. Keep one primary action per local region, make status and next steps legible, and provide recovery paths for relevant loading, empty, error, disabled, permission, and retry states.
4. For a substantial direction or flow, apply the full loop: brief, preview, critique hierarchy before decoration, subtract, then verify.
5. Keep internal review notes out of product copy. For AI output, distinguish fact, inference, recommendation, and uncertainty.

## Output contract

When delivering a design, implementation, or critique, state:

- that the Chukong design method was used;
- the product/project references actually consulted, decisions made, assumptions, and facts that remain unverified;
- the relevant states, responsive behavior, accessibility path, and motion behavior;
- what was rendered or tested, and what still needs user or product review.

Do not describe a static mock, synthetic fixture, or successful build as proof of real backend integration or user success.

## Boundaries

Preserve provenance and license notes for borrowed ideas or assets. Never put credentials, private endpoints, personal data, or unredacted customer content in prompts, fixtures, screenshots, or commits. Do not make external releases or other mutations unless the user explicitly authorizes them.
