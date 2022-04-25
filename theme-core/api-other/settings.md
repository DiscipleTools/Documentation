# Post-Settings

## Get Settings

`Get` [https://example.com/wp-json/dt-core/v1/settings](https://example.com/wp-json/dt-core/v1/settings)

### Return

\(object\) the settings object
- available\_translations: list of languages available for the user to select
- post\_types: list of post types and the post type settings. See [Post Type Settings](../api-posts/post-settings.md)

Example format:

```json5
{
  "available_translations":[
    {"language":"en_US","english_name":"English (United States)","native_name":"English (United States)","site_default":true},
    {"language":"am_ET","native_name":"Amharic (Ethiopia)","english_name":"Amharic (Ethiopia)","site_default":false},
    //etc
  ],
  "post_types": {
    "peoplegroups": {}, //see post type settings
    "contacts": {},
    "groups": {}
    //etc
  }
}
```