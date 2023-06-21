[< Menu](../twig-cheatsheet.md)

# Add a template file for a theme in a custom module
Just adding a template file to a module will not get the theme to recognize and use it. You need to also use a `hook_theme()`.

Then the hook_theme in the module looks like this:

```php
function modulename_theme() {
  return [
    'block__alert_block' => [
      'template' => 'block--alert-block',
      'base hook' => 'block'
    ],
  ];
}
```

Then add a template file in the module directory at `/templates/block--alert-block.html.twig`