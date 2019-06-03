# Challenges with Challenge 3

## Challenge 3 and SLAM

Visual servoing has been the go-to method for most tasks that involve identifying a known object, going towards it and performing some action near/on it. Most sub-tasks in Challenges 1 and 2 follow this pattern. However, in the case of Challenge 3, particularly in the scenario where the robot is already inside the building and has to get out \(say, after dousing the fire\), the view of objects from inside the building would be previously unseen. This makes it unsuitable for something like visual servoing.

SLAM's ability to localize the robot in a previously unseen location has made it a suitable candidate for this task. The approach here has been to try to keep track of the path taken by the drone from the time it enters the building till it is ready to go back, and try to make the robot retrace this path so that it reaches the point where it started.

The motivation for and details of the two experiments related to this challenge \(one real-world and performed one simulation and yet-to-be-performed\) are outlined below.

## Experiment 1: Is SLAM really needed?

### Experiment setup

A ZED Mini camera was mounted on a Turtlebot and manually driven around three obstacles \(cardboard boxes\) to reach the source of a simulated fire. During this manually controlled stage, the pose messages from ZED Mini's visual odometry system were continuously recorded and stored in a bagfile. This file, therefore, contained an ordered list of poses that the Turtlebot took to get to the final point.

We then play out these poses from the rosbag in reverse order as commands to the Turtlebot \(making it retrace its path autonomously\). Assuming the Turtlebot's wheel-encoder based waypoint navigation feature is highly accurate, the idea was that this experiment could serve to quantify the accuracy of different approaches as a function of different variables such as time/distance of operation, recording resolution, etc.

### Experiment details

Given the phrasing of the problem as one of "retracing" and the relatively small area of interest \(inside the tower\), a pure visual odometry approach seemed like a natural first candidate to explore.

Pure visual odometry \(often referred to simply as "visual odometry"\) differs from SLAM in that it only remembers a local map and lacks the ability to "close loops" when the same location is visited after a gap. This makes it susceptible to drift when used for longer durations of time.

Our experiments with using ZED Mini's built-in visual odometry \(ZED Mini internally fuses vision with IMU to provide this odometry\) showed that for short trajectories \(length of around 5 metres\), it performed fairly well in the task of retracing while avoiding obstacles. However, we had good reason to believe that with 5 metres, we were reaching the limits of how far pure VO would perform decently because we found that around this point, the Turtlebot would often graze the surface of one of the cardboard boxes on its way back.

## Experiment 2: How to recover from a "lost track" situation?

### Experiment rationale

Losing track of your location is a common problem while performing SLAM. This can happen due to a variety of reasons such as very quick movements or being exposed to featureless scenes. 

The common approach that most SLAM frameworks take in addressing this issue are based along two main lines:

1. Preventing the "losing track" scenario from happening in the first place by making SLAM more robust to quick movements. This is mostly done by fusing Visual SLAM with information from IMU sensors.
2. Generating a new map that is disconnected from the original one and hoping that they will merge at some future point in time.

However, neither of these approaches exploit a very crucial component of the situation - the control inputs. Rather than passively running SLAM on whatever trajectory is decided by the control input, by letting the SLAM algorithm influence the trajectory taken, we can do things like:

1. create frequent loop closures \(which ensure a robust map\), and
2. retrace our steps from the point where we lost track to induce relocalization.

This approach has been studied under the name of "Active SLAM"



