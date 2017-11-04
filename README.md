# **Finding Lane Lines on the Road** 

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./test_images_output/solidWhiteRight_gray.jpg "Grayscale"
[image2]: ./test_images_output/solidWhiteRight_gaussian.jpg "Gaussian"
[image3]: ./test_images_output/solidWhiteRight_edges.jpg "Edges"
[image4]: ./test_images_output/solidWhiteRight_masked.jpg "Masked"
[image5]: ./test_images_output/solidWhiteRight_linesegment.jpg "Hough"
[image6]: ./test_images_output/solidWhiteRight_lineextended.jpg "Fit"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 6 steps. 
    1. I converted the images to grayscale: ![alt text][image1]
    2. I applied a Gaussian filter to smooth out noises:![alt text][image2]
    3. I applied Canny filter to detect the edges: ![alt text][image3]
    4. A mask is used to reduce the view to only the region of interest, that roughly outlines area of left and right lanes: ![alt text][image4]
    5. The line segments of lane markings are then detected in the Hough space: ![alt text][image5]
    6. The line segments tracing the left and right lane markings are then fitted linearly, that extends to make the boundaries more continuous: ![alt text][image6]


In order to draw a single line on the left and right lanes, I modified the draw_lines() function by adding a linear fit, which is shown above (lines in red).


### 2. Identify potential shortcomings with your current pipeline

1. Manually tuned parameters that are specific to the camera mounting location (the challenge problem had the edge of the hood in the view of the camera, which is picked up by line detection).
2. "Optimized" based on a small sample set of images, while the test is done by a video sequence which contained many more images.
3. The linear fit takes all starting points of line segments into account. And objects picked by lines detected that are not part of lane markings cause the fitted lines jitter.


### 3. Suggest possible improvements to your pipeline

1. Use logic to filter line segments detected from Hough space -- the slope of lane markings should be within a tolerance band with a given mounting location of the camera, so that anything that's beyond the band should be eliminated.
2. If ground truth data can be provided to a larger training set, a deep learning approach may be better.
3. The same slope tolerance band based filter may help improve the jittering of extended lines.
