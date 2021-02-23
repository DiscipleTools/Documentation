# Site-to-Site-Link

To authenticate with D.T from another server.

### Creating the token

Go to the wp-admin. Open **Site Links** in the menu on the left. Click the **Add New** button.

In **Site 1** add the D.T domain. Example: example.disciple.tools

In **Site 2** add the remote server's. Example: example.com

note: both domains need to be HTTPS. You can disable this for local testing by commenting this out [here](https://github.com/DiscipleTools/disciple-tools-theme/blob/683924b5d417a9d901e78cfb609d1c126972c459/dt-core/admin/site-link-post-type.php#L204).

**Connection type**: You will create a connection type and associate permissions to it. See below.

Since you are not connecting to another D.T instance, under **DT Site** choose 'No, connection for a non-Disciple Tools system.'.

### Remote authentication

We'll use the token and the 2 domains we just defined to authenticate with D.T form another server.

Here are example for creating a contact. Note we are not using the endpoints that include "dt\_public" in the url. Those most likely will not work.

PHP Example

```php
function create_contact( $fields ) {
  $token = "token from the Site to Site link";
  $site_key = md5($token . "example.disciple.tools" . "example.com");
  $transfer_token = md5($site_key . date('Y-m-dH'));

  $url = 'https://example.disciple.tools/wp-json/dt/v1/contact/create';
  $req = curl_init();
  curl_setopt_array($req, array(
    CURLOPT_URL => $url,
    CURLOPT_RETURNTRANSFER => true,
    CURLOPT_CUSTOMREQUEST => 'POST',
    CURLOPT_POSTFIELDS => json_encode($fields),
    CURLOPT_HTTPHEADER => array(
      "Content-Type: application/json",
      "cache-control: no-cache",
      "Authorization: Bearer " . $transfer_token
    ),
  ));

  $response = curl_exec($req);
  return json_decode($response);
}
```

Wordpress Example

```php
function create_contact( $fields ){
  $token = "token from the Site to Site link"
  $site_key = md5( $token . "example.disciple.tools" . "example.com" );
  $transfer_token = md5( $site_key . current_time( 'Y-m-dH', 1 ) );
  $args = [
    'method' => 'POST',
    'body' => $fields,
    'headers' => [
        'Authorization' => 'Bearer ' . $transfer_token,
    ],
  ];
  return wp_remote_post( 'https://example.disciple.tools/wp-json/dt/v1/contact/create', $args );
}
```

Node example

```js
import moment from 'moment'
import request from "request-promise"
let CryptoJS = require('crypto-js')

create_contact = (fields)=>{
  let token = "token from the Site to Site link"
  let key =  CryptoJS.MD5(token + "example.disciple.tools" + "example.com")
  let date = moment().utc().format("Y-MM-DDHH")
  let transfer_token = CryptoJS.MD5(key + date).toString()

  let options = {
    method: "POST",
    uri: 'https://example.disciple.tools/wp-json/dt/v1/contact/create',
    body: fields,
    headers: {
      Authorization: 'Bearer ' + transfer_token
    },
    json: true
  }

  return request(options)
}
```

## Connection Types

Here is how you add a connection type and the right permissions from you D.T plugin.

For a list of permissions see \[\[Permissions\]\]. In the `site_link_capabilities` function you can add your own permission that you use later on in your plugin.

```php
add_filter( 'site_link_type', 'site_link_type', 10, 1 );
add_filter( 'site_link_type_capabilities', 'site_link_capabilities', 10, 1 );

function site_link_type( $types ){
    if ( !isset( $types["connection_to_system_x"] ) ){
        $types["connection_to_system_x"] = "Connection to System X";
    }
    return $types;
}
function site_link_capabilities( $args ){
    if ( $args['connection_type'] === "connection_to_system_x" ){
         $args['capabilities'][] = 'view_x_metrics';
    }
    return $args;
}
```
