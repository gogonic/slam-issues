# ORB SLAM 2

ORB SLAM 2 is the successor of ORB SLAM that includes support for Stereo and RGB-D cameras along with certain improvements made to the Monocular case.

## Paper and Code

The code for ORB SLAM 2 can be found on its official GitHub repository - [https://github.com/raulmur/ORB\_SLAM2](https://github.com/raulmur/ORB_SLAM2). 

The repository also includes the links to the paper and related resources.

## Issues

1. It loses track in segments of quick, pure rotations of the camera.
2. Even during brief periods of being exposed to featureless scenes, ORB SLAM loses track and is not robust enough to localize itself until a more feature-rich scene is encountered.

The above two issues could probably be solved by fusing the visual odometry with measurements from an inertial sensor. While there are open-source forks of ORB SLAM 2 \(such as [this](https://github.com/lfy89/ORB_SLAM-IMU), [this](https://github.com/JzHuai0108/ORB_SLAM), and [this](https://github.com/ZuoJiaxing/Learn-ORB-VIO-Stereo-Mono)\) that aim to do this, none of them are well-maintained and suffer from various installation issues. We have been unable to successfully run one of these so far.

Another approach to solving this might involve tightly coupling the SLAM algorithm with the control system of the robot. Specifically, the control algorithm could be designed to respond to triggers from the SLAM algorithm every time the tracking is lost, and perform a short retracing step, giving ORB SLAM a chance to relocalize itself. A simulation to test out this approach is being prepared in the context of Challenge 3.

