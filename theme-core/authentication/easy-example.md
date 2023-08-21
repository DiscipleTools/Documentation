## Easy Webform Create Contact Example

### Create a "Token" Site Link.

![image](https://github.com/DiscipleTools/Documentation/assets/24901539/0c92e588-974c-46e1-8f8e-97c5dccb9759)

Notes:

- Site 1: Your D.T instance
- Site 2: Where you expect the webform to be used. It can be any url is this is not verified).
- Connection Type: At leate "Create Contact" to give the permision needed.
- Use Token As API KEY: This is required to keep the Authentication simple.

### Create a Contact

Create a Post Request to your instance

`POST`: `https://example.disciple.tools/wp-json/dt-posts/v2/contacts`

Use the site key in the Authorization header 
`Authorization: Bearer 14c5f0f1ebbc3c4b1042e884c1cf4e04410e274198928197c9ae726cbbe15b19`


Usage:
```php
$token = "token from the Site to Site link"
$args = [
  'method' => 'POST',
  'body' => $fields,
  'headers' => [
      'Authorization' => 'Bearer ' . $token,
  ],
];
return wp_remote_post( 'https://example.disciple.tools/wp-json/dt-posts/v2/contacts', $args );
```

$fields need to be in the format specified in [Fields Format](theme-core/api-posts/post-types-fields-format.md)
