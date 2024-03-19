# Post Comments

## Get comments

`Get` [https://example.com/wp-json/dt-posts/v2/{post\_type}/{post\_id}/comments](https://example.com/wp-json/dt-posts/v2/{post_type}/{post_id}/comments)

### Parameters

* **number** \(int\) optional. How many comments to return
* **offset** \(int\) optional. How many comments to skip \(for pagination\)

### Returns

```javascript
[ 
   comments: (array) An array of comments.
   total: (int) the number of comment in total
]
```

Includes comment meta data and reactions along with default comment:
```javascript
{
   "comments": [{
       ...
       "comment_reactions": {
           "reaction_thumbs_up": [
               { "name": "admin", "user_id": "1" },
               { "name": "user1", "user_id": "2" }
           ],
           "reaction_heart": [
               { "name": "admin", "user_id": "1" }
           ]
       },
       "comment_meta": {
           "audio_url": [
               { "id": "1", "value": "https://my.path/to/audio.mp3" },
               { "id": "2", "value": "https://my.path/to/audio.ogg" },
           ]
       }
   }]
}
```

## Create a comment

`POST` [https://example.com/wp-json/dt/v2/{post\_type}/{post\_id}/comments](https://example.com/wp-json/dt/v2/{post_type}/{post_id}/comments)

### Parameters

* **comment** \(string\) the body of the comment. 
* **date** \(string\) optional. format "Y-m-d H:i:s"
* **comment\_type** \(string\) optional. The comment type. Default: 'comment'
* **meta** \(object\) optional. Additional meta data

Query params: add `?silent=true` to disable notifications

**@mentions** Mention are used to make sure a user sees a comment and gets a notification. This example @mentions user with id 46 and will display bob as the name of the user.

```javascript
{
    "comment": "@[bob](46) this is a mention notification"
}
```

**links** Create a link to another record, page or site
```javascript
{
    "comment": "See changes on [link text](link url)
}
```

**meta data** Create additional meta data - such as reactions or audio files - by passing a meta data object with the key/value pairs to be created. Values can be primitive types (string, int, etc) or arrays.
```javascript
{
    "meta": {
        "audio_url": [
            "https://my.path/to/audio.mp3",
            "https://my.path/to/audio.ogg"
        ]
    }
}
```
```javascript
{
    "meta": {
        "audio_url": "https://my.path/to/audio.ogg"
    }
}
```

### Returns

\(object\) The default wordpress comment. See [https://developer.wordpress.org/reference/functions/get\_comment/](https://developer.wordpress.org/reference/functions/get_comment/)

Includes comment meta data along with default comment:
```javascript
{
    "comment_meta": {
        "audio_url": [
            "https://my.path/to/audio.mp3",
            "https://my.path/to/audio.ogg"
        ]
    }
}
```

## Update a comment

`POST` [https://example.com/wp-json/dt/v2/{post\_type}/{post\_id}/comments/{comment\_id}](https://example.com/wp-json/dt/v2/{post_type}/{post_id}/comments/{comment_id})

### Parameters

* **comment** \(string\) the body of the comment.
* **meta** \(object\) optional. Additional meta data

### Returns

\(object\) The default wordpress comment. See [https://developer.wordpress.org/reference/functions/get\_comment/](https://developer.wordpress.org/reference/functions/get_comment/)

Includes comment meta data along with default comment:
```javascript
{
    "comment_meta": {
        "audio_url": [
            "https://my.path/to/audio.mp3",
            "https://my.path/to/audio.ogg"
        ]
    }
}
```

## Delete a comment

`DELETE` [https://example.com/wp-json/dt/v2/{post\_type}/{post\_id}/comments/{comment\_id}](https://example.com/wp-json/dt/v2/{post_type}/{post_id}/comments/{comment_id})

### Returns

\(bool\) true if the contact was deleted

