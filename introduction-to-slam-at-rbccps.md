# Introduction to SLAM at RBCCPS

## Our Approach to SLAM \(So Far\)

### Why Visual SLAM?

Since the resultant system is aimed at providing localization and mapping capabilities for aerial vehicles in addition to ground vehicles, LiDAR-based approaches, due to their bulky nature, have not been considered. Keeping this in mind, the work so far has focused only on vision-based techniques combined with other sensor modalities such as inertial sensors, GPS sensors, and wheel encoders.

### Standard SLAM datasets

The general approach so far has involved testing out various popular open-source Visual SLAM/Odometry frameworks as well as other commonly used approaches for localization such as EKF-based sensor-fusion techniques that can combine vision with other sensor modalities. Due to differences in both the nature of the environment as well as the exact sensor models used, the results obtained from standard evaluation datasets such as EuRoC, KITTI, and TUM have not been reliable indicators of performance in conditions resembling that of the challenge. Moreover, the sensitivity of the accuracy of the mapping/localization systems on the calibration of the sensors and the initialization procedures make it difficult to separate the errors stemming from the shortcomings of the frameworks from those arising from errors in the calibration/initialization process.

This called for empirical evaluation of the various SLAM frameworks and identifying which of them might be suitable for our setting, keeping in mind the sensor modalities available to us, computational resources, ease of integration with other parts of the system, nature of the challenge, and the nature of the environment.

### Deep-learning based techniques

As a parallel track, we are also exploring the feasibility and accuracy of deep learning based SLAM techniques.



