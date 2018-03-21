# **Finding Lane Lines on the Road** 

## Writeup Template

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 6 steps. 
    * First, I converted the images to grayscale
    * Then I applied a gaussian blur to each image
    * I applied [Canny Edge Detaction](https://en.wikipedia.org/wiki/Canny_edge_detector) which is used to detect edges in an image by marking where a color changes significantly to another; I've chosen a low_threshold of 50 and high_threshold of 150
    * Next I limited the area in a polygon shape to where the lanes are, then applied [Hough Transform](https://en.wikipedia.org/wiki/Hough_transform) to get an array containing endpoints of detected line segments
    * In order to draw a single line on the left and right lanes, I modified the draw_lines() function by determining the slope of each lines to get their direction, also if the slope of a line is not extreme enough, it will not be a considered edge.
    If a slope is negative, its line belongs to the left lane marking. If the slope is positive, its line belongs to the right group. To add a line to either group, I added the various x and y endpoint coordinates to its corresponding array.


![alt text][test_images/solidWhiteCurve]
![alt text][test_images/0.png]


### 2. Identify potential shortcomings with your current pipeline

The images and videos this pipeline has been tested on are mainly straight roads with visible lane lines. 

One potential shortcoming would be what would happen when the visibility of the lane lines are reduced. ie when driving in the dark

Another shortcoming could be driving throuigh curved terrain


### 3. Suggest possible improvements to your pipeline

A  big possible improvement would be to  continue tuning the Canny edge and Hough lines parameters.

Another potential improvement could be to impprove my drawlunes function to cater for super extreme slopes
