# CUSTOMIZATION

- [Adding a metrics menu](#adding-a-metrics-menu)
- [Adding Fields and Tiles](#adding-fields-and-tiles)
- [Custom Post Types](#custom-post-types)
- [Modifying Fields](#modifying-fields)

## Adding a metrics menu

See [Disciple.Tools Advanced Metrics Template](https://github.com/DiscipleTools/disciple-tools-advanced-metrics-template)

## Adding Fields and Tiles

### Adding fields

Don’t see something you need? Want to track something different? You can expand Disciple.Tools functionality!

See this [starter plugin branch](https://github.com/DiscipleTools/disciple-tools-starter-plugin-template/tree/tile_and_field_example) for an implemented example.

### Adding a field to track

You need tell Disciple.tools that you want to track something new. Fields are defined in the theme’s custom post type file. And we give you a way to add to that list using the `dt_custom_fields_settings` filter.

Here is an example on how to add a spoken language field on the contact:

```javascript
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
                ]
            ];
        }
    }
    //don't forget to return the update fields array
    return $fields;
}
```

Here we take advantage of the `dt_custom_fields_settings` filter, tell it to call the `dt_contact_fields` function. The `1` parameter is the priority. We want this to be called before other filters. The `2` parameter is the number of arguments we expect (fields and post_type)

### Displaying the field on the contact record.

Note that we have the language field defined, we want to display it on the contact itself.

The will take 2 steps:

- Declaring the new section(s) using the    `dt_contact_details_additional_section_ids` filter
- Building the new section in the `dt_contact_details_additional_section` action

#### Declaring the section

```javascript
add_filter( "dt_details_additional_section_ids", "dt_declare_section_id", 999, 2 );
function dt_declare_section_id( $sections, $post_type = "" ){
    //check if we are on a contact
    if ($post_type === "contacts"){
        $contact_fields = Disciple_Tools_Contact_Post_Type::instance()->get_custom_fields_settings();
        //check if the language field is set
        if ( isset( $contact_fields["language"] ) ){
            $sections[] = "contact_language";
        }
        //add more section ids here if you want...
    }
    return $sections;
}
```

#### Adding the section

```php
add_action( "dt_details_additional_section", "dt_add_section" );
function dt_add_section( $section ){
    if ($section == "contact_language"){
        $contact_id = get_the_ID();
        $contact_fields = Disciple_Tools_Contact_Post_Type::instance()->get_custom_fields_settings();
        $contact = Disciple_Tools_Contacts::get_contact( $contact_id, true )
    ?>
        <!-- need you own css? -->
        <style type="text/css">
            .required-style-example {
                color: red
            }
        </style>

        <label class="section-header">
            <?php esc_html_e( 'Language', 'disciple_tools' )?>
        </label>
        <div class="section-subheader">
            <?php esc_html_e( 'Spoken Language', 'disciple_tools' )?> <span class="required-style-example">*</span>
        </div>
        <select class="select-field" id="language" style="margin-bottom: 0px">
            <?php
            foreach ( $contact_fields["language"]["default"] as $key => $value ){
                if ( $contact["language"]["key"] === $key ) {
                    ?>
                    <option value="<?php echo esc_html( $key ) ?>" selected><?php echo esc_html( $value["label"] ); ?></option>
                <?php } else { ?>
                    <option value="<?php echo esc_html( $key ) ?>"><?php echo esc_html( $value["label"] ); ?></option>
                <?php }
            }
            ?>
        </select>


        <script type="application/javascript">
            //enter jquery here if you need it
            jQuery(($)=>{
            })
        </script>
    <?php
    }

    //add more sections here if you want...
}
```

#### End result

![End result](https://github.com/DiscipleTools/disciple-tools-theme/raw/master/dt-assets/images/wiki/new_section_example.png)

### Add field to site search

If you want the custom field to be searched when using the contact/group search, you can add the field name to the list of fields to be searched using the `dt_search_extra_post_meta_fields filter`.

```javascript
add_filter( "dt_search_extra_post_meta_fields", "dt_search_fields", 10, 1 );
function dt_search_fields( array $fields ) {
    //add the "language" field added in the dt_contact_fields function to search
    array_push( $fields, "language" );
    return $fields;
}
```

## Custom Post Types

Contacts and Groups are post types. With custom post types you can add a post type gaining:

- a menu tab next to metrics
- a menu option to create records
- a list page
- a details page.
- a set of endpoints ready to use.
- some cool to show your friends.

[The started plugin](https://github.com/DiscipleTools/disciple-tools-starter-plugin-template) comes with a custom post type example named “starter”.

## Modifying Fields

Here is how you can modify fields like the seeker_path and the milestones. We do want to encourage you to closely examine the default options. We might be already tracking what you want to add in a different way, or named differently.

If you want to add a new field or set of options have a look at this topic: [Adding Fields and Tiles](#adding-fields-and-tiles)

```javascript
add_filter( "dt_custom_fields_settings", "dt_custom_fields", 1, 2 );


function dt_custom_fields( array $fields, string $post_type = "" ){
    if ( $post_type === "contacts" ) {
        //add the baptized milestone
        $fields['milestone_baptized'] = [
            'name'        => __( 'Baptized', 'disciple_tools' ),
            'description' => '',
            'type'        => 'key_select',
            'default'     => [We created them from our experie

                'no' => __( 'No', 'disciple_tools' ),
                'yes' => __( 'Yes', 'disciple_tools' )
            ],
            'section'     => 'milestone',
        ];

        //add an option to the seeker path (or change the label)
        if ( isset( $fields["seeker_path"]["default"] )){
            $fields["seeker_path"]["default"]['coaching'] = __( 'Being Coached' );
        }
    }
    return $fields;
}
```
