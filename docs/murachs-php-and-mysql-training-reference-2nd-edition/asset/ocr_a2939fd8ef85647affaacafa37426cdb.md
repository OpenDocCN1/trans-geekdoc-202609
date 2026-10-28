# The utility files

Parts 2 through 4 of this figure show the code for the two utility files that are used by the controller of the Upload Image application.

The first file (file_util.php) contains the get_file_list function that returns an array of the filenames in the directory path that’s passed to it. However, if the path that’s passed to it isn’t valid, this function returns an empty array. Since the code in this function is so similar to the code in figure 23–1, you shouldn’t have any trouble understanding it.

The second file (image_util.php) contains a process_image function that is used to create 100- and 400-pixel versions of an image, if that’s necessary, plus a helper function named resize_image that actually does the resizing.

The process_image function accepts two parameters: the directory for the image and the filename for the image. Then, the first four statements set up the variables that are needed throughout the function. The first statement adds a separator to the end of the directory parameter, so a directory named “images” becomes “images/”. The second statement gets the index for the dot in the filename. The third statement stores the name of the file without its extension. And the fourth statement stores the extension of the file.

Then, the process_image function sets up the read path for the old image and the write paths for the new images. For the write paths, this code appends “_400” to the name of the file to indicate a maximum width of 400 pixels, and it appends “_100” to the name of the file to indicate a maximum width of 100 pixels.

Last, this code calls the resize_image function twice to create the two smaller versions of the image. This function is shown in parts 3 and 4 of this figure. Since its code is similar to the code in the last four figures, you shouldn’t have much trouble understanding it. But here’s a quick summary.