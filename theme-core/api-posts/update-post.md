# Update Post

`Post` [https://example.com/wp-json/dt-posts/v2/{post\_type}/{post\_id}/](https://example.com/wp-json/dt-posts/v2/{post_type}/{post_id}/)

Requires permission: `update_any_{post_type}` or the record to be shared with the user.

## Parameters

Body params: See [Post Types Fields Format](post-types-fields-format.md)

Query params: add `?silent=true` to disable notifications

### do_not_overwrite_existing_fields (boolean)

When enabled, existing field values on a post will not be overwritten during update:

- **Single-value fields:** If the field already has a value, it will be preserved and not updated.
- **Multi-value fields:** Only new values that do not already exist will be added; existing values are preserved.

## Returns

Will return the same content as: [Get Post](get-post.md)

