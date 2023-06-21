# Translations
## Translate with token replacement variables
Strings that include variables can be translated using tokens. This is often a special case where simply using {%trans}...{%endtrans} doesn't work. Like when needing to set a variable.
```
{% set audio_title = 'Hear from @quotee_name at @quotee_organization'|t({'@quotee_name': quotee_name, '@quotee_organization': quotee_organization}) %}
```

## Translations that include variables
In most cases just use `{%trans}...{%endtrans}` and the string with variable will be available for string translation.
```twig
{%trans} 
	Hear from {{ quotee_name }} at {{ quotee_organization }}
{%endtrans}
```