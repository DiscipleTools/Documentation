# Permissions

This is a list of the capabilities used by D.T roles within the theme core. Each role is assigned certain capabilities which determines what the user is able to do.

## WP capabilities

**edit\_posts**  
give the user access and update ability for site links

**edit\_page**  
give the user access and update ability for site links

**read**  
let the user access the wp-admin interface

## D.T Admin capabilities

**manage\_dt**  
let the user update all D.T settings

## User management

**promote\_users**  
Ability to add/update/remove a user roles. Note only and administrator can give or take away the administrator role.

**edit\_users**  
Edit user data in the wp-admin interface

**create\_users**  
Create new users or invite users to the instance

**delete\_users**  
Ability to delete users

**list\_users**  
WP Admin list users

**dt\_list\_users**  
D.T Front End list users

## Metrics

**view\_project\_metrics**  
view more metrics for the whole project

## Locations

**read\_location**  
list locations

## People Groups

**access\_peoplegroups**  
Basic permission list and update all people groups.

**list\_peoplegroups**  
List all people groups in typeaheads.

## Post Types

Replace `post_type` with `contacts`, `groups` or your custom post type.

**access\_\[post\_type\]**  
Give the user access to view their or all records of the post\_type

**create\_\[post\_type\]**  
Gives the user the ability to create a record of the post\_type

**list**_**all**_**\[post\_type\]**  
List all post\_type record names in typeaheads

**assign**_**any**_**\[post\_type\]**  
Ability to assign any post\_type record to a user.

**access\_specific\_sources**  
Ability to list and update all contacts of source x

**dt\_all\_access\_contacts** &gt;= v1.0.0  
List and update all contact of type 'access'

**view**_**any**_**\[post\_type\]**  
gives full permission to view and update all records of the post type. Recommended only for API/script use.

