#**Finding Lane Lines on the Road**

##Writeup

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

###1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 6 steps:
1. convert the images to grayscale;
2. apply Gaussian smoothing to the grayscale images;
3. use the Canny edge detection from OpenCV to detect the edges of objects in the images.
4. apply a four-sided polygon to mask the images so that only the edges on the road remain.
5. apply Hough Transformation to find lane lines in the image.
6. add the lane lines back to the original images.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by splitting the lines into two subsets, one containing the lines of the left lane and the other containing the lines of the right lane. Then I calculate each subset's average slope and average position. From there I can extrapolate to the top and bottom of the lines.

![alt text][image1]


###2. Identify potential shortcomings with your current pipeline


One potential shortcoming is that my draw_lines function does not handle outliers lines very well. For example, in the optional challenge video, my line prediction is greatly affected by the bottom part of the video, which shows edges of the cars. 

Another shortcoming could be ...


###3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...
