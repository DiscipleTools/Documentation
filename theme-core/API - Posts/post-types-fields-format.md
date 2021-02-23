Fields have different types. Each type will need it's own syntax.
The list of fields will changed based on your D.T instance. For a list of available fields have a look at: the field explorer tool under Utilities in your wp-admin.

### Text
Field examples:
- title
```  
fields = [
  "title" => "John Doe" 
]
```

### boolean
Field examples:
- update_required

```
fields = [
   "update_required" => true
]
```

### key_select
Field examples:
- overall_status
- seeker_path

The key is used to set save the field instead of the value.
```
fields = [
   "overall_status" => "active"
]
```

### multi_select
Field examples:
- sources
- tags
- milestones

```
$fields = [
  "sources" => [
    "values" => [ 
      [ "value" => "web" ],  //add new, or make sure it exists
      [ "value" => "phone", "delete" => true ] //remove existing
    ],
    "force_values" => false // true will set source to the values entries. removing all others
  ]
]
```

### Contact Fields
- contact_phone
- contact_email
- contact_address
- contact_facebook
- etc

There are three actions you can take:
- Create, if you don't include a key, a new field will be created
- Update, include the key and value to update
- Delete, including the key and the delete flag will remove the Phone number

```
$fields = [
  "contact_phone" => [
    ["value" => "94 39 29 39"], //create
    ["key" => "contact_phone_123", "value" => "43 42 45 43"],  //update
    ["key" => "contact_phone_123", "delete" => true] //delete
  ] 
]
```
To change a detail on a contact method:
```
$fields = [
  "contact_phone" => [
    ["key" => "contact_phone_123", "verified" => true],  //update verified flag
  ]
]
```

### date
- baptism_date
```
$fields = [
  "baptism_date" => "2018-12-31" //format yyyy-mm-dd
]
```

### user_select
- assigned_to //int, a user id

```
$fields = [
   "assigned_to" => 4  //the id of the user
]
```

### number
- quick_button_no_answer
- quick_button_contact_established
- quick_button_meeting_scheduled
- quick_button_meeting_complete
- quick_button_no_show
```
$fields = [
  "quick_button_no_answer" => 3
]
```

### location
- location_grid
```
$fields = [
  "location_grid" => [ "values" => [ [ "value" => '100089589' ] ] ] //France
]
```

### connection
- groups
- people_groups
- baptized_by
- baptized
- coaching
- coached_by
- subassigned
- relation

Let's say our contact is connected to locations with IDs 1, 3 and 43.
This example will add the location with ID 1 and will remove the location with ID 43. The contact will then be connected to locations 1 and 3
```
$fields = [
  "locations" => [
    "values" => [ 
      [ "value" => 1 ],
      [ "value" => 43, "delete" => true ]
    ],
    "force_values" => false // true will set locations to the values entries. removing all others
  ]
]
```
This example will remove locations 1 and 3 and leave the contact connected to location 5:
```
$fields = [
  "locations" => [
    "values" => [ 
      [ "value" => 5 ],
    ],
    "force_values" => true // true will set locations to the values entries. removing all others
  ]
]
```

### post_user_meta
Meta for a post for a specific user. This meta is only accessible by the user who created it and is stored in its own table.
- reminders
```
$fields = [
  "reminders" => [
    "values" => [ 
      [ "value" => "Call again" ],
      [ "value" => "Call again", date => "2018-01-01" ], //optional date value
      [ "id" => 43, "delete" => true ] //delete user the meta id.
    ]
  ]
]
```




## Fields example together
```
$fields = [
  "title" => "Bob",
  "overall_status" => "active",
  "contact_phone" => [
    ["value" => "43 42 45 43"],
    ["value" => "94 39 29 39"]
  ],
  "locations" => [ 
    "values" => [
      [ "value" => "9" ]
    ]
  ],
  "quick_button_no_answer" => 3,
  "baptism_date" => "2017-11-34",
]
DT_Posts::create_post( 'contacts', $fields )
```