# **Finding Lane Lines on the Road** 

## Writeup Template

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 6 steps. Actual output of each of the steps can be found in the "Notebook"

* First, I converted the images to grayscale,
* Added gaussian blur to the image
* Applied canny filter to discover edges in the image 
* Applied the polynomial region filter to isolate the relevant edges in the image. The polynomial is a triangle, with base at the bottom of the image. The top of the triangle is at "0.57" of the height of the image. 
* Used Hough Algorithem to determine the lines in the image. The algorithm was modified to extrapolate and average the lines to find single left and right lane.
* Finally the identified lines were super imposed on the original image

### Modification to Draw_Lines()
* First extrapolate all the lines found,  from bottom of image till "0.57" of the image which is same as hight of polynomial used for filtering. 
* Excluded any extrapolated lines that were going beyond the boundry of the image in X axis.  
* Next found the slope of each of the lines and grouped them, Positive slop for right lane and negetive slope for left lane. 
* Averaged the end points of all left lane and right lane related lines. 
* THe averaged line was used for drawing the final Lane on the original Image. 


The final video output from the algorithm was uploaded in youtube. 

[solidWhiteRight](https://www.youtube.com/watch?v=GGbwaK0Gshw)
[solidYellowLeft](https://www.youtube.com/watch?v=vl3HtRlkGuU)


### 2. Identify potential shortcomings with your current pipeline

This is a very basic model and has its shortcommings. 
* During sharp turns, the slope for both left and right lane may be same. need better algorithem to group lanes marking found. 
* The polynomial used for filtering can be better shaped, as it was not suitable for the 3rd exercise. 
* the Hough parameters need further tuning, as for few frames in the test video they did not find any lanes lines. 


### 3. Suggest possible improvements to your pipeline

Apart from the short commings, there are many improvements that can be done. 
* Rather than using straing lines we can build curved lines by finding shorter lane lines and using the endpoints and drawing a curve. 
* Found few articles which uses clever colouring schemes to better identify lane colour, white and yello
* Find all the lanes instead of finding only the lane on which we are driving. 


