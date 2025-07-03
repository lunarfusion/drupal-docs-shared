
https://www.drupal.org/project/ui_suite
https://www.drupal.org/project/ui_patterns


## Install UI Patterns
ddev composer require 'drupal/ui_patterns:^2.0'

Enable
ddev drush pm-enable ui_patterns


## Install UI Icons
ddev composer require 'drupal/ui_icons:^1.1@beta'

Enable
ddev drush pm-enable ui_icons


## Install UI Patterns and UI Icons in one package
ddev composer require 'drupal/ui_suite:^2.0.0'


## SDC Devel
ddev composer require 'drupal/sdc_devel:^1.0'

(provides error reports at /admin/reports/ui-components)