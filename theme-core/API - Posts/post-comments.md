# Post-Comments

## Get comments

`Get` [https://example.com/wp-json/dt-posts/v2/{post\_type}/{post\_id}/comments](https://example.com/wp-json/dt-posts/v2/{post_type}/{post_id}/comments)

### Parameters

* **number** \(int\) optional. How many comments to return
* **offset** \(int\) optional. How many comments to skip \(for pagination\)

### Returns

```js
[ 
   comments: (array) An array of comments.
   total: (int) the number of comment in total
]
```

## Create a comment

`POST` [https://example.com/wp-json/dt/v2/{post\_type}/{post\_id}/comments](https://example.com/wp-json/dt/v2/{post_type}/{post_id}/comments)

### Parameters

* **comment** \(string\) the body of the comment. 
* **date** \(string\) optional. format "Y-m-d H:i:s"
* **comment\_type** \(string\) optional. The comment type. Default: 'comment'

Query params: add `?silent=true` to disable notifications

**@mentions** Mention are used to make sure a user sees a comment and gets a notification. This example @mentions user with id 46 and will display bob as the name of the user.

```js
{
    "comment": "@[bob](46) this is a mention notification"
}
```

### Returns

\(object\) The default wordpress comment. See [https://developer.wordpress.org/reference/functions/get_comment/](https://developer.wordpress.org/reference/functions/get_comment/)

## Update a comment

`POST` [https://example.com/wp-json/dt/v2/{post\_type}/{post\_id}/comments/{comment\_id}](https://example.com/wp-json/dt/v2/{post_type}/{post_id}/comments/{comment_id})

### Parameters

* **comment** \(string\) the body of the comment.

### Returns

\(object\) The default wordpress comment. See [https://developer.wordpress.org/reference/functions/get_comment/](https://developer.wordpress.org/reference/functions/get_comment/)

## Delete a comment

`DELETE` [https://example.com/wp-json/dt/v2/{post\_type}/{post\_id}/comments/{comment\_id}](https://example.com/wp-json/dt/v2/{post_type}/{post_id}/comments/{comment_id})

### Returns

\(bool\) true if the contact was deleted
