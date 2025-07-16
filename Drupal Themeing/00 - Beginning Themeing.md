
## Disable CSS Aggregation

1. In your site, go to admin/config/development/performance
2. Under Bandwidth optimization, uncheck "Aggregate CSS files"

**Result:** This will ensure your CSS changes show up as you work.

## Twig Development Mode

1. In your site, go to admin/config/developement/settings
2. Check the checkbox for "Twig development mode"
3. Save Settings


**Result:** This will allow you to inspect your code to see hints for what twig templates you need to override to customize your theme


## Twig Debug Mode

1. In your site, go to admin/config/developement/settings
2. Check the checkbox for "Twig debug mode"
3. Save Settings

**Result:** You can now insert the dump function into a twig template:

```php
{{ dump() }}
```

This will display all available variables for that template (you should see them listed if you reload your site)


-----

## Theme YML Files

Just to show up in appearance, your theme must have:

1.  themename.info.yml
2. themename.libraries.yml

Drupal uses the term "libraries" to refer to assets such as CSS and JS which are needed by the theme. We will list those in our libraries file and we will include those CSS and JS files inside our theme directory (folder).

To demonstrate how this file structure could exist within the site's web directory:

📁 web
	📁 themes
		📁 custom
			📁 themename
				- 📄 themename.info.yml
				- 📄 themename.libraries.yml
				- 📄 style.css

(you can also place your CSS file in a subdirectory if you prefer).

### Example  📄 themename.info.yml:

```
name: themename
description: An experimental Drupal theme
type: theme
core_version_requirement: ^11
base theme: false

libraries:
  - themename/themename

regions:
  header_top: 'Header Top'
  header: 'Header'
  header_bottom: 'Header Bottom'
  content_top: 'Content Top'
  content: 'Content'
  sidebar_first: 'Left sidebar'
  sidebar_second: 'Right sidebar'
  content_bottom: 'Content Bottom'
  footer_top: 'Footer Top'
  footer: 'Footer'
  footer_bottom: 'Footer Bottom'
```


### Example 📄 themename.libraries.yml:

```
themename:
  css:
    theme:
      style.css: {}
```

If you place your CSS in a directory (folder), be sure to update the path in your libraries file to point to that location.


## Theme logo and screenshot

You can add a logo (which appears in your site's branding block) and a screenshot (which appears on the Appearance page in your site's administrative dashboard).

Screenshot suggested dimensions are 480px x 360px. Most themes display a screenshot of the theme with demo content as it might appear in a finished site. But it's perfectly fine to create a placeholder screenshot while your theme is in development.

You can store your logo and screenshot image files anywhere in your theme directory. For my demo, I created a "dist" folder with various assets I use in my theme (such as my CSS "library").

📁 themename
- 📄 themename.info.yml
- 📄 themename.libraries.yml
- 📁 dist
	- 📁 icons
	- 📁 js
	- 📁 assets
		- - 📄 logo.svg
		- - 📄 screenshot.png
	- 📄 style.css


Next, I need to edit my themename.info.yml folder to tell Drupal where these files are:

```
name: themename
description: An experimental Drupal theme
type: theme
core_version_requirement: ^11
base theme: false
logo: dist/assets/logo.svg
screenshot: dist/assets/screenshot.png

libraries:
  - themename/themename

regions:
  header_top: 'Header Top'
  header: 'Header'
  header_bottom: 'Header Bottom'
  content_top: 'Content Top'
  content: 'Content'
  sidebar_first: 'Left sidebar'
  sidebar_second: 'Right sidebar'
  content_bottom: 'Content Bottom'
  footer_top: 'Footer Top'
  footer: 'Footer'
  footer_bottom: 'Footer Bottom'
```

Next, flush your Drupal cache:

`ddev drush cr
`
And you should see the logo and screenshot in your local dev environment.