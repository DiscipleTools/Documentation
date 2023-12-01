# Gulp - CSS and JS

## Setting Up the Build Process

D.T Uses gulp to compile and minify the css and javascript. If you will be contributing styling or JS changes you will need to use gulp.

* First you need to have Node.js installed on your computer. You can download and install Node.js from [here](https://nodejs.org/)
* Second from your terminal enter the Disciple Tools theme folder.
* From your Disciple Tools theme folder run npm install. You should only have to do this once.
* Once the install process is complete you should be able to type `gulp` in the command line and see an output that looks something like
```
[15:09:08] Using gulpfile /wp-content/themes/disciple-tools-theme/gulpfile.js
[15:09:08] Starting 'default'...
[15:09:08] Starting 'styles'...
[15:09:08] Starting 'scripts'...
[15:09:15] Finished 'scripts' after 7.14 s
[15:09:16] Finished 'styles' after 8.02 s
[15:09:16] Finished 'default' after 8.02 s
```
* If you will making multiple changes to css or js files you will probably not want to have to run gulp after every change. In this case you can use the command `gulp watch` and gulp will watch for any changes to scss or js files and will automatically run when the file is changed.

## CSS

D.T uses SCSS for CSS styiling. The SCSS files can be found under `dt-assets > scss.`

You probably want to modify:

* `_details.scss` for contact, group etc record page
* `_list.scss` for the list page
* `_main.scss` most other cases

Compile your changes to css by running `gulp` in your terminal in the theme root.  
This generates the `dt-assets/build/css/style.min.css` file that is used by the browser

## JS

If you modify `dt-assets/js/footer-scripts.js` you will also need to run `gulp` to apply the changes.  
The outpet is `dt-assets/build/js/scripts.min.js`

