---
title: 'Writeup'
disqus: Ansheel Banthia
---

Project 1 - Finding Lane Lines on the Road :car: 
===

Udacity Self-Driving Car Engineer Nanodegree

## Table of Contents

 - [ Summary ](#sum)
 - [ Description of Pipeline ](#des)
 - [ Potential Shortcomings ](#short)
 - [ Improvement to Pipeline ](#fut)


<a name="sum"></a>
## Summary

![](https://github.com/Ansheel9/P3-Collabration-Competition-DeepRL/blob/master/Images/plot.PNG)

When we drive, we use our eyes to decide where to go.  The lines on the road that show us where the lanes are act as our constant reference for where to steer the vehicle.  Naturally, one of the first things we would like to do in developing a self-driving car is to automatically detect lane lines using an algorithm.

In this project you will detect lane lines in images using Python and OpenCV.  OpenCV means "Open-Source Computer Vision", which is a package that has many useful tools for analyzing images.

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report

<a name="des"></a>
## Description of Pipeline
---
My pipeline consisted of 5 steps. First, I converted the images to grayscale. Then I apply the GaussianBlur function to the images in order to depress noise. Third, I use Canny Edge Detection algorithm to detect the edges for images. Fourth, I apply a region mask defined by the vertices of a quadrilateral to crop the images. Fifth, I run Hough Transform to detect lines for the cropped images, and use the draw_lines() function to draw the left and right straight lane lines. Last, I use cv2.addWeighted() function to draw the lane lines on the original images.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by seperating line segments by their slope (y2-y1)/(x2-x1) and their center coordinate to decide which line segments are part of the line vs. the right line. Then I average the position and slope of each of theline segments and extrapolate to the top and bottom of the lane.

This pipeline can successfully detect lane lines in the "solidWhiteRight.mp4" and "solidYellowLeft.mp4" videos. But when I apply it to the "challenge.mp4" video, it doesn't work.

So I modify the pipeline to overcome this obstacle. In the optional "challenge.mp4" video,we need to overcome the different lightness and shadow obstacle to successfully detect the lane lines. I used new set of parameters in the pipeline. Also, modified the vertices of region mask because the video resolution is higher than others.

<a name="short"></a>
## Potential Shortcomings with Current Pipeline
---
 - The pipeline could draw some strange lane lines when there are some shadows of trees or others in the test images.
 - Sometimes, the genrated line distorts with "challenge.mp4" video.

<a name="fut"></a>
## Improvement to Pipeline
---
 - A possible improvement would be to use advanced OpenCV techniques, such as Sobel operator, HLS or HSV color spaces and so on.
 - Use Convolutional Neural Network or other Deep Learning methods to create a semantic segmentation solution for detecting lane lines.


