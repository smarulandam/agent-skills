---
name: dioxus
description: Practical guidance to build and debug Dioxus 0.7 web/fullstack apps. Use this skill for dx and dioxus-cli workflows, hydration issues, signals/hooks/reactivity, server functions, routing, SSR/SSG, deployment, and migration from Dioxus 0.5/0.6.
---

# Dioxus

## Overview

Build and debug Dioxus 0.7 apps with a practical focus on web and fullstack.
Route each request to targeted files under `references/0.7` and keep responses
actionable, concise, and tied to concrete docs.

## Working Defaults

- Keep the version pinned to Dioxus `0.7` unless project files show otherwise.
- Prefer web/fullstack workflows first (`router`, `server functions`, `SSR/SSG`).
- Load the smallest useful subset of docs from `references/0.7`.
- Do not restate entire docs; extract only what is needed to solve the task.

## Task Intake Checklist

Before proposing code or architecture changes, gather:

1. Target: `web`, `desktop`, or `fullstack`.
2. Versions: `dioxus`, `dioxus-router`, `dioxus-fullstack`, `dioxus-cli`.
3. Runtime mode: `dx serve`, `cargo`, `SSR`, or `SSG`.
4. Exact symptom: full error text, runtime behavior, and expected behavior.
5. Minimal reproducible snippet or file reference.

If context is missing, ask only for missing checklist items.

## Reference Selection Algorithm

1. Detect one primary category (setup, UI, state, routing, fullstack, tooling).
2. Open one index file and up to two core files for the category.
3. Expand only to direct dependencies of the current issue.
4. If there is ambiguity or version mismatch, prioritize `migration/*` and
   `guides/*` over inference.
5. Keep `beyond/*` out unless the user explicitly asks about framework internals.

## Reference Routing Map

### Setup tasks

- Start here: `references/0.7/getting_started/index.md`
- Then use: `references/0.7/tutorial/tooling.md`
- For first app flow: `references/0.7/tutorial/new_app.md`

### UI and RSX tasks

- Entry: `references/0.7/essentials/ui/index.md`
- Core files: `references/0.7/essentials/ui/rsx.md`, `references/0.7/essentials/ui/components.md`, `references/0.7/essentials/ui/styling.md`
- Rendering behavior: `references/0.7/essentials/ui/render.md`
- Dev reload issues: `references/0.7/essentials/ui/hotreload.md`

### State and reactivity tasks

- Entry: `references/0.7/essentials/basics/index.md`
- Core files: `references/0.7/essentials/basics/signals.md`, `references/0.7/essentials/basics/hooks.md`, `references/0.7/essentials/basics/effects.md`, `references/0.7/essentials/basics/resources.md`
- For larger state patterns: `references/0.7/essentials/basics/context.md`, `references/0.7/essentials/basics/hoisting.md`

### Routing tasks

- Entry: `references/0.7/essentials/router/index.md`
- Core files: `references/0.7/essentials/router/routes.md`, `references/0.7/essentials/router/navigation.md`, `references/0.7/essentials/router/layouts.md`
- For nested and advanced routing: `references/0.7/essentials/router/nested-routes.md`, `references/0.7/essentials/router/redirects.md`

### Fullstack tasks

- Entry: `references/0.7/essentials/fullstack/index.md`
- Core files: `references/0.7/essentials/fullstack/server_functions.md`, `references/0.7/essentials/fullstack/ssr.md`, `references/0.7/essentials/fullstack/static_site_generation.md`, `references/0.7/essentials/fullstack/forms.md`
- Error and response handling: `references/0.7/essentials/fullstack/errors.md`, `references/0.7/essentials/fullstack/headers.md`
- Streaming behavior: `references/0.7/essentials/fullstack/streaming.md`
- Infrastructure integration: `references/0.7/essentials/fullstack/axum.md`, `references/0.7/essentials/fullstack/middleware.md`, `references/0.7/essentials/fullstack/authentication.md`

### Tooling, deploy, and debugging

