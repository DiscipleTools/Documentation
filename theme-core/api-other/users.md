# Users

## Get My User Info

`Get` [https://example.com/wp-json/dt/v1/user/my](https://example.com/wp-json/dt/v1/user/my)

### Parameters

### Returns

```php
[
    "ID": 1,
    "user_email": "user@example.com",
    "display_name": "BOB JOE",
    "locale": "fr_FR",
    "locations": {
      "location_grid": [],
      "location_grid_meta": []
    },
    "apps": [
      {
        "description": "An update summary of assigned contacts.",
        "label": "User Contact Updates",
        "link": "http://...."
      }
    ],
    "notifications": {
      "email_preference": {
        "daily": false,
        "hourly": false,
        "realtime": true
      },
      "follow_all": false,
      "notify_types": [
        {
          "channels": [
            {
              "enabled": true,
              "key": "email",
              "label": "Email"
            },
            {
              "enabled": true,
              "key": "web",
              "label": "Web"
            },
            {
              "enabled": false,
              "key": "push_notifications",
              "label": "Push Notifications"
            }
          ],
          "key": "new_assigned",
          "label": "Newly Assigned Contact"
        }
      ]
    },
    "preferences": {
      "languages": [
        {
          "key": "fr",
          "label": "French"
        }
      ]
    },
    "profile": {
      "ID": 1,
      "address": [],
      "bio": "This has been my journey so far....",
      "display_name": "admin",
      "email": [
        {
          "label": "admin@dtdev.local",
          "value": "admin@dtdev.local"
        }
      ],
      "gender": "male",
      "language": "English (United States)",
      "locale": "en_US",
      "locations": {
        "location_grid": [],
        "location_grid_meta": []
      },
      "name": "Administrator",
      "nickname": "admin",
      "other": [],
      "phone": [],
      "roles": {
        "administrator": "Administrator"
      },
      "social": [],
      "username": "admin"
    },
    "unavailability": [
      {
        "id": 1,
        "start_date": "2022-06-13",
        "end_date": "2022-06-17"
      },
      {
        "id": 2,
        "start_date": "2022-06-20",
        "end_date": "2022-06-24"
      }
    ]
]
```

## Update My User Details

`POST` [https://example.com/wp-json/dt/v1/user/update](https://example.com/wp-json/dt/v1/user/update)

### Parameters

* **locale** \(string\) optional. The new user locale

### Returns

`true` on success. WP\_ERROR if not

## List Users

`Get` [https://example.com/wp-json/dt/v1/users/get\_users](https://example.com/wp-json/dt/v1/users/get_users)

### Parameters

* **s** \(string\) optional. Search user display names
* **get\_all** \(string\) optional. Return all the users. Default false.  "1" for true

### Returns

```php
[
    "ID": 1,
    "name": "BOB JOE",
    "avatar": "http://2.gravatar.com/avatar/x?s=16&d=mm&r=g"
]
```
