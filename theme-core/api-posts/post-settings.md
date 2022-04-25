# Post-Settings

## Get Settings

`Get` [https://example.com/wp-json/dt-posts/v2/{post\_type}/settings](https://example.com/wp-json/dt-posts/v2/{post_type}/settings)

### Return

\(object\) the settings object

Example format:

```json
{
  "tiles":
  {
    "status":{"label":"Status","tile_priority":10,"order":["overall_status","assigned_to","subassigned"]},
    "details":{"label":"Details","tile_priority":20,"order":["name","nickname","contact_phone","contact_email","location_grid","location_grid_meta","contact_address","contact_facebook","contact_twitter","contact_other","gender","age","baptism_date","sources","campaigns","people_groups"]},
    //etc
  },
  "fields":{ 
    "name":{"name":"Name","type":"text","tile":"details","in_create_form":true,"required":true,"icon":"http:\/\/example.com\/wp-content\/themes\/disciple-tools-theme\/dt-assets\/images\/name.svg","show_in_table":5},
    "last_modified":{"name":"Last Modified","type":"date","default":0,"customizable":false,"show_in_table":100},
    "post_date":{"name":"Creation Date","type":"date","default":0,"customizable":false},
    "favorite":{"name":"Favorite","type":"boolean","default":false,"private":true,"show_in_table":6,"icon":"http:\/\/example.com\/wp-content\/themes\/disciple-tools-theme\/dt-assets\/images\/star.svg"}
    //etc
  },
    
  "channels":{
    "email":{"name":"Email","icon":"http:\/\/example.com\/wp-content\/themes\/disciple-tools-theme\/dt-assets\/images\/email.svg?v=2","type":"communication_channel","tile":"details","customizable":false,"in_create_form":["access"],"label":"Email"},
    "address":{"name":"Address","icon":"http:\/\/example.com\/wp-content\/themes\/disciple-tools-theme\/dt-assets\/images\/house.svg?v=2","type":"communication_channel","tile":"details","mapbox":false,"customizable":false,"in_create_form":["access"],"label":"Address"},
    "twitter":{"name":"Twitter","icon":"http:\/\/example.com\/wp-content\/themes\/disciple-tools-theme\/dt-assets\/images\/twitter.svg?v=2","hide_domain":true,"type":"communication_channel","tile":"details","customizable":false,"label":"Twitter"}
    //etc
  },
  "connection_types":["relation","subassigned","subassigned_on","coaching","coached_by","baptized_by","baptized","people_groups","groups","group_leader","group_coach"],
  "label_singular":"Contact",
  "label_plural":"Contacts",
  "post_type":"contacts"
}
```