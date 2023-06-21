# Media

## Get the url of a media image referenced on a node
Ex. 1 - A node contains a field referencing a media image
```
node.field_blog_author.entity.field_media_image.entity.uri.value
```

Ex. 2 A
```
node.field_blog_author.entity.field_image.entity.field_media_image.entity.uri.value
```

Break this apart:
- `...field_blog_author.entity...` the field on the node references another node type, get the node entity referenced in that field
- `...field_image.entity...` the referenced node has a media field on it, get that media entity
- `...field_media_image.entity...` The media entity has an image field on it, get that image file entity
- `...uri.value` Get the fileuri of that image file entity

### an alternative equivalent

```
node.field_blog_author.entity.field_image.entity.field_media_image.entity.fileuri
```
The only difference here is that we use the `fileuri` method to return the uri from the image file object.

---

## URL to a file from URI
Use the `file_url` method
Ex 1 - 
- first find the image file URL, on a node that may look like this
	- `node.field_of_the_image.entity.field_media_image.entity.uri.value`
- then pass it to the `file_url`
	- `file_url(node.field_of_the_image.entity.field_media_image.entity.uri.value)`

---

## ALT text of a media image
The ALT text field is included with the image file field. You can retrieve the image field alt text from the field itself.
`node.field_of_the_image.entity.field_media_image.alt`
1. Get the media entity
2. Get the image field on the media entity
3. Get the alt text value

--- 

## Render an image through an image style
If you remember that everything is a render array, then we just need to create a render array for the 'image_style' theme function. 

Example from a node template, but can be used anywhere as long as you have the URI of a Drupal managed image:


```twig

{%  
 set styled_image = {  
 '#theme': 'image_style',  
 '#style_name': 'medium',  
 '#uri': node.field_image.entity.field_media_image.entity.uri.value,  
 '#attributes': {'alt': 'This is a photo of XYZ'}  
}  
%}
```



### Using a Responsive Image Style
 ```twig

{%  
 set styled_image = {  
 '#theme': 'responsive_image',  
 '#responsive_image_style_id': 'my_custom_responsive_style',
 '#uri': node.field_image.entity.field_media_image.entity.uri.value,  
 '#attributes': {'alt': 'This is a photo of XYZ'}  
}  
%}
```