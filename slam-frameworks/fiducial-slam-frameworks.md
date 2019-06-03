# Fiducial SLAM Frameworks

## Introduction

Both as a way of recovering the scale of the environment from a monocular camera and making SLAM robust to relatively plain scenes, we explored fiduciary/fiducial tag based SLAM frameworks soon after we realized the shortcomings of ORB SLAM.

## Frameworks Explored

We explored two frameworks - [UcoSLAM](http://www.uco.es/investiga/grupos/ava/node/62) and a ROS package called [fiducial\_slam](http://wiki.ros.org/fiducial_slam). While UcoSLAM augments vanilla monocular ORB SLAM with the detection and pose estimation of the Fiducial tags \(it uses generic ORB features in addition to the Fiducial markers\), the fiducial\_slam ROS package makes use of only the Fiducial markers and needs to always have two markers in its view to localize itself.

## Future Work

The natural extension of this approach into an environment where setting up of fiducial markers beforehand is infeasible would be to use other known objects in place of these tags. While the core principle would still be centred around exploiting the known metric dimensions of an object, using any object already present in the scene is more flexible than restricting it to specially designed Fiducial tags.

