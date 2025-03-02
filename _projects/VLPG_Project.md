---
layout: page
title: VLPG-Nav Object Navigation Using Visual Language Pose Graph and Object Localization Probability Maps
description: Advancing Visual Language Navigation and Object Goal Navigation with VLPG-Nav
img: assets/img/publication_preview/new_formulation.gif
importance: 3
category: work
---

We present VLPG-Nav, a visual language navigation method for guiding robots to specified objects within household scenes. Unlike existing methods primarily focused on navigating the robot toward objects, our approach considers the additional challenge of centering the object within the robot’s camera view. Our method builds a visual language pose graph (VLPG) that functions as a spatial map of VL embeddings. Given an open-vocabulary object query, we plan a viewpoint for object navigation using the VLPG. Despite navigating to the viewpoint, real-world challenges such as object occlusion, displacement, and the robot’s localization errors can prevent visibility. We build an object localization probability map that leverages the robot’s current observations and prior VLPG. When the object is not visible, the probability map is updated, and an alternate viewpoint is computed. In addition, we propose an object-centering formulation that locally adjusts the robot’s pose to center the object in the camera view. We evaluate the effectiveness of our approach through simulations and real-world experiments, evaluating its ability to successfully view and center the object within the camera’s field of view. VLPG-Nav demonstrates improved performance in locating the object, navigating around occlusions, and centering the object within the robot’s camera view, outperforming selected baselines in the evaluation settings.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/vlpg_framework.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    (Fig. a) The overall framework of VLPG-Nav. Given an object-related prompt, an initial viewpoint is computed using the visual language pose graph (VLPG) and clustering. Subsequently, we center the object in the camera image through our proposed object-centering cost function. If the object is not in view at the chosen viewpoint, we replan using an object localization probability map constructed using the local occupancy map and VLPG. (Fig. b) A real-world example where the robot is tasked with viewing a plant. The figure shows the camera view from the initial viewpoint, and the robot successfully views the plant. (Fig. c) In this case, we obstruct the initial viewpoint with an obstacle. The figure shows the obstructed camera view from the initial viewpoint. (Fig. d) Due to occlusion, the local search identifies an alternative viewpoint, enabling the robot to achieve an unobstructed view of the plant.
</div>


<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include video.liquid path="assets/video/VLPG_NAV_IROS24_Final.mp4" title="example image" class="img-fluid rounded z-depth-1" controls=true autoplay=true %}
    </div>
</div>


```html
<div class="row justify-content-sm-center">
  <div class="col-sm-8 mt-3 mt-md-0">
    {% include figure.liquid path="assets/img/6.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
  </div>
  <div class="col-sm-4 mt-3 mt-md-0">
    {% include figure.liquid path="assets/img/11.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
```

{% endraw %}
