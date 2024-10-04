# JWT-Authentication-for-the-mobile-app

The mobile app plugin includes JWT authentication. Some hosting setups require additional configuration.

For full documentation [https://github.com/Tmeister/wp-api-jwt-auth/blob/develop/README.md](https://github.com/Tmeister/wp-api-jwt-auth/blob/develop/README.md)

Here is the basic usage:

## Namespace and Endpoints

When the plugin is activated, a new namespace is added.

```text
/jwt-auth/v1
```

Also, two new endpoints are added to this namespace.

| Endpoint | HTTP Verb |
| :--- | :--- |
| _/wp-json/jwt-auth/v1/token_ | POST |
| _/wp-json/jwt-auth/v1/token/validate_ | POST |

## Usage

### /wp-json/jwt-auth/v1/token

This is the entry point for the JWT Authentication.

Validates the user credentials, _username_ and _password_, and returns a token to use in a future request to the API if the authentication is correct or error if the authentication fails.

#### Sample request using AngularJS

```javascript
( function() {
  var app = angular.module( 'jwtAuth', [] );

  app.controller( 'MainController', function( $scope, $http ) {

    var apiHost = 'http://yourdomain.com/wp-json';

    $http.post( apiHost + '/jwt-auth/v1/token', {
        username: 'admin',
        password: 'password'
      } )

      .then( function( response ) {
        console.log( response.data )
      } )

      .catch( function( error ) {
        console.error( 'Error', error.data[0] );
      } );

  } );

} )();
```

Success response from the server:

```javascript
{
    "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOlwvXC9qd3QuZGV2IiwiaWF0IjoxNDM4NTcxMDUwLCJuYmYiOjE0Mzg1NzEwNTAsImV4cCI6MTQzOTE3NTg1MCwiZGF0YSI6eyJ1c2VyIjp7ImlkIjoiMSJ9fX0.YNe6AyWW4B7ZwfFE5wJ0O6qQ8QFcYizimDmBy6hCH_8",
    "user_display_name": "admin",
    "user_email": "admin@localhost.dev",
    "user_nicename": "admin"
}
```

Error response from the server:

```javascript
{
    "code": "jwt_auth_failed",
    "data": {
        "status": 403
    },
    "message": "Invalid Credentials."
}
```

Once you get the token, you must store it somewhere in your application, e.g. in a **cookie** or using **localstorage**.

From this point, you should pass this token to every API call.

Sample call using the Authorization header using AngularJS:

```javascript
app.config( function( $httpProvider ) {
  $httpProvider.interceptors.push( [ '$q', '$location', '$cookies', function( $q, $location, $cookies ) {
    return {
      'request': function( config ) {
        config.headers = config.headers || {};
        //Assume that you store the token in a cookie.
        var globals = $cookies.getObject( 'globals' ) || {};
        //If the cookie has the CurrentUser and the token
        //add the Authorization header in each request
        if ( globals.currentUser && globals.currentUser.token ) {
          config.headers.Authorization = 'Bearer ' + globals.currentUser.token;
        }
        return config;
      }
    };
  } ] );
} );
```

The **wp-api-jwt-auth** will intercept every call to the server and will look for the authorization header, if the authorization header is present, it will try to decode the token and will set the user according with the data stored in it.

If the token is valid, the API call flow will continue as always.

**Sample Headers**

```text
POST /resource HTTP/1.1
Host: server.example.com
Authorization: Bearer mF_s9.B5f-4.1JqM
```

### Errors

If the token is invalid an error will be returned. Here are some samples of errors:

**Invalid Credentials**

```javascript
[
  {
    "code": "jwt_auth_failed",
    "message": "Invalid Credentials.",
    "data": {
      "status": 403
    }
  }
]
```

**Invalid Signature**

```javascript
[
  {
    "code": "jwt_auth_invalid_token",
    "message": "Signature verification failed",
    "data": {
      "status": 403
    }
  }
]
```

**Expired Token**

```javascript
[
  {
    "code": "jwt_auth_invalid_token",
    "message": "Expired token",
    "data": {
      "status": 403
    }
  }
]
```

## Usage

Usage:
```php
$token = "token retrieved above"
$args = [
  'method' => 'GET',
  'headers' => [
      'Authorization' => 'Bearer ' . $token,
  ],
];
return wp_remote_get( 'https://example.disciple.tools/wp-json/dt-posts/v2/contacts', $args );
```

### /wp-json/jwt-auth/v1/token/validate

This is a simple helper endpoint to validate a token; you only will need to make a POST request sending the Authorization header.

Valid Token Response:

```javascript
{
  "code": "jwt_auth_valid_token",
  "data": {
    "status": 200
  }
}
```

