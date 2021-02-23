## Get all comments on a contact or a group

`GET` https://example.com/wp-json/dt/v1/{contact||group}/{contact_id||group_id}/comments

Replace `example.com` with your domain
Replace `{contact||group}` with either `contact` or `group`
Replace `{contact_id||group_id}` with the ID of the contact or group.

**Parameters**
- none

**Returns**

- **An array of comments:**
  - **gravatar** (string) the gravatar url for the author
  - **comment_author** (string): the display_name of the author
  - **comment_ID** (integer) The comment ID
  - **comment_post_ID** (integer) The ID of the post/page that this comment responds to
  - **comment_author_email** (string) The comment author's email
  - **comment_author_url** (string) The comment author's webpage
  - **comment_author_IP** (string) The comment author's IP
  - **comment_date** (string) The datetime of the comment (YYYY-MM-DD HH:MM:SS)
  - **comment_date_gmt** (string) The GMT datetime of the comment (YYYY-MM-DD HH:MM:SS)
  - **comment_content** (string) The comment's content
  - **comment_karma** (integer) The comment's karma
  - **comment_approved** (string) The comment approval level (0, 1 or "spam")
  - **comment_agent** (string) The commenter's user agent (browser, operating system, etc.)
  - **comment_type** (string) The comment's type. Ex comment, facebook...
  - **comment_parent** (string) The parent comment's ID for nested comments (0 for top level)
  - **user_id** (integer) The comment author's ID if s/he is registered (0 otherwise)
  
**Return Example**
```
[ 
 { comment_ID: "2431", comment_post_ID: "962", comment_author: "ME" ... },
 { comment_ID: "2432", comment_post_ID: "962", comment_author: "You" ... }
]
```
