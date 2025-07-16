# Update Post

`Post` [https://example.com/wp-json/dt-posts/v2/{post\_type}/{post\_id}/](https://example.com/wp-json/dt-posts/v2/{post_type}/{post_id}/)

Requires permission: `update_any_{post_type}` or the record to be shared with the user.

## Parameters

Body params: See [Post Types Fields Format](post-types-fields-format.md)

Query params: add `?silent=true` to disable notifications

### do_not_overwrite_existing_fields (boolean, default: true)

When enabled (default), existing field values on a post will not be overwritten during update:

- **Single-value fields:** If the field already has a value, it will be preserved and not updated.
- **Multi-value fields:** Only new values that do not already exist will be added; existing values are preserved.
- **Field format:** For multi-value fields (such as tags, multi_select, user_select, connection, location, location_meta, communication_channel), both direct array format (`[['value' => 'xxx']]`) and wrapped format (`['values' => [['value' => 'xxx']]]`) are accepted, but the API will always return the wrapped format for consistency.

To override this behavior and allow fields to be overwritten, set `do_not_overwrite_existing_fields` to `false` in the request body.

**Note:** This setting may prevent some direct manual record field updates if the field already contains a value.

## Returns

Will return the same content as: [Get Post](get-post.md)

