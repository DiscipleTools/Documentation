# Create Post

`POST` [https://example.com/wp-json/dt-posts/v2/{post\_type}/](https://example.com/wp-json/dt-posts/v2/{post_type}/)

Requires permission: `create_{post_type}`

## Parameters

Body params: See [Fields Format](post-types-fields-format.md)

Query params: add `?silent=true` to disable notifications

Query param: `check_for_duplicates`.  
Check for duplicates on a field before creating an new post. 
If a duplicate is found, then the existing post will be updated instead of a new one created.  
ex: `check_for_duplicates=contact_phone,contact_email`

## Returns

Will return the same content as: [Get Post](get-post.md)

