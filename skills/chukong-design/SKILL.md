---
name: chukong-design
description: Use the Chukong Design System to design or review product interfaces with its tokens, components, motion, accessibility, and quality constraints. Load the canonical references before making visual decisions; do not invent a parallel system.
---

# Chukong Design

This is a lightweight, reference-led skill. It intentionally contains no copied
tokens, component source, fonts, or brand assets. The canonical implementation is
the private [Chukong Design System](https://github.com/chukong-creator/chukong-design-system);
this skill explains how to consult it and keep product work aligned.

## Before designing

Read the repository [reference map](https://github.com/chukong-creator/chukong-design-skill/blob/main/README.md#references),
then load the canonical files that match the task:

- `DESIGN.md` — binding contract, token hierarchy, component choices, behavior,
  content, and completion signals.
- `docs/style-brief.md` — visual personality, surfaces, type, color, and density.
- `docs/components.md` — component boundaries, states, and composition rules.
- `docs/motion.md` — functional motion, timing, and reduced-motion behavior.
- `docs/adoption.md` — how a project consumes and updates the packages.
- `packages/tokens/src` and `packages/react/src` — implementation source when
  exact token or API details are needed.

If the private reference is not available, ask the user to provide access or a
local checkout. Do not make up Chukong tokens, components, or brand rules to fill
the gap.

## Working contract

1. Establish the user, situation, primary task, important states, platform, and
   acceptance check before styling. Reuse an approved direction; ask only about
   decisions that materially change the result.
2. Use the canonical `primitive → semantic → component` token path and the real
   `@chukong-design/react` components whenever the project consumes the system.
   Do not add page-level brand hex values or a second competing token namespace.
3. Preserve the system's light/dark/high-contrast behavior, functional motion,
   visible focus, keyboard semantics, responsive layout, and recovery paths for
   loading, empty, error, disabled, permission, and retry states as relevant.
4. For a substantial direction or flow, keep a short constraint brief, preview
   the rendered surface with representative sanitized data, critique hierarchy
   before decoration, and finish with a subtraction pass. Keep internal review
   notes out of product copy.

## Precedence and boundaries

Explicit product, platform, technical, accessibility, and user decisions outrank
external inspiration. Otherwise the canonical Chukong Design System wins;
Vercel, Meta, Fluid Functionalism, and other references are inputs to explore,
not sources of truth to copy. Preserve provenance and license notes for borrowed
ideas or assets. Never put credentials, private endpoints, or personal data in
prompts, fixtures, screenshots, or commits.
