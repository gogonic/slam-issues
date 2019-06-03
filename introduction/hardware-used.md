# Hardware

## Camera and IMU

The majority of the experiments were conducted with ZED Mini by Stereolabs, which comes with a built-in gyroscope and accelerometer. A stereo camera was chosen because it enables us to estimate depth and the therefore, scale of environment. The ZED Mini is also small in size, lightweight and easy to mount on both ground and aerial vehicles. The only caveat with ZED Mini is that it cannot run on a CPU and needs a GPU for functioning.

## Robots

The appeal of using real robots \(both UGVs and UAVs\) for experiments is twofold. The first and obvious one is that they are the intended platforms that the final system will run on and will provide a more realistic setting for our experiments. Second, certain classes of robots such as UGVs offer an easy way to obtain the \(rough\) ground truth for the trajectory. For example, the Turtlebot uses wheel encoders to output the robot's current pose from its starting point as a reference, which is quite good in the absence of wheel slippage.

**NOTE: All robots mentioned below are subject to availability, and might require scheduling slots in advance to prevent conflicts with other people who might be using it.**

### Turtlebot

A Turtlebot 3 is available at RBCCPS. 

### Parrot Bebop

A few Parrot Bebop drones are available at RBCCPS. These are easy-to-control drones that can be flown with the help of a mobile app. However, without hardware modification, you are limited to using Bebop's built-in camera. There are other limitations such as the inability to access raw sensor values directly due to its proprietary nature.

### Larger drones

Larger drones such as the DJI Matrice need coordination with Aero for flights. You may contact [Varun](https://slam-rbccps.gitbook.io/slam/people#handy-contacts) to set up a slot for any flights.

### Logistical issues

Despite the advantages offered by using actual robots for experiments, handheld recording offers a quick and easy way to record various kinds of sequences and perform sanity tests without the need for extensive setting up of hardware. Along with the non-triviality of the hardware setup, the shortage of experienced UAV pilots needed to fly these drones as well as the lack of a systematic way to schedule slots with the flying team for performing these trials have contributed to significant delays in performing field tests. The long wait times for the repairs following drone crashes have also exacerbated this issue.

