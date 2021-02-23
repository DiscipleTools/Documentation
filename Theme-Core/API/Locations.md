# Changes
Locations appear as the `location_grid` field on contacts and groups.
The old `locations` field has been removed.

`location_grid` is a field of type 'location'. It is updated the same way connections are. See [Post Types Fields Format](https://github.com/DiscipleTools/disciple-tools-theme/wiki/Post-Types-Fields-Format) for more details


# Endpoints

## Search Locations
`GET` https://example.com/wp-json/dt/v1/mapping_module/search_location_grid_by_name

Requires permission: `access_{post_type}`

### Parameters
* `s` (string): the string to filter the list to.
* `filter` (string): Options: `[ 'all' | 'focus' | 'used' ]`
  * `all`: return all geoname locations
  * `focus`: Anly return the locations included in the selected Mapping Focus
  * `used`: Only return locations currently used by contacts, groups (and other)

### Returns
```
{
  location_grid: [
   {
     ID : 6255147,
     name: 'Asia',
   },
   { ... location_grid_id 2 ... }
  ], 
  total: 339 // the total number of location_grid_ids matching the search
}
```