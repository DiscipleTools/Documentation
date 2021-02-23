# Permissions

This is a list of the capabilities used by D.T roles within the theme core.
Each role is assigned certain capabilities which determines what the user is able to do.

## WP capabilities
**edit_posts**  
give the user access and update ability for site links

**edit_page**  
give the user access and update ability for site links

**read**  
let the user access the wp-admin interface

## D.T Admin capabilities
**manage_dt**  
let the user update all D.T settings

## User management
**promote_users**  
Ability to add/update/remove a user roles. Note only and administrator can give or take away the administrator role.

**edit_users**   
Edit user data in the wp-admin interface

**create_users**  
Create new users or invite users to the instance

**delete_users**  
Ability to delete users

**list_users**    
WP Admin list users

**dt_list_users**  
D.T Front End list users

## Metrics
**view_project_metrics**  
view more metrics for the whole project

## Locations
**read_location**  
list locations

## People Groups
**access_peoplegroups**  
Basic permission list and update all people groups.

**list_peoplegroups**  
List all people groups in typeaheads.

## Post Types
Replace `post_type` with `contacts`, `groups` or your custom post type.

**access_[post_type]**   
Give the user access to view their or all records of the post_type

**create_[post_type]**    
Gives the user the ability to create a record of the post_type

**list_all_[post_type]**  
List all post_type record names in typeaheads

**assign_any_[post_type]**  
Ability to assign any post_type record to a user.

**access_specific_sources**    
Ability to list and update all contacts of source x

**dt_all_access_contacts** >= v1.0.0  
List and update all contact of type 'access'

**view_any_[post_type]**  
gives full permission to view and update all records of the post type. Recommended only for API/script use.

