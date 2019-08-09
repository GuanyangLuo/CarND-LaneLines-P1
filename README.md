# **Finding Lane Lines on the Road** 

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

My pipeline consisted of 5 steps:
1. Convert the images to grayscale
2. Apply Gaussian blur
3. Apply Canny edge detection
4. Apply polygonal mask to focus on the area with the lanes
5. Apply Hough transform to find the lines

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by:
1. Selecting the lines with slope similar to what can be expected from each lane (based on experience)
2. Averaging the slopes and intercepts of the lines belonging to each lane
3. Draw one line for each lane using the averaged slopes and intercepts from bottom of the image to the middle (or 2/5) of the image


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when the colors of parts of the road differ greatly such that sections of the image are over-exposed or under-exposed, causing Canny to fail to pick up the edges. 

Another shortcoming could be the fact that dark (tire) streaks on a light color road being may be detected as lane.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to threshold the image so as to remove pixels with grayscale value lower than the average value in a bright image (light colored road), so that only the bright lanes are detected and not the dark streak.

Another potential improvement could be to use a better mask to limit the Hough transform to somewhere around to the lanes, instead of a large region of the image.

