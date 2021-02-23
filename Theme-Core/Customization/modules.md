#Post Type Modules

Modules extend the functionality of a post type like Contacts or Groups. 
A modules can be used to add: 
- Fields
- Workflows
- List filters
- Roles
- Other functionality

A module resembles what can be done through a plugin. The big difference is the instance admin can enable/disable the modules they want and the theme/plugins can package multiple modules. 

With v1.0 the D.T theme has 2 main modules available by default: the DMM module and the Access modules.  
The DMM adds fields, filters and workflows that go with: coaching, faith milestones, baptism date, baptisms etc. These are fields needed for any DMM.  
The Access module focuses more on contact followup and come with fields like the seeker path, the assigned_to and subassigned. It also adds our Follow-up filter tab on the lists page.


## Getting The Module List

```
$modules = dt_get_option( "dt_post_type_modules" );
// check if the access module is enabled
if ( empty( $modules["access_module"]["enabled"] ) ){
    return;
}
```

## How To Add A Modules

### Declaring The Module

Hook into the `dt_post_type_modules` filter.

```
add_filter( 'dt_post_type_modules', function( $modules ){
    $modules["module_key"] = [
        "name" => "Module Name",
        "enabled" => true, // default if the module is enabled. The admin's preference in the settings will take precedence.
        "prerequisites" => [ "dmm_module", "contacts_base" ], //don't load this module unless these other modules are also loaded
        "post_type" => "contacts", //the post type the module extends
        "description" => "Field and workflows for follow-up ministries" //displayed on the wp-admin settings page.
    ];
    return $modules;
}, 20, 1 );
```

### The Module Class
See dt-contacts/access-module.php as an example.

Keep in mind:
- extend `DT_Module_Base`.
- declare the $post_type and $module public variables.
- call `self::check_enabled_and_prerequisites()` to only load if:
  - the module is enabled in the settings.
  - the prerequisites are also enabled.

```
class DT_Contacts_Access extends DT_Module_Base {
    public $post_type = "contacts";
    public $module = "access_module";

    public function __construct(){
        parent::__construct();
        if ( !self::check_enabled_and_prerequisites() ){
            return;
        }
        //your filters
    }
    
    //your functions
}
```