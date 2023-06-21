[< Menu](../README.md)

# Links
## Get the URL from a link field
This gets the FIRST links url, often link fields are multiple, or need to be accessed by their index. 
```twig
{{ content.field_link_multiple.0['#url'] }}
```

## Get the link TITLE from a link field
```twig
{{ content.field_link_multiple.0['#title'] }}
```