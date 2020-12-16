
# Adding menu navigation links

```
// Hook for adding a menu item to the desktop view
add_filter( 'desktop_navbar_menu_options', 'add_navigation_links', 35 );

// Hook for adding a menu item to the desktop view
add_filter( 'off_canvas_menu_options', 'add_navigation_links', 35);



function add_navigation_links( $tabs ) {
    //check user permissions
    if ( current_user_can( 'access_' . $this->post_type ) ) {
    
        $tabs[] = [
            "link" => site_url( "/awesome_page/" ), // the link where the user will be directed when they click
            "label" => __( "Awesome Page", "disciple_tools" )  // the label the user will see
        ];
        
    }
    return $tabs;
}
```
