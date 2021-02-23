# Get all comments on a contact or a group

`GET` [https://example.com/wp-json/dt/v1/{contact\|\|group}/{contact\_id\|\|group\_id}/comments](https://example.com/wp-json/dt/v1/{contact||group}/{contact_id||group_id}/comments)

Replace `example.com` with your domain Replace `{contact||group}` with either `contact` or `group` Replace `{contact_id||group_id}` with the ID of the contact or group.

**Parameters**

* none

**Returns**

* **An array of comments:**
  * **gravatar** \(string\) the gravatar url for the author
  * **comment\_author** \(string\): the display\_name of the author
  * **comment\_ID** \(integer\) The comment ID
  * **comment\_post\_ID** \(integer\) The ID of the post/page that this comment responds to
  * **comment\_author\_email** \(string\) The comment author's email
  * **comment\_author\_url** \(string\) The comment author's webpage
  * **comment\_author\_IP** \(string\) The comment author's IP
  * **comment\_date** \(string\) The datetime of the comment \(YYYY-MM-DD HH:MM:SS\)
  * **comment\_date\_gmt** \(string\) The GMT datetime of the comment \(YYYY-MM-DD HH:MM:SS\)
  * **comment\_content** \(string\) The comment's content
  * **comment\_karma** \(integer\) The comment's karma
  * **comment\_approved** \(string\) The comment approval level \(0, 1 or "spam"\)
  * **comment\_agent** \(string\) The commenter's user agent \(browser, operating system, etc.\)
  * **comment\_type** \(string\) The comment's type. Ex comment, facebook...
  * **comment\_parent** \(string\) The parent comment's ID for nested comments \(0 for top level\)
  * **user\_id** \(integer\) The comment author's ID if s/he is registered \(0 otherwise\)

**Return Example**

```text
[ 
 { comment_ID: "2431", comment_post_ID: "962", comment_author: "ME" ... },
 { comment_ID: "2432", comment_post_ID: "962", comment_author: "You" ... }
]
```

