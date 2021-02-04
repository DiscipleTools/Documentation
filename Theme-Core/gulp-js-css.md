# CSS

D.T uses SCSS for CSS styiling.
The SCSS files can be found under `dt-assets > scss.`

You probably want to modify:
- `_details.scss` for contact, group etc record page
- `_list.scss` for the list page
- `_main.scss` most other cases

Compile your changes to css by running `gulp` in your terminal in the theme root.  
This generates the `dt-assets/build/css/style.min.css` file that is used by the browser

**Note**: if you haven't already you will need to run `npm install` to install gulp and other needed packages.


# JS
If you modify `dt-assets/js/footer-scripts.js` you will also need to run `gulp` to apply the changes.  
The outpet is `dt-assets/build/js/scripts.min.js`
