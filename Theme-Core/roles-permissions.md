Documentation for theme version 1.0.0 or greater

# Permissions

Permissions guide what a user can and cannot see and what records the user has access to.
What Roles a user has determines what a user is permitted to do.

### Records Access

By default when a user creates contact, group or any record, that record is shared with the user.  
If a record is shared with a user, that user has permission to view and update that record and can share the record with other users.   
The list page looks up all the records that user has access to and displays them. By default this means the list page will ask for all the records shared with the user.

### Expanding access

Some roles like the Administrator and the Dispatcher can see more than the records they created.
This is because their roles has additional capabilities which expands their access to records.  
An example is the Dispatcher role has has permission to see and update all access contacts. The dispatcher role has the `dt_all_access_contacts` capability.
The access module looks for users which that capability and gives them access to all contacts of type 'access'.


# Roles
Since version 1.0.0 Roles are modular. The theme sets declares a set of roles and their capabilities. Plugin can add roles and modify capabilities on all roles.

Let's build out the Dispatcher role.

First we hook into the `dt_set_roles_and_permissions` filter to declare role and set the capabilities.
```
add_filter( 'dt_set_roles_and_permissions', [ $this, 'dt_set_roles_and_permissions' ], 10, 1 );
public function dt_set_roles_and_permissions( $expected_roles ){
    
    $expected_roles['dispatcher'] = [
        "label" => __( "Dispatcher", "disciple_tools" ), // the displayed name of the role
        "descriptions" => "Monitor new D.T contacts and assign the to waiting Multipliers", //discription shown to help the admin choose what role to assign a user.
        "permissions" => [
            'dt_all_access_contacts' => true, //gives permission to all contacts with the 'access' type.
            'view_project_metrics' => true, //view all poject chart is the metrics tab
            'list_users' => true, //list users in the wp-admin
            'dt_list_users' => true, //list user in the theme (needed for assigning to multipliers)
        ]
    ];
    return $expected_roles;
}
```
If you want to add capabilities to an existing role from your plugin make sure the filter priority is higher that the number user when declaring the role in the first place.
Let's add a capability to the dispatcher role. They priority used by the filter when declaring it was 10. So we'll used 20. 
```
add_filter( 'dt_set_roles_and_permissions', [ $this, 'dt_set_roles_and_permissions' ], 20, 1 );
public function dt_set_roles_and_permissions( $expected_roles ){
    //check if the role is declared. You don't need to reset the label and description.
    if ( isset( $expected_roles["dispatcher"]["permissions"] ) ){
        $expected_roles["dispatcher"]["permissions"]["my_custom_capability"] = true;
    }
    return $expected_roles;
}
```

# Linking capabilities to permissions

### In listing records

**dt_filter_access_permissions** filter  
This filter is called when querying a list of records.
Here you can expand or restrict the records the user has access to based on their role and capabilities.


Example, giving the dispatcher permission to all contacts of type 'access':
```
public static function dt_filter_access_permissions( $permissions, $post_type ){
    if ( $post_type === "contacts" ){
        //give user permission to all contacts af type 'access'
        if ( current_user_can( "dt_all_access_contacts" ) ){
            $permissions[] = [ "type" => [ "access" ] ];
        }
    }
    return $permissions;
}
```

### In viewing records

**dt_can_view_permission** filter

Example, giving the Dispatcher permission to view any contact of type 'access':
```
add_filter( "dt_can_view_permission", [ $this, 'can_view_permission_filter' ], 10, 3 );
public function can_view_permission_filter( $has_permission, $post_id, $post_type ){
    if ( $post_type === "contacts" ){
        if ( current_user_can( 'dt_all_access_contacts' ) ){
            $contact_type = get_post_meta( $post_id, "type", true );
            if ( $contact_type === "access" ){
                return true;
            }
        }
    }
    return $has_permission;
}
```


### In updating records

**dt_can_update_permission** filter

Example, giving the Dispatcher permission to update any contact of type 'access':
```
add_filter( "dt_can_update_permission", [ $this, 'can_update_permission_filter' ], 10, 3 );
public function can_update_permission_filter( $has_permission, $post_id, $post_type ){
    if ( $post_type === "contacts" ){
        if ( current_user_can( 'dt_all_access_contacts' ) ){
            $contact_type = get_post_meta( $post_id, "type", true );
            if ( $contact_type === "access" ){
                return true;
            }
        }
    }
    return $has_permission;
}
```

### In deleting records

**dt_can_delete_permission** filter

Would be similar to the code above.