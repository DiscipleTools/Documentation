# Post-Sharing

## Get shares

`Get` [https://example.com/wp-json/dt-posts/v2/{post\_type}/{post\_id}/shares](https://example.com/wp-json/dt-posts/v2/{post_type}/{post_id}/shares)

Requires permission: `view_any_{post_type}` or post is shared with user.

### Return

\(array\) An array of shares

Example format:

```js
[
  {
    "id":"10", // the id of the share
    "user_id":"1", // user the post is shared with
    "post_id":"27", // the id of the post
    "meta":null, // meta related to the share
    "display_name":"Me" // display name of the user
  },
  {
    ...share2...
  }
]
```

## Share the post with a user

`POST` [https://example.com/wp-json/dt-posts/v2/{post\_type}/{post\_id}/shares](https://example.com/wp-json/dt-posts/v2/{post_type}/{post_id}/shares)

### Parameters

* **user\_id** \(int\): the id of the user to share the post with

### Returns

`1` if successful

## Unshare the post with a user

`DELETE` [https://example.com/wp-json/dt-posts/v2/{post\_type}/{post\_id}/shares](https://example.com/wp-json/dt-posts/v2/{post_type}/{post_id}/shares)

### Parameters

* **user\_id** \(int\): the id of the user to unshare the post with

### Returns

`1` if successful

