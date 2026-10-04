236 T. P. Fowdar, L. Babooram, M. U-D-Ibn Nazir Rosun and M. Indoondonman

6. Double click on the kmeans_image.js file and add the codes in Listitng 3.68 to it. These codes are based on the example given in [63].

# Listing 3.68. The kmeans_image.js file for clustering

```
// Array variable for holding the data from the dataset.
var data = new Array();

// Upon clicking the 'Browse' button, a document browser opens and allows the
//selection of several images at a time. When the 'Open' button is clicked on the
//document browser, the loadImages() function is invoked and the selected
//images are displayed on the HTML page [63].

function loadImages() {
  reset();
}
// The function iterates through all the files that have been selected, and
//displays the images in a sequential order in a <div> tag with 'img' as its id.

for (var i = 0; i < imagefile.files.length; i++) {
  var fileReader = new FileReader();

  // Prepare a callback for onload = function(e) of the end of fileread operation [63];

  fileReader.onload = function(e) {
    var imageData = new Uint8Array(e.target.result);
    var blob = new Blob([imageData], {
      type: "image/jpeg"
    });
    var url = URL.createObjectURL(blob);

    var img = new Image();
    img.onload = function() {


// Draw the image on the canvas while reducing its resolution to 4x4 pixels [63]

var context = canvas.getContext("2d");

if (img.width > img.height) {
  context.drawImage(img, 0, 0, img.width, img.height, 0, 0, canvas.width,
```