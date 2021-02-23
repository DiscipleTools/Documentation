# Fields

## Field Types

* multi\_select
* key\_select
* communication\_channel
* connection
* user\_select
* text
* date
* number
* array
* post\_user\_meta
* boolean
* location

## Adding fields

```php
add_filter( "dt_custom_fields_settings", "dt_contact_fields", 1, 2 );
function dt_contact_fields( array $fields, string $post_type = ""){
    //check if we are dealing with a contact
    if ($post_type === "contacts"){
        //check if the language field is already set
        if ( !isset( $fields["language"] )){
            //define the language field
            $fields["language"] = [
                "name" => __( "Spoken Language", "disciple_tools_language" ),
                "type" => "key_select",
                "default" => [
                    "english" => __( "English", "disciple_tools_language" ),
                    "french" => __( "French", "disciple_tools_language" )
                ],
                "tile" => "contact_language"
            ];
        }
    }
    //don't forget to return the update fields array
    return $fields;
}
```

### Parameters

* **name**: \(string\). The name you want the user to see for the field. Required.
* **type**: \(string\). the field type. Required.
* **description**: \(string\). Extra context for the field. May show up in the help modals. Optional.
* **default**: \(array, string\). Options for the field. Required for key\_select\_and multi\_select fields.   
* **icon**: \(string\). The url of the icon to display next to the name.
* **tile**: \(string\). Which tile this field should be displayed on.
* **customizable**: \(bool, string\). If this field is customizable by the user in the wp\_admin settings page. Options: false, 'add\_only'
* **in\_create\_form**: \(bool, array\). Whether this field should be visible by default on the create post page. Either true or an array of \(post\) types to display on ex: \[ "personal", "access" \]. 
* **hidden**: \(bool\). If this field should show on the front end in filter options or new record pages.
* **show\_in\_table**: \(int\). If this field should by default show in the list table. Lower number means higher priority. 
* **custom\_display**: \(bool\). If this field should be ignored by D.T field display generator.

**Extra Parameters for connections fields**

* **post\_type**: the post\_type of the connected posts
* **p2p\_key**: the p2p connection key. See Declaring Connection Fields below.
* **p2p\_direction**: the p2p direction. See Declaring Connection Fields below.
* **create-icon**: url for the icon user in the typeahead create button.

**Extra parameters for communication\_channel fields**

* **hide\_domain** whether to hide the url domain name when displaying a like. Ex "[https://facebook.com/person](https://facebook.com/person)" would show "person" as a link.

**Extra parameters for key\_select and multi\_select field**

* **default\_color**: \(string\). Default color for key\_select and multi\_select options. This triggers the color mode for the select field 
* **default**: options:

  ```php
  [
    "option_key" => [
        "label" => "" // name of the option
        "description" => "" //option description
        "color" => "#3F729B" //color used to display the option as.
        "hidden" => bool //don't show this option on the front end.
        "icon" => "" The url of the icon to display next to the option.
    ]
  ]
  ```

## Declaring Connection Fields

Connections field types need to be registered so the connection can be saved in database in the p2p table.

Let's register Groups connection.

```php
p2p_register_connection_type(
    [
        'name'           => 'contacts_to_groups',
        'from'           => 'contacts',
        'to'             => 'groups',
    ]
);
```

Here the connection is from the contacts post type to the groups post\_type.

Declaring the field on the contacts post\_type looks like:

```php
$fields["groups"] = [
    "name" => __( 'Groups', 'disciple_tools' ),        
    "type" => "connection",
    "post_type" => "groups",
    "p2p_direction" => "from",
    "p2p_key" => "contacts_to_groups",
    'tile'     => 'details',
];
```

Note the direction and post\_type change on the field declaration on the group post\_type:

```php
$fields["members"] = [
    "name" => __( 'Member List', 'disciple_tools' ),
    "type" => "connection",
    "post_type" => "contacts",
    "p2p_direction" => "to",
    "p2p_key" => "contacts_to_groups"
];
```

## Function to have D.T display a field:

`render_field_for_display( $field_key, $fields_options, $post, $show_extra_controls = false, $show_hidden = false )`

