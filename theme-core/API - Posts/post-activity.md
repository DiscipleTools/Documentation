# Post Activity

## Get Activity

`Get` [https://example.com/wp-json/dt-posts/v2/{post\_type}/{post\_id}/activity](https://example.com/wp-json/dt-posts/v2/{post_type}/{post_id}/activity)

### Parameters

* **number** \(int\) optional. How many activities to return
* **offset** \(int\) optional. How many activities to skip \(for pagination\)

### Returns

```text
[ 
   activity: (array) An array of activities. See below for format.
   total: (int) the number of activities in total
]
```

Activity list format:

```js
[
  {
    "meta_key":"overall_status",
    "gravatar":"http:\/\/2.gravatar.com\/avatar\/id?s=16&d=mm&r=g",
    "name":"Me", //name of the user who did the activity
    "object_note":"Overall Status: Active",
    "hist_time":"1559128822", //when the activity happened
    "meta_id":"150", // the ID of the related post_meta field
    "histid":"179" // the ID of the activity
  },
  {
    ...activity2...
  }
]
```

## Get Singe Activity

`Get` [https://example.com/wp-json/dt-posts/v2/{post\_type}/{post\_id}/activity/{activity\_id}](https://example.com/wp-json/dt-posts/v2/{post_type}/{post_id}/activity/{activity_id})

### Returns

\(array\) The activity array.

Activity list format:

```json
{
  "meta_key":"overall_status",
  "gravatar":"http:\/\/2.gravatar.com\/avatar\/id?s=16&d=mm&r=g",
  "name":"Me", //name of the user who did the activity
  "object_note":"Overall Status: Active",
  "hist_time":"1559128822", //when the activity happened
  "meta_id":"150", // the ID of the related post_meta field
  "histid":"179" // the ID of the activity
}
```
