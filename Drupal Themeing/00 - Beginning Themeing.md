
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

themename.info.yml
themename.libraries.yml

Any CSS or JS referenced in the libraries.yml will need to be included, as well.

