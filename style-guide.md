# Style Guide

## Branding

Please use "Disciple.Tools" or "D.T" and avoid "Disciple Tools", or "DiscipleTools" or other variants.

## Theme Colors

![#3f729b](https://via.placeholder.com/15/3f729b/000000?text=+) Main color blue: \#3f729b  
![#8BC34A](https://via.placeholder.com/15/8BC34A/000000?text=+) Secondary color: \#8BC34A  
![\#224f72](https://via.placeholder.com/15/224f72/000000?text=+) Darker blue: \#224f72  
![\#4caf50](https://via.placeholder.com/15/4caf50/000000?text=+) Success/New green: \#4caf50  
![\#00897B](https://via.placeholder.com/15/00897B/000000?text=+) Action butons: \#00897B

Status Colors  
![\#4CAF50](https://via.placeholder.com/15/4CAF50/000000?text=+) Active: \#4CAF50  
![\#FF9800](https://via.placeholder.com/15/FF9800/000000?text=+) Paused: \#FF9800  
![\#F43636](https://via.placeholder.com/15/F43636/000000?text=+) New: \#F43636  
![\#366184](https://via.placeholder.com/15/366184/000000?text=+) other: \#366184  
![\#808080](https://via.placeholder.com/15/808080/000000?text=+) Archived: \#808080  

## CSS filters for svg icons.

Add this css to an icon to change its color.

To \#3F729B ![\#3F729B](https://via.placeholder.com/15/3F729B/000000?text=+) `filter: invert(41%) sepia(42%) saturate(518%) hue-rotate(164deg) brightness(94%) contrast(100%);`

To find a good filter see [https://codepen.io/sosuke/pen/Pjoqqp](https://codepen.io/sosuke/pen/Pjoqqp)

Use the existing `dt-white-icon`,`dt-blue-icon` and`dt-green-icon` classes to quitly change an icon color.

Example: 
`<img src="settings.svg">` gives ![image](https://user-images.githubusercontent.com/24901539/134213152-5dd422c6-f6c7-411a-9289-77e6cdc32fa0.png)

`<img class="dt-blue-icon" src="settings.svg">` gives ![image](https://user-images.githubusercontent.com/24901539/134213328-1afde89c-a7ea-45cf-b5bd-6faedd371ed0.png)