- Tooling: `references/0.7/guides/tools/index.md`, `references/0.7/guides/tools/creating.md`, `references/0.7/guides/tools/configure.md`
- Tailwind setup and workflow: `references/0.7/guides/utilities/tailwind.md`
- Platform baseline: `references/0.7/guides/platforms/web.md`
- Deploy: `references/0.7/guides/deploy/index.md`, `references/0.7/guides/deploy/config.md`, `references/0.7/tutorial/deploy.md`
- Testing/debug/perf: `references/0.7/guides/testing/index.md`, `references/0.7/guides/testing/debugging.md`, `references/0.7/guides/tips/optimizing.md`, `references/0.7/guides/tips/antipatterns.md`

## Troubleshooting Playbooks

### Hydration or SSR mismatch

- Docs: `references/0.7/essentials/fullstack/ssr.md`, `references/0.7/essentials/fullstack/streaming.md`, `references/0.7/essentials/fullstack/errors.md`
- Action: verify the rendering mode, identify non-deterministic values in the
  initial render, and align server/client output before optimizing.

### Server function or form errors

- Docs: `references/0.7/essentials/fullstack/server_functions.md`, `references/0.7/essentials/fullstack/forms.md`, `references/0.7/essentials/fullstack/errors.md`, `references/0.7/essentials/fullstack/headers.md`
- Action: confirm request/response boundaries, payload parsing, and status/error
  propagation first, then patch handler signatures and call sites.

### Nested routing, layout, or redirect issues

- Docs: `references/0.7/essentials/router/routes.md`, `references/0.7/essentials/router/layouts.md`, `references/0.7/essentials/router/redirects.md`, `references/0.7/essentials/router/navigation.md`
- Action: validate route-tree structure and layout nesting, then check redirect
  triggers and navigation transitions.

### Reactivity bugs (signals, hooks, effects, resources)

- Docs: `references/0.7/essentials/basics/signals.md`, `references/0.7/essentials/basics/reactivity.md`, `references/0.7/essentials/basics/hooks.md`, `references/0.7/essentials/basics/effects.md`, `references/0.7/essentials/basics/resources.md`
- Action: isolate tracked vs untracked state reads, verify effect dependencies,
  then simplify to a minimal reactive path before refactoring.

### Build or tooling failures (`dx`, config, deploy)

- Docs: `references/0.7/guides/tools/index.md`, `references/0.7/guides/tools/configure.md`, `references/0.7/guides/deploy/config.md`, `references/0.7/guides/testing/debugging.md`
- Action: verify CLI/version alignment and config shape first, then apply the
  smallest config/build change that produces a successful run.

## Output Contract

- Always provide: diagnosis, likely root cause, minimal fix, safer alternative,
  and validation steps.
- If context is insufficient, request only missing items from the intake checklist.
- Avoid generic advice without concrete file paths or API references.
- Prefer short, executable next steps over abstract recommendations.

## Migration Guardrail

- If project targets Dioxus `0.5` or `0.6`, read migration docs first:
- `references/0.7/migration/to_07.md`
- `references/0.7/migration/to_06.md`
- `references/0.7/migration/to_05/index.md`
- Do not suggest 0.7-only APIs before migration blockers are resolved.
- After migration guidance, continue with 0.7 essentials and guides.

## Out of Scope by Default

- `references/0.7/beyond/*` for governance/contributing/project internals.
- Deep custom renderer internals unless user explicitly asks for renderer work.

## Maintenance Policy

- Keep this skill pinned to Dioxus `0.7`.
- When docs are updated, refresh the routing map and troubleshooting playbooks first.
- Run `quick_validate.py` on each iteration.
- Packaging recommendation: avoid shipping `.venv` and `.DS_Store`
  inside the skill folder.

## Licensing and Source Provenance

- SPDX policy for this skill package: `MIT OR Apache-2.0`.
- Markdown files in `references/0.7` come from or are adapted from the
  official Dioxus documentation project (`DioxusLabs/docsite`) and are not
  original work from this skill.
- Upstream documentation licensing is preserved as dual-license
  `MIT OR Apache-2.0`.
- New original content added to this skill in v1 is intentionally licensed as
  `MIT OR Apache-2.0` for compatibility with upstream docs.
- See `references/0.7/UPSTREAM_ATTRIBUTION.md`, `LICENSE-MIT`, and
  `LICENSE-APACHE` for source and license details.
