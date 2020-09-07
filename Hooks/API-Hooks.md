## Post Create

**dt_create_post_check_proceed** filter  
Extra permission check before the fields are processed  
Parameters 2: bool continue, array $fields


**dt_post_create_fields** filter  
Add, remove or modify fields before the fields are processed.  
Parameters 2: array $fields, string $post_type


**dt_post_create_allow_fields** filter  
Add extra field keys that are allowed. The API will reject requests with fields that are not declared or allowed
Parameters 2: array $field_keys, string $post_type

*post created*  
*fields processed*

**dt_post_created** action  
Runs after post is created and fields are processed  
Parameters 3: string $post_type, int post_id, array $initial_request_fields

## Update Post

**dt_post_update_fields**  filter  
Add, remove or modify fields before the fields are processed.  
Parameters 3: array $fields, string $post_type, int $post_id

**dt_post_create_allow_fields** filter  
Add extra field keys that are allowed. The API will reject requests with fields that are not declared or allowed  
Parameters 2: array $field_keys, string $post_type

*fields processed*

**dt_post_updated** action  
Runs after fields are processed  
Parameters 5: string $post_type, int post_id, array $initial_request_fields, array $post_fields_before_update, array $post_fields_after_update

## Get Post


**dt_after_get_post_fields_filter** filter  
Add, modify or remove fields from the response  
Parameters 2: array $fields, string $post_type

## List Post
**dt_search_viewable_posts_query** filter  
Add or remove query parameters  
Parameters 1: array $query_fields

**dt_adjust_post_custom_fields**  filter  
Runs an each post in the query result. Add, remove, or modify the post fields 
Parameters 2: array $fields, string $post_type

**dt_list_posts_custom_fields**  filter  
Modify the response before the list of posts is returned.  
Parameters 2: array $request_response, string $post_type


## Comments 
**dt_comment_created**  Action  
Runs after a comment is created  
Parameters 4: string $post_type, int $post_id, int $created_comment_id, string $comment_type

**dt_filter_post_comments**  Filter  
Modify the response before the list of comments is returned.  
Parameters 3: array $request_body, sting $post_type, int $post_id

