---
publish:
title: RUBY.md
type: Prompt
status:
date: 2026-01-07
tags:
  - AI/claude
---

# RUBY.md

Project-agnostic guidance for writing Ruby in this workspace.  
Project-specific instructions (PROJECT.md / repo docs) take precedence.

## Tooling and Versioning

- Prefer the latest **stable** releases of Ruby and core tooling unless a project specifies otherwise.
- Prefer modern, idiomatic Ruby features that improve clarity and reduce boilerplate.

## Style and Linting

- Prefer an opinionated formatter/linter and adhere to it consistently.
- Default to RuboCop unless the project specifies StandardRB.
  - If RuboCop is used, prefer minimal configuration and community conventions.
  - Avoid reformatting unrelated code while making changes.

### Strings

- Prefer **double quotes** by default.
- Use single quotes only when interpolation/escapes are not needed and the project explicitly prefers them.

## Design Principles

- Prioritize readability and maintainability over cleverness.
- Favor small, composable methods with clear responsibilities.
- Prefer early returns and guard clauses (“fail fast”) over nested conditionals.
- Avoid `if/else` ladders when guard clauses, polymorphism, or extracted methods make intent clearer.

## Error Handling

- Prefer **fail fast** behavior in core logic.
- Raising exceptions from models / domain logic is acceptable and often preferred.
- Handle exceptions at appropriate boundaries (service layer, controller, job runner) rather than burying rescues deep inside business logic.
- Avoid swallowing exceptions without logging/context.

## Metaprogramming

- Metaprogramming is allowed when it **meaningfully simplifies code** and improves consistency.
- Use metaprogramming to remove repetition and enforce patterns, but not at the cost of understandability.
- Prefer explicit code when metaprogramming would obscure control flow or make debugging difficult.
- If metaprogramming is used:
  - Keep it localized (one place, well-named).
  - Add YARD docs and small tests proving behavior.
  - Avoid surprising monkey patches unless clearly justified and documented.

## Testing

- Follow test-first development for functional changes (see CLAUDE.md).
- Mocking/stubbing is acceptable when practical.
- `allow_any_instance_of` is allowed when it materially reduces test complexity, but avoid it when more precise seams are easy to introduce.
- Prefer tests that clearly communicate intent over overly strict interaction tests.

## Performance

- Prefer clear code over micro-optimizations.
- Optimize only when necessary and ideally guided by measurement.
- Ruby “tricks” are acceptable when they remain readable and idiomatic.

## Concurrency

- Default assumption is single-threaded Ruby unless there is a clear performance benefit for long-running work (jobs, batch processes).
- Introduce concurrency deliberately with clear boundaries and tests.

## Documentation

- Prefer **YARD-style documentation** for public APIs, non-obvious logic, and reusable modules/classes.
- Keep README-level docs for major workflows and high-level usage; don’t duplicate everything from YARD.

## lib/ Organization

- Prefer extracting reusable functionality into focused files under `lib/`.
- Require/load `lib/` code intentionally (don’t blindly auto-require the world).
- Keep `lib/` code well-namespaced to avoid collisions.

## Default Decisions (may Be Overridden per project)

- Lint/format: RuboCop (unless project uses StandardRB)
- Strings: double quotes by default
- Exceptions: fail fast; raise in models/domain, handle at boundaries
- Metaprogramming: allowed when it increases clarity and reduces duplication
