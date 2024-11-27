---
layout: page
title: Self-Driving Polaris GEM
description: Autonomous vehicle lane detection and waypoint navigation project
img: assets/img/GEM.jpeg
importance: 1
category: academic
related_publications: false
---

<meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">

Below is a demonstration of autonomous vehicle systems algorithms
applied in both real world and simulated scenarios.

## NVIDIA Jetson F1Tenth Car Lane Following and Traffic Sign Detection
The following is my project using an F1tenth car with an NVidia Jetson to navigate a track while recognizing traffic signs and reacting accordingly.

<div class="embed-responsive embed-responsive-16by9">
    <iframe src="https://i.giphy.com/media/v1.Y2lkPTc5MGI3NjExY2dzMm5iM2xmYjkyZnlzYnphOHl4MDFpZjVyN2J4ODBzMjJ4ODNlYiZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/2P09sX8uPMy2V3T3XC/giphy.gif" class="embed-responsive-item" allowFullScreen></iframe>
</div>
<div class="caption">
    Line Following using PID Controller on F1Tenth Car
</div>

## Lane Detection
The lane detection is shown through 2 different views. The rviz view on the top is sobel edge detection gradient threshold filtering combined with a color filter that filters in common white and yellow lane markings. The view on the bottom of the rviz screen is the birds eye view. This view is created by taking in a binary image and gradient threshold. Then, the binary image is put though a 3x3 transformation matrix using the [cv2.getPerspectiveTransform()](https://docs.opencv.org/4.x/da/d54/group__imgproc__transform.html) function.


<div class="embed-responsive embed-responsive-16by9">
    <iframe src="https://giphy.com/embed/JkTMoWDDpuufxiKPnx" class="embed-responsive-item" allowFullScreen></iframe>
</div>
<div class="caption">
    Real World Lane Detection Example
</div>

<div class="embed-responsive embed-responsive-16by9">
    <iframe src="https://giphy.com/embed/zh3bAGgGyS0UyoU0Ix" class="embed-responsive-item" allowFullScreen></iframe>
</div>
<div class="caption">
    Another Real World Lane Detection Example
</div>

<div class="embed-responsive embed-responsive-16by9">
    <iframe src="https://www.youtube.com/embed/NN2vsqcLwJA?si=2MWB7vqfK9gv0hnR" class="embed-responsive-item" allowfullscreen></iframe>
</div>
<div class="caption text-center">
    Lane Detection Algorithm in Gazebo Simulator
</div>

## Waypoint Navigation
The waypoint navigation is created through longetudinal and lateral controllers. The longetudinal controller determines the speed of the vehicle depending on whether there is a curve in the road. If the GEM car detects a curve, the vehicle slows down to safely navigate around the turn, then speeds up once the turn is finished. For the lateral controller, I used the [pure pursuit](https://www.mathworks.com/help/nav/ug/pure-pursuit-controller.html) algorithm to determine the turning angle of the car by processing lookahead points. The following algorithm was used in determining the turning angle of the GEM car:

$$
\delta = \arctan\left( \frac{2L \cdot \sin(\alpha)}{ld} \right)
$$

where:

- L is the length of the vehicle wheelbase,
- α is the angle between the vehicle's heading and the look-ahead line,
- ld is the lookahead distance.

<div class="embed-responsive embed-responsive-16by9">
    <iframe src="https://www.youtube.com/embed/GVSbcxOKyEM?si=776pPRJnbhWhioOG" class="embed-responsive-item" allowfullscreen></iframe>
</div>
<div class="caption text-center">
    Waypoint Navigation in Gazebo Simulator
</div>

## Monte Carlo Localization
In robotics, it is very difficult to determine where a robot is in a certain space. Monte Carlo Localization (MCL), also known as particle filter localization, offers a solution to this challenge by using a probabilistic approach to determine a robot's position and orientation within a known map. As the robot moves, these particles are shifted based on the robot's motion model, incorporating uncertainty to account for movement inaccuracies. Sensor data is then used to update the likelihood of each particle's accuracy, with those matching more closely to the real-world data being deemed more probable. This step is followed by resampling, where particles with higher likelihoods are chosen to represent the robot's new estimated state, allowing the algorithm to focus on the most probable locations. Below, the yellow turtle represents the estimated robot location, and the green turtle represents the actual robot location.

<div class="embed-responsive embed-responsive-16by9">
    <iframe src="https://www.youtube.com/embed/SYovdYsZSRI?si=sMoiSOaJ4qCYmbK2" class="embed-responsive-item" allowfullscreen></iframe>
</div>
<div class="caption text-center">
    Monte Carlo Localization with 8 Directional Measurement
</div>

<!-- For more information on how to run these simulations, check out the source code below: -->

<!-- {% if site.data.repositories.github_repos %}
<div class="repositories d-flex justify-content-center" style="width: 100%;">
  {% for repo in site.data.repositories.github_repos %}
    {% if repo == "PNatarajan123/AutonomousPolarisGEM" %}
      {% include repository/repo.liquid repository=repo %}
      {% break %}
    {% endif %}
  {% endfor %}
</div>
{% endif %} -->