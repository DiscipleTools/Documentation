### Public settings

Filter `dt_core_public_endpoint_settings`, in D.T v1.0.7  
Expose settings publicly to world.
To not use unless it is for setting that must be accessed before the user is logged in.
Settings are available at https://dt-instance/wp-json/dt-public/dt-core/v1/settings


Usage example:
```
add_filter( "dt_core_public_endpoint_settings", function ( $settings ){
    $settings["login_settings"]["google"] = [ "login_url" => "https://google.com/login?redirect=https://dt-instance.com/wp-json/google-auth" ];
    return $settings;
} );
```
