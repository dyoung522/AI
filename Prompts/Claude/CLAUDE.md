---
publish:
title: CLAUDE.md
type: Prompt
status:
date: 2026-01-07
tags:
  - AI/claude
---

# CLAUDE.md

A generic CLAUDE.md, intended primarily to be a high level instruction set used for global config.

## Primary Directives

If any directive in this document conflicts with explicit, project-specific objectives or instructions, the conflict must be called out explicitly and resolved before proceeding.

1. Plan before build. Unless otherwise specifically requested, all actionable edit or write tasks that are more than trivial should start with a Plan. Examples of "a trivial task" would include (but are not limited to) changes which do not alter behavior, such as:
    1. renaming a single variable across multiple files which does not alter behavior
    2. updating a config value which does not alter behavior
    3. adding a small helper function
2. If we're adding, modifying, or fixing functional code:
    1. Always start with a test. Bug fixes **must** begin with a failing test that reproduces the issue.
    2. Double check your results either via tests and/or running code directly to verify an expected outcome. Do not proceed to the next task until verification passes.
3. Strive to follow best programming practices, such as DRY, KISS, YAGNI, and SOLID whenever practical.
    1. Use abstraction where it meaningfully reduces complexity, not by default.
    2. Favor simplicity (KISS, YAGNI) over extensibility unless there is a clear, current need.
4. Avoid adding any additional libraries or other such dependencies unless they are clearly justified and/or required. Prefer standard library solutions where feasible.
5. If the project is versioned or user-facing
    1. Update the project's documentation (such as the README) when functional components are added, changed, or removed.
    2. Maintain a changelog in `CHANGELOG.md` summarizing major modifications to user-facing functionality.
    3. Use semantic versioning and update the version number appropriately before any new public release.
6. Actively push back on questionable architecture choices by explaining concerns and proposing a safer alternative before implementing. Wait for confirmation if the change is significant.

## Assumptions and Clarifications

If requirements are incomplete, make reasonable assumptions explicit and confirm them before implementation.

## Supplemental Files to Read

Any file named after the primary code the project is using should be read if it exists in any of the usual config locations. Supplemental files take precedence over this document when they provide more specific guidance.

For example:

- Ruby based projects should read @RUBY.md (Note: Rails projects should look for and read @RUBY.md and @RAILS.md files)
- Go (Golang) based projects should read @GO.md
- Rust should read @RUST.md
- etc.
