# **Finding Lane Lines on the Road** 
[![Udacity - Self-Driving Car NanoDegree](https://s3.amazonaws.com/udacity-sdc/github/shield-carnd.svg)](http://www.udacity.com/drive)

<img src="examples/laneLines_thirdPass.jpg" width="480" alt="Combined Image" />

Overview
---

Project 1 of Self-Driving Car NanoDegree. 

Based on the [problem statement & code template](https://github.com/udacity/CarND-LaneLines-P1/blob/master/P1.ipynb) and the [writeup template](https://github.com/udacity/CarND-LaneLines-P1/blob/master/writeup_template.md). The project requirements are listed in the [project rubric](https://review.udacity.com/#!/rubrics/322/view)


Project Reflection
---

1. Describe the pipeline
From a 30,000 foot view, the pipeline is based on tuning of a few images (far less than the # of images contained in the video sequence used for testing).
The image is converted to grey scale, and undertakes a Gaussian smooth to reduce noise. Then Canny edge filter is applied, and a masked area (so that edges of other objects on the road are omitted) is used to detect lanes. The Hough transform is applied and tuned to find line segments that are more likely to be the lane markings. The segments are then fitted linearly, to extend the segments into lines that define the lane continuously.

2. Identify any shortcomings
    1. Manually tuned parameters based on a small sample population.
    2. The masked area enables simplicity of detection, but is highly dependent on the mounting location of camera.

3. Suggest possible improvements


Project Criteria Checklist
---

