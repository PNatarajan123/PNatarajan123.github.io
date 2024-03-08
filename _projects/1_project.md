---
layout: page
title: Self-Driving Polaris GEM
description: Autonomous vehicle lane detection and waypoint navigation project
img: assets/img/GEM.jpeg
importance: 1
category: academic
related_publications: false
---

Below is a demonstration of autonomous algorithms
applied in both real world and simulated scenarios.

## Lane Detection
The lane detection is shown through 2 different views. The rviz view on the bottom is sobel edge detection gradient threshold filtering combined with a color filter that filters in common white and yellow lane markings. The view on the top of the rviz screen is the birds eye view. This view is created by taking in a binary image and gradient threshold. Then, the binary image is put though a 3x3 transformation matrix using the [cv2.getPerspectiveTransform()](https://docs.opencv.org/4.x/da/d54/group__imgproc__transform.html) function.


<div class="row">
    <div class="col-sm mt-3 mt-md-0 d-flex justify-content-center">
        <div style="max-width: 100%; width: 560px; aspect-ratio: 16 / 9;">
            <iframe src="https://giphy.com/embed/JkTMoWDDpuufxiKPnx" width="560" height="315" frameBorder="0" class="giphy-embed" allowFullScreen></iframe>
        </div>
    </div>
</div>

<div class="caption">
    Real World Lane Detection Example
</div>
<div class="row">
    <div class="col-sm mt-3 mt-md-0 d-flex justify-content-center">
        <div style="max-width: 100%; width: 560px; aspect-ratio: 16 / 9;">
            <iframe src="https://giphy.com/embed/zh3bAGgGyS0UyoU0Ix" width="560" height="315" frameBorder="0" class="giphy-embed" allowFullScreen></iframe>
        </div>
    </div>
</div>
<div class="caption">
    Another Real World Lane Detection Example
</div>
<div class="row">
    <div class="col-sm mt-3 mt-md-0 d-flex justify-content-center">
        <div style="max-width: 100%; width: 560px; aspect-ratio: 16 / 9;">
            <iframe width="560" height="315" src="https://www.youtube.com/embed/NN2vsqcLwJA?si=2MWB7vqfK9gv0hnR" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
        </div>
    </div>
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

<div class="row">
    <div class="col-sm mt-3 mt-md-0 d-flex justify-content-center">
        <div style="max-width: 100%; width: 560px; aspect-ratio: 16 / 9;">
            <iframe width="560" height="315" src="https://www.youtube.com/embed/GVSbcxOKyEM?si=776pPRJnbhWhioOG" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
        </div>
    </div>
</div>
<div class="caption text-center">
    Waypoint Navigation in Gazebo Simulator
</div>

For more information on how to run these simulations, check out the source code below:

{% if site.data.repositories.github_repos %}
<div class="repositories d-flex justify-content-center" style="width: 100%;">
  {% for repo in site.data.repositories.github_repos %}
    {% if repo == "PNatarajan123/AutonomousPolarisGEM" %}
      {% include repository/repo.liquid repository=repo %}
      {% break %}
    {% endif %}
  {% endfor %}
</div>
{% endif %}