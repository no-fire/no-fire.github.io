---
title: Story 1 - Reflections on the Data Collection Pipeline
layout: post
permalink: /data-collection
source-id: 1OwwObSiyLWbOfpometyXA_5ytZnusHYy2c5SZXdFhbM
published: true
---
Reflections on Data Pipeline

# Background

## Why a data pipeline?

For a supervised machine learning project, we need to collect and organize a large amount of data. Creating an agile and robust data pipeline will allow our team to collect the data we need, and avoid future headaches.

## What data do we need?

## ![image alt text]({{ site.url }}/public/cvJhp4jSLYgkJiWIFJsfA_img_0.png)

Figure 2: Neural network inputs and outputs. *Input Image 1* is fed into the neural network to calculate *Output Vector 1* (containing the desired forward and angular velocities). *Input Image 2* is then combined with the *Recurrent State 1* to calculate *Output Vector 2*.

Because we want a recurrent neural network regressor for our robot controller, we need a data pipeline that allows us to gather and store **sequential images **and **corresponding continuous velocities**.

# The Data Pipeline

# ![image alt text]({{ site.url }}/public/cvJhp4jSLYgkJiWIFJsfA_img_1.png)

Figure 1: The data pipeline

## Robot + Joystick

The robot send images and velocities data to our laptops in the form of a rosbag. The joystick is used to drive the robot in a continuous output space (like a steering wheel)

## Rosbag

Rosbag is a ROS tool that allows you to store and replay what happened to a robot.

## Extractor Script

The extractor script allows us to extract and organize sorted images and corresponding velocities.

## Disk (Images)

We store the sorted images and velocities on the machine learning server

## Neural Network

The server uses the data to train neural networks with the organized data.

# Philosophy

## Collect everything, process later

Because we are working with a physical robot, actually collecting the data can take a substantial amount of time. For example, if we can collect useful data points at 2hz and need 10,000 points, we need to spend over an hour just driving the robot around to get the necessary data. While we hope to need fewer than 10,000 points, the idea of needing to recollect data because we forgot to record something important still seems not very fun.

To handle this, we decided to use the fantastic built-in [rosbag](http://wiki.ros.org/rosbag) tool as the first step in all of our data collection. Because it is capable of exhaustively recording *everything* that travels over the ROS network, we can be confident we didn't forget to record something that we will regret later.

This method also has another important benefit: repeatability. Because we have committed to doing all of our preprocessing from these rosbag files, we should be able to run multiple different networks, requiring different forms of preprocessed data, off of the same bag files. This will allow us to compare the performance of lower vs. higher resolution processing pipelines, grayscale vs. color, or even LIDAR vs. camera only, if that is something we ever decide to investigate.

## All data from one collection session should live together

# How to parallelize writing scripts based on data you don't have

After deciding what data we were going to collect, we dove into how to collect it, process it, and integrate it. One thing that we did fairly well was the structure for setting up expectations of exactly what the data pipeline was going to look like, so that we could all work on separate pieces of how this was going to come together at the same time and parallelize our work. 

## Our data storage structure (from other document)

We all sat down to decide exactly what the data pipeline was going to look like, and typed up an accessible google doc (you can see it [here](https://docs.google.com/document/d/1m_9tAMSPhVd9YHXxiS7gS74h9O3FT_X9WAszFTgKTE0/edit?usp=sharing), or concisely in the image below) for all of us to reference when creating our individual parts. By making a google doc, we were all working towards the same end goal, and could develop on the same file system -- which didn't exist yet in real life -- on each of our respective computers. 

![image alt text]({{ site.url }}/public/cvJhp4jSLYgkJiWIFJsfA_img_2.png)

Specifically, the google doc contained the exact directories, naming conventions, and content that we would each be working with. While Joystick Control was outputting a source.bag to within a directory named based on the date and content of the bag, the Bag Processing script was able to take in a bag and output two hundred processed images to a folder named "raw" within that directory.

## Joystick control

The first step in the data pipeline is actually collecting the data from the physical robot, and because this is supervised learning, we need to collect both the image data and a "ground truth" estimate of how the network *should* command the robot in this situation. To start with, we are assuming that our network will process images at 2hz and output a single value: the desired turning velocity of the robot. In order to correctly train the network, we need to mimic those conditions as closely as possible during training.

To do this, we created a custom ROS node called `joy_control.py` whose job was to allow a human to drive the robot manually, subject to the same constraints the network will be. In particular, once recording has started, the robot will always travel forward slowly at constant speed, and turn commands requested by the user will only be updated twice per second.

This method has the added benefit of implicitly synchronizing the joystick controller timing with the bag processor. Because the `/cmd_vel` packets are stored in the bag file, they convey timing information about when the bag processor should capture and store the next sequential image.

## Creating bag processing script

# Network Data Transfer / Use of server

## Struggles: use ros to process files on laptop then transfer to real computer

* Diagram?

# Lessons Learned

* +: Having an actual document to describe data layout (before coding starts) is nice

* Δ: Indicate where the data goes in the design document

* Δ: Stub and chain!

![image alt text]({{ site.url }}/public/cvJhp4jSLYgkJiWIFJsfA_img_3.jpg)

![image alt text]({{ site.url }}/public/cvJhp4jSLYgkJiWIFJsfA_img_4.jpg)

