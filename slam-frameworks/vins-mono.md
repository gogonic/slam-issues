# VINS Mono

## Introduction

VINS-Mono is a monocular visual-inertial SLAM frameworks. VINS-Fusion is a newer framework that includes support for Stereo among other enhancements. However, since our experiments were performed before the release of VINS-Fusion, this document will outline our experience with VINS-Mono only.

## **Paper and Code**

The code and links to the paper can be found on the official GitHub repository - [https://github.com/HKUST-Aerial-Robotics/VINS-Mono](https://github.com/HKUST-Aerial-Robotics/VINS-Mono).

## **Issues**

### **Memory requirement**

While VINS Mono running on a recording from ZED Mini's VGA resolution of 672x376 runs smoothly even on mobile platforms, at 1280x720 \(ZED Mini's HD resolution\), even a laptop with 16 GB of RAM begins to lag, making HD resolution infeasible for usage in live settings. An \(unverified\) hypothesis is that being restricted to VGA resolution significantly reduces the accuracy of both the resulting trajectory as well as the map.

### **Camera-IMU calibration**

VINS-Mono needs either an accurate specification of the spatio-temporal calibration parameters \(both the extrinsic transformation matrix between the IMU and camera as well as the time delay between the two\) or a dynamic initialization procedure involving exciting the IMU sensor in all its axes. VINS provides three separate methods for calibration that are based on mixing and matching these two options:

1. a confident estimate of both of these values provided beforehand  
2. an initial approximation estimate of the two values provided beforehand, followed by VINS refining it during the IMU excitation step  
3. no initial estimates given; VINS will estimate it from scratch during the IMU excitation step.

If we assume that the "hyperparameters" of VINS are the same for all three cases, the errors in the output trajectory can be attributed to only the calibration procedure, a combination of the calibration and the initialization procedures, and only the initialization procedure respectively.

Using ZED Mini across a wide variety of environments \(both indoor and outdoor\), we noticed that when using the second and third methods, accurate calibration was highly sensitive to initial excitation movements to an extent that almost identical excitation patterns produced vastly different results. With the first method, the expectation being that the calibration is solely dependent on the calibration performed beforehand, the results were equally bad.

Using Kalibr, we estimated both the extrinsic transformation as well as the time offset between the camera and the IMU \(commonly referred to as spatio-temporal calibration\).

