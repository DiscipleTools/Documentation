# Posts in Typeaheads

`GET` [https://example.com/wp-json/dt-posts/v2/{post\_type}/compact/](https://example.com/wp-json/dt-posts/v2/{post_type}/compact/)

Requires permission: `access_{post_type}`

## Parameters

* `s` \(string\): the string to filter the list to.  Or the id of the target record

## Returns

```text
{
  posts: [
   {
     ID : 1,
     name: 'Bob',
     user: 432, //if the record corresponds to a user, only useful for contacts
     status: active //the overall status, only if the record is a contact
   },
   { ... post2 ... }
  ], 
  total: 339 // the total number of posts matching the search
}
```

