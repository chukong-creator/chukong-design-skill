---
name: chukong-design
description: Apply the Chukong design method to product interface work. Use it for context, visual exploration, critique, subtraction, and verification; optionally pair it with Chukong Design System, another system, or no design system.
---

# Chukong Design Method

This is a method-first skill. It teaches an agent how to understand a design task, explore a direction, build a rendered surface, critique it, remove unnecessary complexity, and verify the delivered path. The Chukong Design System is an optional implementation reference, not a requirement and not the default visual style for every project.

## Separate method from system

Before making a visual or implementation claim, identify the selected design-system context:

- **Method-only (default):** apply this skill's process. Use the project's conventions, platform primitives, or an explicitly agreed visual direction. Do not assume Chukong tokens, colors, components, or brand personality.
- **Chukong system selected:** when the user chooses Chukong or the project is already bound to it, optionally read the private [`chukong-design-system`](https://github.com/chukong-creator/chukong-design-system). Treat `DESIGN.md` as its contract, `packages/tokens/src` as its token source, and `packages/react/src` as its component/API source.
- **Another system selected:** apply this method, but use the chosen system and the project's installed version as the implementation truth. Do not replace it with Chukong merely because this skill is active.
- **Chukong requested but unavailable:** continue with method-level work and label Chukong-specific decisions as unverified. Ask for access or a local checkout when exact tokens, APIs, versions, or release behavior matter; never invent them.

Do not load private Chukong references solely because this skill is installed.

## Route only the references the task needs

Read the public [reference map](https://github.com/chukong-creator/chukong-design-skill#reference-map), then choose the smallest useful source:

| Need | First source |
| --- | --- |
| User, task, constraints, direction, hierarchy, completion | This method and the user's product context |
| Exact token, component, theme, or API | The selected design system and the real consumer project |
| Chukong-specific visual or behavior rule | Chukong `DESIGN.md`, style, component, or motion reference (only when selected) |
| HTML prototype, rendered preview, design checker | Public `chukong-design` workflow, if the project uses it |
| Claude Design loop details or Claude Code tool mapping | Public `ai-design-loop.md` and `claude.md` |

External Vercel, Meta, Fluid Functionalism, and other research are comparison inputs, never an automatic visual authority.

## Chukong Design method

For a new visual direction, important surface, high-fidelity prototype, or quality-sensitive redesign, use this loop. Skip the full loop for a small bug, token-only change, accessibility-only audit, or tightly scoped copy edit.

`Context → Discover → Define → Build → Critique → Deliver → Verify`

- **Context:** establish the user, situation, primary task, fixed constraints, open decisions, important states, platform, and acceptance check. Describe an existing identity from evidence before changing it.
- **Discover:** explore a small set of genuinely different directions (usually 2–3), each with a feeling, composition, material/type language, memorable choice, and reason it could fit. Let the user steer taste; do not make variants only to fill a catalog.
- **Define:** freeze the chosen direction into a brief with emotional intent, layout topology, roles for type/color/surface/imagery/motion, content density, one primary action, anti-references, and a stable rubric.
- **Build:** use the selected design system when one exists; otherwise use project conventions or accessible platform primitives. Render with representative sanitized data. Add imagery, 3D, shader, video, or other enrichment only when it communicates meaning that structure and type cannot.
- **Critique:** keep implementation and visual critique independent when possible. The critic judges the fresh rendered surface, not the code or implementation effort, and reports `what works → biggest gaps → concrete fixes in priority order → score with evidence → unverified questions`.
- **Deliver:** run a subtraction pass. Remove or simplify elements that do not improve understanding, action, trust, orientation, feedback, or the intended feeling; do not mistake decoration for polish.
- **Verify:** check the delivered browser/app path, runtime errors, responsive hierarchy, mouse/touch/keyboard behavior, focus, contrast, reduced-motion, relevant states, and the 5-second primary-message check. Static mocks and critic scores are signals, not proof of usability or production readiness.

If quality is not converging after one or two focused iterations, revisit the direction or rubric instead of accumulating micro-tweaks. Read the longer public [`ai-design-loop.md`](https://github.com/chukong-creator/chukong-design/blob/main/skills/chukong-design/references/ai-design-loop.md) and Claude Code [`claude.md`](https://github.com/chukong-creator/chukong-design/blob/main/skills/chukong-design/references/claude.md) only when that task needs their detail.

## Working contract

1. Establish the user, situation, primary task, entry point, important states, platform, and acceptance check before styling. Ask only about decisions that materially change the result.
2. If a design system is selected, follow its `primitive → semantic → component` path and real component API. If no system is selected, use project conventions or accessible platform primitives. Never add a competing token namespace or page-level brand hex values without an explicit product decision.
3. Preserve the selected system's theme, focus, keyboard, responsive, motion, and recovery behavior; when no system exists, define the minimum behavior needed for the task.
4. For a substantial direction or flow, apply the method loop: brief, preview, critique hierarchy before decoration, subtract, then verify.
5. Keep internal review notes out of product copy. For AI output, distinguish fact, inference, recommendation, and uncertainty.

## Output contract

When delivering a design, implementation, or critique, state:

- that the Chukong design method was used and which design system was selected, if any;
- the references actually consulted, decisions made, assumptions, and facts that remain unverified;
- the relevant states, responsive behavior, accessibility path, and motion behavior;
- what was rendered or tested, and what still needs user or product review.

Do not describe a static mock, synthetic fixture, or successful build as proof of real backend integration or user success.

## Precedence and boundaries

The method governs how work is explored and verified; a selected design system governs its tokens, components, and implementation details:

1. Explicit product, platform, technical, accessibility, privacy, and user decisions.
2. The selected design system and the real consumer project version, if any.
3. An approved project visual direction.
4. The Chukong design method's process heuristics and external research.

Preserve provenance and license notes for borrowed ideas or assets. Never put credentials, private endpoints, personal data, or unredacted customer content in prompts, fixtures, screenshots, or commits. Do not make external releases or other mutations unless the user explicitly authorizes them.
