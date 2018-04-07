# **Finding Lane Lines on the Road** 
This is a project from Udacity Self-Driving Car NanoDegree

<img src="examples/laneLines_thirdPass.jpg" width="480" alt="Combined Image" />

Overview
---

When we drive, we use our eyes to decide where to go.  The lines on the road that show us where the lanes are act as our constant reference for where to steer the vehicle.  Naturally, one of the first things we would like to do in developing a self-driving car is to automatically detect lane lines using an algorithm.

In this project, I will detect lane lines in images using Python and OpenCV.  OpenCV means "Open-Source Computer Vision", which is a package that has many useful tools for analyzing images.  

The Project
---

My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I used gaussian blur to smooth images. Then canny transformation is applied to find edges. I used a trapezoid shape mask to limit the region. Then applied the Hough transformation on the masked canny result and draw lines on the raw image.  

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by calculating the slope of left and right lanes separately. If both vertices of the line is on the left part of the image and the slope is smaller than -0.5, I treat it as a valid left line; if both vertices of the line is on the right part of the image and the slope is larger than 0.5, I treat it as a valid right line. Do a linear fit to both valid left and right lines, and draw the fit Lane lines.  

Image results of the pipeline are shown in the notebook.  


