UPDATED August 6, 2025

------
**VIDEO**
These instructions have a companion video which can be found here:
https://www.youtube.com/watch?v=KuapsnUBBSc&t=51s

Note: video does not have the most updated instructions. See below for a more updated guide.

------

We will use ddev to quickly spin up a local sandbox site. Change "drupal11" to whatever you want to call your site directory.

```
brew upgrade ddev
cd sites
mkdir drupal11 && cd drupal11
ddev config --project-type=drupal11 --docroot=web
ddev start
ddev composer create-project "drupal/recommended-project:^11"
ddev composer require drush/drush
ddev drush site:install --account-name=admin --account-pass=admin -y
ddev launch
```

The site will open automatically in your browser at http://drupal11.ddev.site

You will be automatically logged in to the site and sent to your user profile, where you can update your user account email, name, and password.