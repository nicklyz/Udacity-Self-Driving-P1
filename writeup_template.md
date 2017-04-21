# **Finding Lane Lines on the Road**

## Writeup

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"
[gray]: ./test_images_output/solidWhiteCurve.jpg-gray.jpeg "Gray"
[blur_gray]: ./test_images_output/solidWhiteCurve.jpg-blur_gray.jpeg "Blur Gray"
[edges]: ./test_images_output/solidWhiteCurve.jpg-edges.jpeg "Edges"
[masked_edges]: ./test_images_output/solidWhiteCurve.jpg-masked_edges.jpeg "Masked_edges"
[lines]: ./test_images_output/solidWhiteCurve.jpg-lines.jpeg "lines"
[img]: ./test_images_output/solidWhiteCurve.jpg "img"

---

### Reflection

#### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 6 steps:
1. convert the images to grayscale; ![alt text][gray]
2. apply Gaussian smoothing to the grayscale images; ![alt text][blur_gray]
3. use the Canny edge detection from OpenCV to detect the edges of objects in the images. ![alt text][edges]
4. apply a four-sided polygon to mask the images so that only the edges on the road remain. ![alt text][masked_edges]
5. apply Hough Transformation to find lane lines in the image. ![alt text][lines]
6. add the lane lines back to the original images. ![alt text][img]

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by splitting the lines into two subsets, one containing the lines of the left lane and the other containing the lines of the right lane. Then I calculate each subset's average slope and average position. From there I can extrapolate to the top and bottom of the lines.


### 2. Identify potential shortcomings with your current pipeline

One potential shortcoming is that my draw_lines function does not handle outliers lines very well. For example, in the optional challenge video, my line prediction is greatly affected by the bottom part of the video, which shows edges of the cars.

Another shortcoming could be that the masked area may not be accurate for all cases. If the camera position moves either vertically or horizontally, my line detection would have a lot more noises.

### 3. Suggest possible improvements to your pipeline

A possible improvement would be to use outlier detection algorithm to take out the line noises that have significant different slope than the lane lines.
