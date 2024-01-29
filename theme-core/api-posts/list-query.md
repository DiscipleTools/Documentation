# List Query

## Get a list of contacts, groups or another post type, with filtering and sorting parameters

## Endpoint

`GET` [https://example.com/wp-json/dt-posts/v2/{post\_type}/](https://example.com/wp-json/dt-posts/v2/{post_type}/)

## Parameters

**sort** \(string\)

* Options:
  * name //name or title of the record
  * post\_date //creation date of the record
  * any field\_key

Add a `-` before any of these options to return them in descending order

Example:

```javascript
// get records assigned to me, ordered by creation date from newest to oldest
let searchParameters = {
  assigned_to: [ 'me' ],
  sort: `-post_date`
}
```

### `user_select`

Parameters: \(array\) of presets or ids.

* `me` // records assigned to the user making the query
* `83` // records assigned to user of ID 83
* `-84` // exclude records assigned to user 84

Example:

```javascript
// get records assigned to me
let searchParameters = {
  assigned_to: [ 'me' ]
}
// get records assigned_to user 22 and user 48
let searchParameters = {
  assigned_to: [ 22 ]
}
```

### `key_select`, `multi_select`, `tags`

Parameters: \(array\) of keys.

* overall\_stats \(key\_select\)
* milestones \(mutli\_select\)
* gender \(key\_select\)
* tags \(tags\)
* etc

Example:

```javascript
// get contacts that have the 'Has Bible' or 'Reading Bible' milestones and that are at the 'Meeting Scheduled' stage.
let searchParameters = {
  milestones: [ 'milestone_has_bible', 'milestone_reading_bible' ],
  seeker_path: [ 'scheduled' ],
  tags: [ 'open' ]
}
```

```javascript
// get contacts that have the 'Has Bible' milestone but not the 'Reading Bible' milestone.
let searchParameters = {
  milestones: [ 'milestone_has_bible', '-milestone_reading_bible' ],
}
```

### `connection`

Parameters \(array\) of IDs

* subassigned
* groups
* etc

Example:

```javascript
// get contacts subassigned to contact 93. Exclude contacts subassigned to contact 23
let searchParameters = {
  subassinged: [ 93, -23 ]
}
```

Example:

```javascript
// get contacts assigned_to user 22 **OR** subassigned to contact 93
let searchParameters = {
  [ assigned_to => [ 22 ], subassinged: [ 93 ] ]
}
```

Example:

```javascript
// get contacts with no groups connected
let searchParameters = {
   groups: [] 
}
```

Example:

```javascript
// get all contact with any connected group
let searchParameters = {
   groups: [*] 
}
```


### `location`

Parameters: \(array\) of location\_grid IDs

* location\_grid

Example:

```javascript
// get contacts in location with location_grid (in the dt_location_grid table grid_id) id 123456
// but exclude location 5678
let searchParameters = {
  location_grid: [ 123456, -5678 ]
}
```

#### `date`

Parameters: **start** and **end**

* created\_on // date the record was created
* baptism\_date
* etc

Example:

```javascript
// get the records created between in 2018
let searchParameters = {
  created_on : {
    start: "2018-01-01",
    end: "2019-01-01"
  }
}
// get contacts baptized before Feb 2019
let searchParameters = {
  baptism_date : {
    end: "2019-02-01"
  }
}
```

### `boolean`

Parameters \(array\). "1" for true, "0" for false

* requires\_update
* etc

Example:

```javascript
// get records that need an update
let searchParameters = {
  requires_update: [ "1" ]
}
```

### `number`

Parameters \(array\):

* **operator** options: `<`, `>`, `<=`, `>=` or `=`
* **number**

Field examples:

* baptism\_generations
* quick actions

Example:

```javascript
// get records that are baptism generation greater than 4
let searchParameters = {
  baptism_generation => [ "operator" => ">", "number" => 4 ],
}
```

### `text` `communication_channel`

Parameters: \(array\) or text to search for.

* contact\_phone
* name
* nickname
* etc

Examples:

```javascript
// search phone numbers matching 123 anywhere in the number
let searchParameters = {
  contact_phone: ["123"]
}

// search phone numbers matching 123 exactly
let searchParameters = {
  contact_phone: ["^123"]
}

// search phone numbers matching 123 but don't match 234
let searchParameters = {
  contact_phone: ["123", "-234"]
}

// search for records with no phone numbers
let searchParameters = {
  contact_phone: ["123"]
}
```

### Search Parameters

**text** \(string\) searches contact or group names/titles and contact information \(email, phone etc\)

Example:

```javascript
// search records with values matching "Bob" anywhere within the name field
let searchParameters = {
  name: ["Bob"]
}

// search records for names matching "Bob" exactly
let searchParameters = {
  name: ["^Bob"]
}

// search records for names; which do not match "Bob"
let searchParameters = {
  name: ["-Bob"]
}

// search records for any names
let searchParameters = {
  name: ["*"]
}

// search for records with no names set
let searchParameters = {
  name: []
}
```

### Combining with AND/OR logic

Wrapping parameters in arrays with switch add AND/OR logic. The first level of values has AND logic. Wrapping them in an array gives them an OR logic. 1st layer: AND 2nd layer: OR 3rd layer: AND etc

Note that the query is sent in the fields array and thath the structure is a bit different.

Examples:

```javascript
// records that are of field `type` `personal` AND coached by me
let searchParameters = {
  fields: [
    {
      type: ["personal"],  
    },
    // AND
    {
      coached_by: [ "me" ]
    }
  ],
  sort: "name"
}
```

```javascript
// records that are of type "personal" OR coached by me
let searchParameters = {
  fields: [
    {
      type: ["personal"],
      //OR
      coached_by: [ "me" ]
    }
  ],
  sort: "name"
}
```

```javascript
// records that are ( ( type "personal" AND coached_by me ) OR ( assigned to me and active ) ) AND shared with me
let searchParameters = {
  fields: [

    [

      {
        type: ["personal"],
        // AND
        coached_by: [ "me" ]
      },
      // OR
      {
        assigned_to: [ "me" ],
        //AND
        overall_status: [ "active" ]
      }
    ],
    //AND
    {
      shared_with: [ "me" ]
    }
}
```

### Recently viewed posts

**dt\_recent** \(bool\) true. Cannot be combined with other parameters except: **fields\_to\_return**

Example:

```javascript
//Get the 30 most recently viewed posts by the user making the request.
let searchParameters = {
  dt_recent: true
}
```

### Paging Parameters

**offset** \(integer\) the number of records to skip. Optional. **limit** \(integer\) the number of records to include in the response. Default is 100, Maximum: 1000. Warning: a large number may cause a server memory error. Optional.

Example:

```javascript
// get second page of records with each page having 100.
let searchParameters = {
  offset: 100,
  limit: 100
}
```

### Specifying and limiting returned fields

**fields\_to\_return** \(array\) the fields to return. Optional.

Example:

```javascript
let searchParameters = {
  fields_to_return: [ 'group_status', 'group_type', 'member_count', 'leaders', 'location_grid', 'last_modified', 'requires_updated' ]
}
```

## Bringing it all together

After building the filter parameters, we need to transform the searchParameters object in the query parameters string. The query string needs to be the same format that jQuery.param\(\) outputs. See [here](https://stackoverflow.com/questions/22582795/jquery-param-alternative-for-javascript) for a plain js alternative

```javascript
let searchParameters = {
  overall_status: ["active", "-closed"] // -closed filters out the closed records
  seeker_path: ["none"]
  sort: "post_date"
  sources: ["instagram"]
}

let queryParametersString = jQuery.param(searchParameters)
// this gives a string that looks like this:
// seeker_path%5B%5D=none&overall_status%5B%5D=active&overall_status%5B%5D=-closed&sources%5B%5D=instagram&sort=post_date

//query away with:
let queryString = `https://example.com/wp-json/dt-posts/v2/contacts/?${queryParametersString}`;
```

### Returns

```javascript
//for contacts
{
  posts: [
   { ... contact1 ... },
   { ... contact2 ... }
  ],
  total: 339 // the total number of contacts available to page (see offset)
}
//for groups
{
  posts: [
   { ... group1 ... },
   { ... group2 ... }
  ],
  total: 34 // the total number of groups available to page (see offset)
}
```
