#### In this problem you will get hands-on experience with changing the resolution of an image, i.e., down-sampling and up-sampling. Follow the instructions below to finish this problem.

###(1) 
Download the original image from here. 
The original image is an 8-bit gray-scale image of width 479 and height 359 pixels. 
Convert the original image from type 'uint8' (8-bit integer) to 'double' (real number).

'''
%Load the raw image
raw_image = imread( 'https://d396qusza40orc.cloudfront.net/digital%2Fimages%2Fweek3_quizzes%2Foriginal_quiz.jpg' );
imshow(raw_image);
'''

###(2) 
Recall from the lecture that in order to avoid aliasing (e.g., jagged edges) when down-sampling an image, 
you will need to first perform low-pass filtering of the original image.

For this step, create a 3×3 low-pass filter with all coefficients equal to 1/9. 
Perform low-pass filtering with this filter using the MATLAB function "imfilter" with 'replicate' as the third argument. 
For more information about low-pass filtering using MATLAB, refer to the programming problem in the homework of module 2.

###(3) 
Obtain the down-sampled image by removing every other row and column from the filtered image, that is, 
removing the 2nd, 4th, all the way to the 358th row, and then removing the 2nd, 4th, all the way to the 478th column. 
The resulting image should be of width 240 and height 180 pixles. This completes the procedure for image down-sampling. 
In the next steps, you will up-sample this low-resolution image to the original resolution via spatial domain processing.

###(4) 
Create an all-zero MATLAB array of width 479 and height 359. 
For every odd-valued i∈[1,359] and odd-valued j∈[1,479], set the value of the newly created array at (i,j) 
equal to the value of the low-resolution image at (i+12,j+12). 
After this step you have inserted zeros into the low-resolution image.

###(5) 
Convolve the result obtained from step (4) with a filter with coefficients [0.25,0.5,0.25;0.5,1,0.5;0.25,0.5,0.25] 
using the MATLAB function "imfilter". 
In this step you should only provide "imfilter" with two arguments instead of three, that was the case in step (1). 
The two arguments are the result from step (4) and the filter specified in this step. 
This step essentially performs bilinear interpolation to obtain the up-sampled image.

###(6) 
Compute the PSNR between the upsampled image obtained from step (5) and the original image. 
For more information about PSNR, refer to the programming problem in the homework of module 2. 
Enter the PSNR you have obtained to two decimal points in the box below.
