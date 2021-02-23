# Users

## Get My User Info

`Get` https://example.com/wp-json/dt/v1/user/my

### Parameters

### Returns
```
[ 
    "ID": 1,
    "user_email": "user@example.com",
    "display_name": "BOB JOE",
    "locale": "fr_FR"
]
```

## Update My User Details

`POST` https://example.com/wp-json/dt/v1/user/update

### Parameters
- **locale** (string) optional. The new user locale

### Returns
`true` on success. WP_ERROR if not

## List Users

`Get` https://example.com/wp-json/dt/v1/users/get_users

### Parameters
- **s** (string) optional. Search user display names
- **get_all** (string) optional. Return all the users. Default false.  "1" for true

### Returns
```
[ 
    "ID": 1,
    "name": "BOB JOE",
    "avatar": "http://2.gravatar.com/avatar/x?s=16&d=mm&r=g"
]
```