# How to Add Plugin Notification Channels

Custom plugins have the ability to integrate with D.T's Site Notifications Framework; providing additional channel options across the following notification types:

- Newly Assigned Contact
- @Mentions
- New Comments
- Update Needed
- Contact Info Changed
- Contact Milestones and Group Health metrics


## Assigning Custom Channels to Notification Types

In order to assign custom plugin channels to existing notification types, you will need to hook into the `dt_get_site_notification_options` filter, with code to specify new channel and registering with available types. 

A typical filter function, is provided within the code snippet below.

```php
add_filter( 'dt_get_site_notification_options', 'dt_get_site_notification_options', 10, 1 );
public static function dt_get_site_notification_options( $notifications ){
    if ( !isset( $notifications['channels']['channel-x'] ) ) {
        $notifications['channels']['channel-x'] = [
            'label' => __( 'Channel X', 'disciple_tools' )
        ];
        foreach ( $notifications['types'] as $type_key => $type_value ){
            $notifications['types'][$type_key]['channel-x'] = false;
        }
    }
    return $notifications;
}
```

- **notifications**: Array containing site `channels` and `types` to be updated with custom plugin channel information.



## Publish Custom Channel IDs

Registering with the `dt_communication_channels` filter hook, enables custom channels to be published with the wider system and detected during the dispatching of notifications.

```php
add_filter( 'dt_communication_channels', 'dt_communication_channels', 10, 1 );
function dt_communication_channels( $channels ) {
    if ( empty( $channels ) ) {
        $channels = [];
    }
    $channels[] = 'channel-x';

    return $channels;
}
```

- **channels**: Array containing registered system notification ids.



## Detecting channel Notifications

To detect channel notifications, you would need to register with the `dt_communication_channels_notification` action hook; which is executed following a send notification on channel requests.

```php
add_action( 'dt_communication_channels_notification', 'dt_communication_channels_notification', 10, 4 );
function dt_communication_channels_notification( $channel, $user_id, $notification, $args = [] ) {
    if ( in_array( $channel, [ 'channel-x' ] ) && isset( $user_id, $notification, $notification['notification_note'] ) ){
        // TODO: Channel Specific Execution Code
    }
}
```

- **channel**: String channel id; E.g: `channel-x`
- **user_id**: Recipient user id.
- **notification**: D.T. notification array bundle, typically containing the following:
    - user_id
    - source_user_id
    - post_id
    - secondary_item_id
    - notification_name
    - notification_action
    - notification_note
    - date_notified
    - is_new
    - field_key
    - field_value
    - channels
- **args**: Array containing additional processing parameters:
    - notification_type
    - already_sent



