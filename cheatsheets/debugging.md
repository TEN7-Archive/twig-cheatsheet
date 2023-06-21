[< Menu](../README.md)

# Debugging
## How to dump and debug variable output in Twig.

Install [Twig Tweak](https://www.drupal.org/project/twig_tweak) module and then dump variables with:

```Twig
{{ dd(variable_name) }}
```

Without a contrib module you can dump ALL variables with:

```Twig
<script>console.log({{ _context | json_encode | raw }});</script>
```