# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

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
