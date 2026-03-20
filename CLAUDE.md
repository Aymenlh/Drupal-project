# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Workflow Orchestration

### 1. Plan Mode Default
- Enter plan mode for ANY non-trivial task (3+ steps or architectural decisions)
- If something goes sideways, STOP and re-plan immediately
- Use plan mode for verification steps, not just building
- Write detailed specs upfront to reduce ambiguity

### 2. Subagent Strategy
- Use subagents liberally to keep main context window clean
- Offload research, exploration, and parallel analysis to subagents
- For complex problems, throw more compute at it via subagents
- One task per subagent for focused execution

### 3. Self-Improvement Loop
- After ANY correction from the user: update `tasks/lessons.md` with the pattern
- Write rules for yourself that prevent the same mistake
- Ruthlessly iterate on these lessons until mistake rate drops
- Review lessons at session start for relevant project

### 4. Verification Before Done
- Never mark a task complete without proving it works
- Diff behavior between main and your changes when relevant
- Ask yourself: "Would a staff engineer approve this?"
- Run tests, check logs, demonstrate correctness

### 5. Demand Elegance (Balanced)
- For non-trivial changes: pause and ask "is there a more elegant way?"
- If a fix feels hacky: "Knowing everything I know now, implement the elegant solution"
- Skip this for simple, obvious fixes — don't over-engineer
- Challenge your own work before presenting it

### 6. Autonomous Bug Fixing
- When given a bug report: just fix it. Don't ask for hand-holding
- Point at logs, errors, failing tests — then resolve them
- Zero context switching required from the user
- Go fix failing CI tests without being told how

## Task Management

1. **Plan First**: Write plan to `tasks/todo.md` with checkable items
2. **Verify Plan**: Check in before starting implementation
3. **Track Progress**: Mark items complete as you go
4. **Explain Changes**: High-level summary at each step
5. **Document Results**: Add review section to `tasks/todo.md`
6. **Capture Lessons**: Update `tasks/lessons.md` after corrections

## Core Principles

- **Simplicity First**: Make every change as simple as possible. Impact minimal code.
- **No Laziness**: Find root causes. No temporary fixes. Senior developer standards.
- **Minimal Impact**: Only touch what's necessary. No side effects with new bugs.

## Project Status

This is a new/empty Drupal project repository. Update this file as the project structure is established.

## Common Commands

Once the project is scaffolded (e.g., via `composer create-project drupal/recommended-project`), typical commands include:

```bash
# Install PHP dependencies
composer install

# Run Drupal coding standards check
./vendor/bin/phpcs --standard=Drupal,DrupalPractice web/modules/custom web/themes/custom

# Auto-fix coding standards
./vendor/bin/phpcbf --standard=Drupal,DrupalPractice web/modules/custom web/themes/custom

# Run PHPUnit tests
./vendor/bin/phpunit -c web/core/phpunit.xml.dist web/modules/custom

# Run a single test class
./vendor/bin/phpunit -c web/core/phpunit.xml.dist path/to/TestClass.php

# Export configuration
drush config:export

# Import configuration
drush config:import

# Clear caches
drush cache:rebuild
```

## Architecture Notes

Update this section once the project structure is defined. Typical Drupal project structure:

- `web/` — Drupal webroot
- `web/modules/custom/` — Custom modules
- `web/themes/custom/` — Custom themes
- `web/sites/default/` — Site configuration and settings
- `config/sync/` — Exported Drupal configuration (YAML)
- `composer.json` — PHP dependency management
