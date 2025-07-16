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

### do_not_overwrite_existing_fields (boolean, default: true)

When enabled (default), existing field values on a post will not be overwritten during creation:

- **Single-value fields:** If the field already has a value, it will be preserved and not updated.
- **Multi-value fields:** Only new values that do not already exist will be added; existing values are preserved.
- **Field format:** For multi-value fields (such as tags, multi_select, user_select, connection, location, location_meta, communication_channel), both direct array format (`[['value' => 'xxx']]`) and wrapped format (`['values' => [['value' => 'xxx']]]`) are accepted, but the API will always return the wrapped format for consistency.

To override this behavior and allow fields to be overwritten, set `do_not_overwrite_existing_fields` to `false` in the request body.

**Note:** This setting may prevent some direct manual record field updates if the field already contains a value.

## Returns

Will return the same content as: [Get Post](get-post.md)

