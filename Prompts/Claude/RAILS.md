---
publish:
title: RAILS.md
type:
status:
date: 2026-01-07
tags:
---

# RAILS.md

Project-agnostic guidance for writing modern, idiomatic Ruby on Rails.  
Project-specific instructions (PROJECT.md / repo docs) take precedence.

## Rails Versioning

- Prefer the latest **stable** Rails release unless a project specifies otherwise.
- Assume modern Rails defaults (Zeitwerk, encrypted credentials, Hotwire, etc.).
- Avoid legacy patterns carried forward solely for backward compatibility.

## Overall Philosophy

- Prefer Rails conventions over custom abstractions.
- Use “The Rails Way” unless there is a clear, documented reason not to.
- Optimize for clarity, maintainability, and boring correctness over cleverness.

## Application Structure

- Controllers should be thin: orchestration and HTTP concerns only.
- Models may contain domain logic, validations, and persistence concerns.
- Extract service objects or POROs when logic:
  - does not naturally belong to a single model, or
  - coordinates multiple models or side effects.
- Avoid “god objects” regardless of layer.

## Views and UI

- Prefer server-rendered HTML as the default.
- Favor **Hotwire (Turbo + Stimulus)** for interactivity before reaching for SPA frameworks.
- Keep views simple; extract partials or components only when duplication or complexity warrants it.
- Avoid business logic in views.
- Read WEBUI.md for additional directives

## JavaScript

- Prefer Rails defaults (importmap + Hotwire) unless a project explicitly opts into a JS bundler.
- Avoid introducing frontend complexity unless it materially improves the user experience.
- Keep Stimulus controllers small, focused, and declarative.

## Background Jobs

- Use background jobs for slow, blocking, or non-user-facing work.
- Keep jobs idempotent where possible.
- Avoid embedding complex business logic directly in job classes; delegate to service objects.

## Database and Migrations

- Treat migrations as append-only once merged.
- Do not edit historical migrations.
- Prefer reversible migrations.
- Avoid database-specific behavior unless the project explicitly depends on it.

## Autoloading and Namespacing

- Follow Zeitwerk conventions strictly.
- Ensure file paths and constants align correctly.
- Avoid manual requires unless there is a specific, documented need.
- Keep namespaces shallow and meaningful.

## Testing (Rails-specific)

- Prefer request/system tests for behavior over controller tests.
- Use fixtures or factories consistently (project-specific choice).
- Avoid over-testing Rails internals.
- Test domain behavior and user-visible outcomes.

## Configuration and Secrets

- Use encrypted credentials for secrets.
- Avoid hardcoding environment-specific values.
- Keep configuration centralized and explicit.

## Generators and Defaults

- Prefer Rails generators to establish consistent structure.
- Customize generators only when the benefit is clear and documented.
- Avoid deleting generated files solely for aesthetic reasons.

## Performance

- Avoid premature optimization.
- Use Rails instrumentation and logging before guessing.
- Cache deliberately and invalidate explicitly.

## Anti-Patterns to Avoid

- Overuse of concerns for unrelated behavior.
- Excessive callbacks hiding control flow.
- Monkey-patching Rails internals without strong justification.
- Re-implementing framework features that already exist.
