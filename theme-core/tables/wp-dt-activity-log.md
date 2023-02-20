## [ wp_dt_activity_log ]


D.T custom table; which captures a wide array of system events, such as field updates.


### Field Update Events

The following field types are currently captured:

- text:
```php
(
    [action] => field_update
    [object_type] => contacts
    [object_subtype] => nickname
    [object_id] => 536
    [object_name] => MAKE Contact
    [meta_id] => 8604
    [meta_key] => nickname
    [meta_value] => MAKE Stuff Pls
    [meta_parent] => unknown
    [object_note] => Nickname changed from "MAKE Stuff" to "MAKE Stuff Pls"
    [old_value] => MAKE Stuff
    [field_type] => text
)
```

- date:
```php
(
    [action] => field_update
    [object_type] => contacts
    [object_subtype] => baptism_date
    [object_id] => 536
    [object_name] => MAKE Contact
    [meta_id] => 8667
    [meta_key] => baptism_date
    [meta_value] => 1673395200
    [meta_parent] => unknown
    [object_note] => Added Baptism Date: 1673395200
    [old_value] => 
    [field_type] => date
)
```

- key_select:
```php
 (
     [action] => field_update
     [object_type] => contacts
     [object_subtype] => gender
     [object_id] => 536
     [object_name] => MAKE Contact
     [meta_id] => 8668
     [meta_key] => gender
     [meta_value] => male
     [meta_parent] => unknown
     [object_note] => Added Gender: Male
     [old_value] => 
     [field_type] => key_select
 )
```

- multi_select:
```php
 (
     [action] => field_update
     [object_type] => contacts
     [object_subtype] => milestones
     [object_id] => 536
     [object_name] => MAKE Contact
     [meta_id] => 8669
     [meta_key] => milestones
     [meta_value] => milestone_has_bible
     [meta_parent] => unknown
     [object_note] => Added Faith Milestones: Has Bible
     [old_value] => 
     [field_type] => multi_select
 )
```

- connection:
```php
(
     [action] => connected to
     [object_type] => contacts
     [object_subtype] => connection
     [object_id] => 536
     [object_name] => MAKE Contact
     [meta_id] => 572
     [meta_key] => contacts_to_groups
     [meta_value] => 317
     [meta_parent] => 
     [object_note] => 
     [field_type] => connection from
 )
 (
     [action] => connected to
     [object_type] => groups
     [object_subtype] => connection
     [object_id] => 317
     [object_name] => Metric Group
     [meta_id] => 572
     [meta_key] => contacts_to_groups
     [meta_value] => 536
     [meta_parent] => 
     [object_note] => 
     [field_type] => connection to
 )
```

- number:
```php
(
     [action] => field_update
     [object_type] => contacts
     [object_subtype] => number_test
     [object_id] => 536
     [object_name] => MAKE Contact
     [meta_id] => 8671
     [meta_key] => number_test
     [meta_value] => 5
     [meta_parent] => unknown
     [object_note] => Added Number field: 5
     [old_value] => 
     [field_type] => number
 )
```

- communication_channel:
```php
(
     [action] => field_update
     [object_type] => contacts
     [object_subtype] => contact_other_c8a
     [object_id] => 536
     [object_name] => MAKE Contact
     [meta_id] => 8682
     [meta_key] => contact_other_c8a
     [meta_value] => @other3
     [meta_parent] => unknown
     [object_note] => Added contact_other_c8a: @other3
     [old_value] => 
     [field_type] => communication_channel
 )
 (
     [action] => field_update
     [object_type] => contacts
     [object_subtype] => contact_other_c8a_details
     [object_id] => 536
     [object_name] => MAKE Contact
     [meta_id] => 8683
     [meta_key] => contact_other_c8a_details
     [meta_value] => a:1:{s:8:"verified";b:0;}
     [meta_parent] => unknown
     [object_note] => contact_other_c8a "@other3" not verified
     [old_value] => 
     [field_type] => details
 )
```

- tags:
```php
(
     [action] => field_update
     [object_type] => contacts
     [object_subtype] => tags_test
     [object_id] => 536
     [object_name] => MAKE Contact
     [meta_id] => 8674
     [meta_key] => tags_test
     [meta_value] => random
     [meta_parent] => unknown
     [object_note] => Added Random Tags: random
     [old_value] => 
     [field_type] => tags
 )
```

- user_select:
```php
(
     [action] => field_update
     [object_type] => contacts
     [object_subtype] => user_select_test
     [object_id] => 536
     [object_name] => MAKE Contact
     [meta_id] => 8675
     [meta_key] => user_select_test
     [meta_value] => user-12
     [meta_parent] => unknown
     [object_note] => Added User Select: user-12
     [old_value] => 
     [field_type] => user_select
 )
```

- location:
```php
(
     [action] => field_update
     [object_type] => contacts
     [object_subtype] => location_grid
     [object_id] => 536
     [object_name] => MAKE Contact
     [meta_id] => 8676
     [meta_key] => location_grid
     [meta_value] => 100134548
     [meta_parent] => unknown
     [object_note] => Added Locations: 100134548
     [old_value] => 
     [field_type] => location
 )
```

- location_meta:
```php
(
     [action] => field_update
     [object_type] => contacts
     [object_subtype] => location_grid_meta
     [object_id] => 536
     [object_name] => MAKE Contact
     [meta_id] => 8677
     [meta_key] => location_grid_meta
     [meta_value] => 123
     [meta_parent] => unknown
     [object_note] => Hungary
     [old_value] => 
     [field_type] => location_meta
 )
```