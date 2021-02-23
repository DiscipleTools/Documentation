## Delete a comment on a contact or a group.

`DELETE` https://example.com/wp-json/dt/v1/{contact || group}/{contact_id || group_id}/comment

Replace `example.com` with your domain
Replace `{contact||group}` with either `contact` or `group`
Replace `{contact_id||group_id}` with the ID of the contact or group.

**Parameters**
- **comment_ID** (int) the ID of the comment to delete

**Returns**

**true** on success, **false** on error