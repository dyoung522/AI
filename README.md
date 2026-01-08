---
publish:
title: AI Readme
type: README
status:
date: 2026-01-07
tags:
  - note
---

# AI Readme

This repository organizes AI-related resources, including prompts, project specifications, skills documentation, and custom commands for working with AI assistants like Claude.

## Repository Structure

### `/Prompts/Claude/`

Contains standardized prompt configuration files that guide Claude's behavior across different project types. These files can be placed in project directories or user home directories to provide consistent AI assistance.

- **CLAUDE.md** - Primary directive set for all Claude interactions
  - Enforces plan-before-build methodology
  - Emphasizes test-driven development
  - Promotes best practices (DRY, KISS, YAGNI, SOLID)
  - Requires explicit documentation and changelog updates

- **RUBY.md** - Ruby-specific coding standards and conventions
- **RAILS.md** - Rails framework patterns and best practices
- **WEBUI.md** - Web UI development guidelines

These files work hierarchically: project-specific configurations take precedence over global settings, allowing for customization while maintaining baseline standards.

### `/Projects/`

Contains AI-assisted project specifications and prompts for specific tasks.

Each project file includes detailed requirements, constraints, and expected outcomes to ensure consistent AI assistance across complex tasks.

### `/Skills/`

Documentation for specialized AI interaction patterns and workflows.

Skills provide reusable prompt patterns that can be adapted to different codebases and situations.

### `/Commands/`

Reserved for custom AI commands and shortcuts. Currently empty and available for future automation scripts or frequently-used prompt combinations.

## Usage

### Global Configuration

Place `CLAUDE.md` in your home directory (`~/.claude/CLAUDE.md`) to apply directives globally across all projects.

### Project-Specific Configuration

Copy relevant prompt files (e.g., `RUBY.md`, `RAILS.md`) to your project's root directory to enable language or framework-specific guidance.

### Skills Application

Reference skills documentation when you need to perform specialized analysis or follow established workflows. Copy and adapt the prompts for your specific use case.

## Philosophy

This repository embodies a structured approach to AI-assisted development:

1. **Plan before build** - Non-trivial changes require explicit planning
2. **Test-driven development** - Bug fixes start with failing tests
3. **Best practices by default** - Favor simplicity and proven patterns
4. **Explicit documentation** - Changes to functionality require documentation updates
5. **Thoughtful architecture** - Push back on questionable design choices

These principles ensure AI assistance enhances rather than complicates development workflows.
