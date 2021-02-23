# API-Hooks

Documentation for theme version 1.0.0 or greater

## Post Create

**dt\_create\_post\_check\_proceed** filter  
Extra permission check before the fields are processed  
Parameters 2: bool continue, array $fields

**dt\_post\_create\_fields** filter  
Add, remove or modify fields before the fields are processed.  
Parameters 2: array $fields, string $post\_type

**dt\_post\_create\_allow\_fields** filter  
Add extra field keys that are allowed. The API will reject requests with fields that are not declared or allowed Parameters 2: array $field\_keys, string $post\_type

_post created_  
_fields processed_

**dt\_post\_created** action  
Runs after post is created and fields are processed  
Parameters 3: string $post\_type, int post\_id, array $initial\_request\_fields

## Update Post

**dt\_post\_update\_fields** filter  
Add, remove or modify fields before the fields are processed.  
Parameters 4: array $fields, string $post\_type, int $post\_id, array $existing\_post

**dt\_post\_create\_allow\_fields** filter  
Add extra field keys that are allowed. The API will reject requests with fields that are not declared or allowed  
Parameters 2: array $field\_keys, string $post\_type

_fields processed_

**dt\_post\_updated** action  
Runs after fields are processed  
Parameters 5: string $post\_type, int post\_id, array $initial\_request\_fields, array $post\_fields\_before\_update, array $post\_fields\_after\_update

## Get Post

**dt\_after\_get\_post\_fields\_filter** filter  
Add, modify or remove fields from the response  
Parameters 2: array $fields, string $post\_type

## List Post

**dt\_search\_viewable\_posts\_query** filter  
Add or remove query parameters  
Parameters 1: array $query\_fields

**dt\_adjust\_post\_custom\_fields** filter  
Runs an each post in the query result. Add, remove, or modify the post fields Parameters 2: array $fields, string $post\_type

**dt\_list\_posts\_custom\_fields** filter  
Modify the response before the list of posts is returned.  
Parameters 2: array $request\_response, string $post\_type

## Comments

**dt\_comment\_created** Action  
Runs after a comment is created  
Parameters 4: string $post\_type, int $post\_id, int $created\_comment\_id, string $comment\_type

**dt\_filter\_post\_comments** Filter  
Modify the response before the list of comments is returned.  
Parameters 3: array $request\_body, sting $post\_type, int $post\_id

