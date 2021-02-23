# Update a comment for a contact or a group.

`POST` [https://example.com/wp-json/dt/v1/{contact\|\|group}/{contact\_id\|\|group\_id}/comment/update](https://example.com/wp-json/dt/v1/{contact||group}/{contact_id||group_id}/comment/update)

Replace `example.com` with your domain Replace `{contact||group}` with either `contact` or `group` Replace `{contact_id||group_id}` with the ID of the contact or group.

**Parameters**

* **comment\_ID** \(int\) the ID of the comment to update.
* **comment\_content** \(string\) the new body of the comment. 

**Returns**

If successful will return the int: 1

