# Record Page Hooks

**dt\_record\_picture** Filter
Filter for adding an avatar or image for a record. Expects a URL as an output to be used in an <img tag. A provided image will be used instead of the default icon.  
Parameters 3: string $picture, string $post\_type, string $post\_id

**dt\_record\_icon** Filter
Filter for changing the icon for a record. Expects a class name pertaining to an icon in https://zurb.com/playground/foundation-icon-fonts-3  
Parameters 3: string $icon, string $post\_type, array $post\_id

**dt\_record\_top\_full\_with** Action  
Section for full width content above the details and comment tiles  
Parameters 2: string $post\_type, array $post

**dt\_record\_top\_above\_details** Action  
Section above the details tile.  
Parameters 2: string $post\_type, array $post

**dt\_details\_additional\_section** Action  
Action for displaying content within a tile  
Parameters 2: string $tile\_key, string $post\_type

**dt\_details\_additional\_tiles** Filter  
Declare other tiles to display.  
Parameters 2: array $tiles, string $post\_type

