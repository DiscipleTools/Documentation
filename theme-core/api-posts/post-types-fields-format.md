# Fields Format

Fields have different types. Each type will need it's own syntax. The list of fields will changed based on your D.T instance. For a list of available fields have a look at: the field explorer tool under Utilities in your wp-admin.

## text

Field examples:

* title

```php
fields = [
  "title" => "John Doe" 
]
```

## boolean

Field examples:

* update\_required

```php
fields = [
   "update_required" => true
]
```

## key\_select

Field examples:

* overall\_status
* seeker\_path

The key is used to set save the field instead of the value.

```php
fields = [
   "overall_status" => "active"
]
```

## multi\_select

Field examples:

* sources
* milestones

```php
$fields = [
  "sources" => [
    "values" => [ 
      [ "value" => "web" ],  //set a value, the value must be predefined in the field options
      [ "value" => "phone", "delete" => true ] //remove existing
    ],
    "force_values" => false // true will set source to the values entries. removing all others
  ]
]
```

## tags

Field examples:

* tags

Functions just like `multi_select`, but without requiring a pre-defined list of values.

```php
$fields = [
  "tags" => [
    "values" => [ 
      [ "value" => "web" ],
      [ "value" => "phone", "delete" => true ] //remove existing
    ],
    "force_values" => false // true will set tags to the values entries. removing all others
  ]
]
```

## communication\_channel

* contact\_phone
* contact\_email
* contact\_address
* contact\_facebook
* etc

Note: The field name must start with `contact_`

There are three actions you can take:

* Create, if you don't include a key, a new field will be created
* Update, include the key and value to update
* Delete, including the key and the delete flag will remove the Phone number

```php
$fields = [
  "contact_phone" => [
    ["value" => "94 39 29 39"], //create
    ["key" => "contact_phone_123", "value" => "43 42 45 43"],  //update
    ["key" => "contact_phone_123", "delete" => true] //delete
  ] 
]
```

To change a detail on a contact method:

```php
$fields = [
  "contact_phone" => [
    ["key" => "contact_phone_123", "verified" => true],  //update verified flag
  ]
]
```

## date

* baptism\_date

```php
$fields = [
  "baptism_date" => "2018-12-31" //format yyyy-mm-dd
]
```

## user\_select

* assigned\_to //int, a user id

```php
$fields = [
   "assigned_to" => 4  //the id of the user
]
```

## number

* quick\_button\_no\_answer
* quick\_button\_contact\_established
* quick\_button\_meeting\_scheduled
* quick\_button\_meeting\_complete
* quick\_button\_no\_show

```php
$fields = [
  "quick_button_no_answer" => 3
]
```

If the number is greater than the max_option or less than the min_option for this field, an error will be returned

## location

* location\_grid

```php
$fields = [
  "location_grid" => [ "values" => [ [ "value" => '100089589' ] ] ] //France
]
```

## connection

* groups
* people\_groups
* baptized\_by
* baptized
* coaching
* coached\_by
* subassigned
* relation

Let's say our contact is connected to groups with IDs 1, 3 and 43. This example will add the group with ID 1 and will remove the group with ID 43. The contact will then be connected to group 1 and 3

```php
$fields = [
  "groups" => [
    "values" => [ 
      [ "value" => 1 ],
      [ "value" => 43, "delete" => true ]
    ],
    "force_values" => false // true will set groups to the values entries. removing all others
  ]
]
```

This example will remove groups 1 and 3 and leave the contact connected to group 5:

```php
$fields = [
  "groups" => [
    "values" => [ 
      [ "value" => 5 ],
    ],
    "force_values" => true // true will set groups to the values entries. removing all others
  ]
]
```

### connection meta
Add meta data when creating or updating a connection value. Here we add the role and date meta to the group member.

```php
$fields = [
  "groups" => [
    "values" => [ 
      [ 
        "value" => 5,
        "meta" => [
          "role" => "treasurer",
          "date" => time()
        ]
      ],
    ],
  ]
]
```
Use the same syntax for creating or updating a connection. To delete a connection meta send an empty string:
```php
$fields = [
  "groups" => [
    "values" => [ 
      [ 
        "value" => 5,
        "meta" => [
          "role" => "",
          "date" => ""
        ]
      ],
    ],
  ]
]
```

### Creating a post from a connection field
Example: Cantact A baptized someone (not yet a contact in the system). We can use the `additional_meta` parameter to create the new contact and set the `baptized_by` field by passing in the `baptized` connection field key. When creating the new contact, the API with translate `baptized` to `baptized_by` and set the new contact to be baptized by Contact A.

```php
$fields = [
  "additional_meta": [
    "created_from": 45, //the id of the existing record you want use in the connection
    "add_connection": "baptized", //the connection field where the new record is created from
  ]
]
```


## post\_user\_meta

Meta for a post for a specific user. This meta is only accessible by the user who created it and is stored in its own table.

* reminders

```php
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

```php
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

