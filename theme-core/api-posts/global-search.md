# Global Search

## Advanced Search

`Get` [https://example.com/wp-json/dt-posts/v2/posts/search/advanced_search](https://example.com/wp-json/dt-posts/v2/posts/search/advanced_search)

### Parameters

* **query** \(string\) mandatory. URI encoded search query.
* **post_type** \(string\) mandatory. Post type name to be searched. Set to `all` for multiple post type searches.
* **offset** \(int\) mandatory. How many initial search result hits to skip \(for load more operations\). Set to `0` as default.

### Returns

```text
{
   hits: (array) An array of result hits. See below for format.
   total_hits: (int) the number of result hits in total.
}
```

Result hits format:

```javascript
[
  {
    "post_type":"contacts",
    "posts":[
      "ID": "56",
      "post_title": "Ali XYZ",
      "post_type": "contacts",
      "post_date": "2018-05-29 14:19:36",
      "post_hit": "N", //post hit type indicator (Y/N)
      "comment_hit": "Y", //comment hit type indicator (Y/N)
      "meta_hit": "N", //meta hit type indicator (Y/N)
      "comment_hit_content": "Wow! He is willing to meet today!",
      "meta_hit_value": ""
    ],
    "total": 1,
    "offset": 2 //current offset value for result post type
  },
  {
    ...hit2...
  }
]
```
