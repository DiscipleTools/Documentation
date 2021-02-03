## Field Types
- multi_select
- key_select
- communication_channel
- connection
- user_select
- text
- date
- number
- array
- post_user_meta
- boolean
- location

## Adding fields
```
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
- **name**: (string). The name you want the user to see for the field. Required.
- **type**: (string). the field type. Required.
- **description**: (string). Extra context for the field. May show up in the help modals. Optional.
- **default**: (array, string). Options for the field. Required for key_select_and multi_select fields.   
- **icon**: (string). The url of the icon to display next to the name.
- **tile**: (string). Which tile this field should be displayed on.
- **customizable**: (bool, string). If this field is customizable by the user in the wp_admin settings page. Options: false, 'add_only'
- **in_create_form**: (bool, array). Whether this field should be visible by default on the create post page. Either true or an array of (post) types to display on ex: [ "personal", "access" ]. 
- **hidden**: (bool). If this field should show on the front end in filter options or new record pages.
- **show_in_table**: (int). If this field should by default show in the list table. Lower number means higher priority. 
- **custom_display**: (bool). If this field should be ignored by D.T field display generator.

**Extra Parameters for connections fields**  
- **post_type**: the post_type of the connected posts
- **p2p_key**: the p2p connection key. See Declaring Connection Fields below.
- **p2p_direction**: the p2p direction. See Declaring Connection Fields below.
- **create-icon**: url for the icon user in the typeahead create button.

**Extra parameters for communication_channel fields**
- **hide_domain** whether to hide the url domain name when displaying a like. Ex "https://facebook.com/person" would show "person" as a link.

**Extra parameters for key_select and multi_select field**
- **default_color**: (string). Default color for key_select and multi_select options. This triggers the color mode for the select field 
- **default**: options: 
```
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
```
p2p_register_connection_type(
    [
        'name'           => 'contacts_to_groups',
        'from'           => 'contacts',
        'to'             => 'groups',
    ]
);
```
Here the connection is from the contacts post type to the groups post_type.

Declaring the field on the contacts post_type looks like:
```
$fields["groups"] = [
    "name" => __( 'Groups', 'disciple_tools' ),        
    "type" => "connection",
    "post_type" => "groups",
    "p2p_direction" => "from",
    "p2p_key" => "contacts_to_groups",
    'tile'     => 'details',
];
```
Note the direction and post_type change on the field declaration on the group post_type:
```
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
