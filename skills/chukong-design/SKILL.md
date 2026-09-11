---
name: chukong-design
description: Guide design, implementation, and review of product interfaces with the Chukong Design System. Use for Chukong visual direction, components, states, motion, accessibility, and system adoption; do not invent exact rules when the canonical reference is unavailable.
---

# Chukong Design

Use this skill as a public, reference-led adapter for the Chukong Design System. It helps an agent make consistent design decisions; it is not a runtime component library and contains no copied tokens, component source, fonts, or brand assets.

## Choose the access mode

Before making a precise visual or implementation claim, identify the strongest reference available:

- **Full reference** — the private [`chukong-design-system`](https://github.com/chukong-creator/chukong-design-system) is readable. Treat `DESIGN.md` as the contract, `packages/tokens/src` as the token source, and `packages/react/src` as the component behavior/API source.
- **Consumer project** — the product already contains `@chukong-design/react` or local Chukong token/component docs. Inspect the installed version and real project usage first; project code is the implementation truth for that version.
- **Public guidance** — the private reference is unavailable. Use the public [reference map](https://github.com/chukong-creator/chukong-design-skill#reference-map) and the user’s supplied project context for direction, but label canonical status as unverified. Ask for access or a local checkout when exact tokens, APIs, versions, or release behavior matter.

Never fill an access gap by inventing Chukong hex values, component APIs, or brand rules.

## Route the task to the smallest useful reference

Read the repository [reference map](https://github.com/chukong-creator/chukong-design-skill#reference-map), then load only what the task needs:

| Task | First reference |
| --- | --- |
| Overall direction, hierarchy, completion criteria | `DESIGN.md` |
| Color, surfaces, type, density, visual personality | `docs/style-brief.md` |
| Component choice, composition, states, errors | `docs/components.md` |
| Timing, continuity, reduced-motion | `docs/motion.md` |
| Integration, upgrade, migration | `docs/adoption.md` |
| Exact token or React API | `packages/tokens/src`, then `packages/react/src` |
| HTML prototype, rendered preview, AI design loop | public `chukong-design` workflow references |

Vercel, Meta, Fluid Functionalism and other listed research are inspiration and comparison inputs, never the source of Chukong truth.

## Claude Design method

For a new visual direction, important surface, high-fidelity prototype, or quality-sensitive redesign, use this loop. Do not force it onto a small bug, token-only change, accessibility-only audit, or tightly scoped copy edit.

`Context → Discover → Define → Build → Critique → Deliver → Verify`

- **Context:** establish the user, situation, primary task, fixed constraints, open decisions, important states, and acceptance check. Describe an existing identity from evidence before changing it.
- **Discover:** explore a small set of genuinely different directions (usually 2–3), each with a feeling, composition, material/type language, memorable choice, and reason it could fit. Let the user steer taste; do not create variants only to fill a catalog.
- **Define:** freeze the chosen direction into a brief with emotional intent, layout topology, roles for type/color/surface/imagery/motion, content density, one primary action, anti-references, and a stable rubric.
- **Build:** use the real Chukong components/tokens when available and render with representative sanitized data. Add imagery, 3D, shader, video, or other enrichment only when it communicates meaning that structure and type cannot.
- **Critique:** keep implementation and visual critique independent when possible. The critic judges the fresh rendered surface, not the code or implementation effort, and reports `what works → biggest gaps → concrete fixes in priority order → score with evidence → unverified questions`.
- **Deliver:** run a subtraction pass. Remove or simplify elements that do not improve understanding, action, trust, orientation, feedback, or the intended feeling; do not mistake decoration for polish.
- **Verify:** check the delivered browser/app path, runtime errors, responsive hierarchy, mouse/touch/keyboard behavior, focus, contrast, reduced-motion, relevant states, and the 5-second primary-message check. Static mocks and critic scores are signals, not proof of usability or production readiness.

If quality is not converging after one or two focused iterations, revisit the direction or rubric instead of accumulating micro-tweaks. For the longer source and Claude Code tool mapping, read the public workflow's [`ai-design-loop.md`](https://github.com/chukong-creator/chukong-design/blob/main/references/ai-design-loop.md) and [`claude.md`](https://github.com/chukong-creator/chukong-design/blob/main/references/claude.md) only when that task needs them.

## Working contract

1. Establish the user, situation, primary task, entry point, important states, platform, and acceptance check before styling. Ask only about decisions that materially change the result.
2. Prefer the canonical `primitive → semantic → component` token path and real `@chukong-design/react` components when the project consumes them. Do not add page-level brand hex values or a competing token namespace.
3. Preserve light/dark/high-contrast behavior, visible focus, keyboard semantics, responsive layout, and recovery paths for loading, empty, error, disabled, permission, and retry states as relevant.
4. For a substantial direction or flow, apply the Claude Design loop above: make a short constraint brief, preview the rendered surface with representative sanitized data, critique hierarchy before decoration, and finish with a subtraction pass.
5. Keep internal review notes out of product copy. For AI output, distinguish fact, inference, recommendation, and uncertainty.

## Output contract

When delivering a design, implementation, or critique, make the result inspectable by stating:

- the access mode used and references actually consulted;
- the decisions made, assumptions, and canonical facts that remain unverified;
- the relevant states, responsive behavior, accessibility path, and motion behavior;
- what was rendered or tested, and what still needs user or product review.

Do not describe a static mock, synthetic fixture, or successful build as proof of real backend integration or user success.

## Precedence and boundaries

1. Explicit product, platform, technical, accessibility, privacy, and user decisions.
2. The canonical Chukong Design System and the real consumer project version.
3. An approved project visual direction.
4. External research and screenshots.

Preserve provenance and license notes for borrowed ideas or assets. Never put credentials, private endpoints, personal data, or unredacted customer content in prompts, fixtures, screenshots, or commits. Do not make external releases or other mutations unless the user explicitly authorizes them.
