
We will use ddev to quickly spin up a local sandbox site. Change "drupal11" to whatever you want to call your site directory.

```
mkdir drupal11 && cd drupal11
ddev config --project-type=drupal --docroot=web --php-version=8.3
ddev start
ddev composer create drupal/recommended-project:^11@alpha

ddev composer require drush/drush
ddev launch
```

The site will open automatically in your browser at http://drupal11.ddev.site
