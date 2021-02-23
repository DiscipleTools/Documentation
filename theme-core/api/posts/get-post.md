# Get-Post

`GET` [https://example.com/wp-json/dt-posts/v2/{post\_type}/{post\_id}/](https://example.com/wp-json/dt-posts/v2/{post_type}/{post_id}/)

Requires permission: `access_{post_type}`

### Returns

\(json object\): the contact. Each field type will show in a different way:

* **"ID"**
* **"title"**:"Jonh Doe",
* **"created\_date"**:"2018-06-05 16:07:16",
* **"last\_modified"**:"1552987784",  //date the contact has last been modifield
* **text fields**

```text
"field_key": "text"
```

* **multi\_select fields**

  ```text
  "field_key": [ 
    "option_key", 
    "option_key",
    ... 
  ]
  ```

* **key\_select fields**

  ```text
  "field_key": {
   "key":"option_key",
   "label":"option_label"
  },
  ```

* **connection fields**

  ```text
  "field_key": [ 
   { 
       "ID":{post_id},
       "post_type":"{post_type}",
       "post_date_gmt":"2018-05-29 13:12:01",
       "post_date":"2018-05-29 13:12:01",
       "post_title":"{post_title}"
   },
   ...
  ]
  ```

* **date fields**

  ```text
  "field_key": {
    timestamp: "1552953600",  //unix timestamp and the date
    formatted: "March 19, 2019" // date formatted base on selected date format in WP settings
  }
  ```

## Return Example

\`\`\` { "ID":72, "title":"Mojiz Chra\u00efbi", "created\_date":"2018-06-05 16:07:16", "last\_modified":"1552987784", geonames":\[ {"id":123456,"label":"World"} \], "groups":\[ {"ID":83,"post\_type":"groups","post\_date\_gmt":"2018-07-02 15:05:53","post\_date":"2018-07-02 15:05:53","post\_title":"Local Christian Church"} \], "people\_groups":\[\], "baptized":\[ {"ID":105,"post\_type":"contacts","post\_date\_gmt":"2018-07-17 14:54:35","post\_date":"2018-07-17 14:54:35","post\_title":"Jessica Blue"} \], "baptized\_by":\[\], "coaching":\[\], "coached\_by":\[\], "subassigned":\[\], "relation":\[\], "seeker\_path":{"key":"none","label":"Contact Attempt Needed"},

"type":{"key":"media","label":"Media"}, "assigned\_to":{"id":"8","type":"user","display":"Anthony Palacio \(multiplier\)","assigned-to":"user-8"}, "overall\_status":{"key":"assigned","label":"Waiting to be accepted"}, "contact\_phone":\[ {"verified":false,"value":"555-5555","key":"contact\_phone\_ca2"} \], "contact\_email":\[ {"verified":false,"value":"","key":"contact\_email\_313"} \], "sources":\["facebook"\], "accepted":false, "gender":{"key":"male","label":"Male"}, "age":{"key":"&lt;19","label":"Under 18 years old"}, "milestones":\[ "milestone\_has\_bible", "milestone\_can\_share", "milestone\_reading\_bible" \], "baptism\_generation":"0", "baptism\_date": {timestamp: "1552953600", formatted: "March 19, 2019"} }

