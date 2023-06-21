[< Menu](../twig-cheatsheet.md)


# Render Arrays

## Get only Renderable array items
Use case: you are working with a paragraph reference field and need to iterate through ONLY the nested paragraph items.

The easiest and best approach is to use the [Twig Tweak](https://www.drupal.org/project/twig_tweak) module. Once it's installed and enabled you can do this:

```twig
{% set renderable_buttons = content.field_buttons|children %}
```

Other options with 'vanilla' Twig features
```twig
{% for key,item in content.field_buttons if key|first != '#' %}
  // Do things with {{item}}
{% endfor %}
```

This may be better in some scenarios
```twig
      {% set renderable_slides = [] %}

      {% for item in carousel_swiper.content|keys %}
        {% if item|slice(0,1) is not same as '#' %}
          {% set renderable_slides = renderable_slides|merge([carousel_swiper.content[item]]) %}
        {% endif %}
      {% endfor %}
```

In the example above where each item in `renderable_slides` is a paragraph entity, you can now use the following to access the paragraph entity field values:

```twig
{% for item in renderable_slides %}#}
  {{ item['#paragraph'].field_text.value }}
{% endfor %}
```

Get Key value of a list field