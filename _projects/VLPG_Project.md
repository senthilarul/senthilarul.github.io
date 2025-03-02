---
layout: page
title: VLPG-Nav Object Navigation Using Visual Language Pose Graph and Object Localization Probability Maps
description: Advancing Visual Language Navigation and Object Goal Navigation with VLPG-Nav
img: assets/img/publication_preview/new_formulation.gif
importance: 3
category: work
---

<h3> Abstract </h3>
We present VLPG-Nav, a visual language navigation method for guiding robots to specified objects within household scenes. Unlike existing methods primarily focused on navigating the robot toward objects, our approach considers the additional challenge of centering the object within the robot’s camera view. Our method builds a visual language pose graph (VLPG) that functions as a spatial map of VL embeddings. Given an open-vocabulary object query, we plan a viewpoint for object navigation using the VLPG. Despite navigating to the viewpoint, real-world challenges such as object occlusion, displacement, and the robot’s localization errors can prevent visibility. We build an object localization probability map that leverages the robot’s current observations and prior VLPG. When the object is not visible, the probability map is updated, and an alternate viewpoint is computed. In addition, we propose an object-centering formulation that locally adjusts the robot’s pose to center the object in the camera view. We evaluate the effectiveness of our approach through simulations and real-world experiments, evaluating its ability to successfully view and center the object within the camera’s field of view. VLPG-Nav demonstrates improved performance in locating the object, navigating around occlusions, and centering the object within the robot’s camera view, outperforming selected baselines in the evaluation settings.

<h3> Problem  </h3>
We consider the problem of navigating a robot to an object of interest within a household environment. Distinct from the field of object-goal navigation, we consider previously explored environments, and our focus extends beyond merely navigating the robot to the object but also to frame the object within the robot’s camera view. Our focus primarily lies in household robot applications, where memory and computational efficiency are crucial. These robots often operate continuously in the same environments, allowing them to leverage prior knowledge to navigate and view the objects efficiently.

<h3> Contribution </h3>
VLPG-Nav, an object-goal navigation method designed for low-compute household robots. When provided with a textual prompt about an object, our approach navigates the robot to an instance of the object in the environment using prior knowledge of the environment and the robot’s current observation. Given the limited computing and memory power in affordable consumer robots, we desire a memory-efficient method that allows for easy integration of new environmental information. Furthermore, the robot’s final pose should provide a clear and discernible viewpoint for external observers, indicating the specific object the robot is focusing on. Our approach has three main components:

<ol>
    <li>
        **Initial Viewpoint Prediction:** We construct a visual language pose graph (VLPG) during environment ex- ploration, which is a graph of the robot’s pose and the corresponding VL embedding. Given a textual prompt, we use VLPG to identify a set of relevant nodes com- puted based on cosine similarity, and the viewpoints are clustered to compute a suitable viewpoint.
    </li>
    <li>
        **Object Centering:** We propose a cost function to locally correct the robot’s pose and center the object in the camera image. Specifically, the cost function orients the robot and moves it toward the object of interest once the initial viewpoint is reached.
    </li>
    <li>
        **Local Search:** When an object is undetected at the chosen viewpoint, we propose a local search method to replan an alternative viewpoint to bring the object into view. We propose a probability map based on the VLPG clusters and the local occupancy map, estimating the likelihood of regions where the object can be localized.
    </li>
</ol>

<h3> Method </h3>

State-of-the-art SLAM systems use pose graphs to localize the robot and construct a spatial representation of the environment. The graph consists of SE(3) robot poses and images captured from the pose as nodes, while the edges are relative pose measurements. Given the comprehensive coverage of the environment during the initial mapping phase, the robot’s path has transited and viewed most of the environment. This encourages using the mapping process to create prior knowledge representative of the environment. We build on the pose graph by augmenting each node with the VL embeddings of the robot’s camera view from

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/vlpg_framework.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    (Fig. a) The overall framework of VLPG-Nav. Given an object-related prompt, an initial viewpoint is computed using the visual language pose graph (VLPG) and clustering. Subsequently, we center the object in the camera image through our proposed object-centering cost function. If the object is not in view at the chosen viewpoint, we replan using an object localization probability map constructed using the local occupancy map and VLPG. (Fig. b) A real-world example where the robot is tasked with viewing a plant. The figure shows the camera view from the initial viewpoint, and the robot successfully views the plant. (Fig. c) In this case, we obstruct the initial viewpoint with an obstacle. The figure shows the obstructed camera view from the initial viewpoint. (Fig. d) Due to occlusion, the local search identifies an alternative viewpoint, enabling the robot to achieve an unobstructed view of the plant.
</div>

<h3> Video </h3>
<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include video.liquid path="assets/video/VLPG_NAV_IROS24_Final.mp4" title="example image" class="img-fluid rounded z-depth-1" controls=true autoplay=true %}
    </div>
</div>
