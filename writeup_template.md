# **Finding Lane Lines on the Road** 


---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I used gaussian blur to smooth images. Then canny transformation is applied to find edges. I used a trapezoid shape mask to limit the region. Then applied the Hough transformation on the masked canny result and draw lines on the raw image.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by calculating the slope of left and right lanes separately. If both vertices of the line is on the left part of the image and the slope is smaller than -0.5, I treat it as a valid left line; if both vertices of the line is on the right part of the image and the slope is larger than 0.5, I treat it as a valid right line. Do a linear fit to both valid left and right lines, and draw the fit Lane lines.

Image results of the pipeline are shown in the notebook.


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when the color of the road is changing and when shade appears. These will influence the result of the canny edge detector.

Another shortcoming could be when the car is right on a curve. The linear fit is not able to handle it perfectly. 


### 3. Suggest possible improvements to your pipeline

A possible improvement to the first shortcoming would be to set multiple thresholds to find valid lane lines. Such as in different color domain, detect different directions' gradient change and so on. 

A possible improvement to the first shortcoming would be to do a second order fit the lane lines. The second order should be enough to fit the curves appear in a high way.
