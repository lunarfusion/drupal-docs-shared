
Check Drupal.org for the correct versions for your Drupal setup.

## UI Suite (full module collection)
https://www.drupal.org/project/ui_suite

## UI Patterns
https://www.drupal.org/project/ui_patterns

**Install UI Patterns**
`ddev composer require 'drupal/ui_patterns:^2.0'`

**Enable the module**
`ddev drush pm-enable ui_patterns`

## UI Icons
https://www.drupal.org/project/ui_icons

**Install UI Icons**
`ddev composer require 'drupal/ui_icons:^1.1@beta'`

**Enable the module**
`ddev drush pm-enable ui_icons`

## Install UI Patterns and UI Icons in one package
`ddev composer require 'drupal/ui_suite:^2.0.0'`

--------
## SDC Devel
Provides error reports available in Reports > UI Components

`ddev composer require 'drupal/sdc_devel:^1.0'`
