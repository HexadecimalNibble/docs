---
sidebar_position: 1
---

# What is Roadrunner?

Roadrunner is an FTC library.

These docs only cover version 1.0+ of the Roadrunner Library. If you are using an older version (0.5) of Roadrunner, please see [learnroadrunner.com](https://learnroadrunner.com/).


## Coordinate Frame
Roadrunner operates on an alliance-centric coordinate frame with coordinate (0, 0) being the center of the field and coordinate (-72, -72) being the bottom left corner from the point of view of the alliance.

Roadrunner's coordinates coorespond to inches. For example, the coordiante (20,30) would be located here:

# Installation
For installation instructions, see: [https://rr.brott.dev/docs/v1-0/installation/](https://rr.brott.dev/docs/v1-0/installation/).

# Sample Program
The following is a simple Roadrunner program showcasing some basic features.

```jsx
// Specify a starting pose
Pose2d beginPose = new Pose2d(-16, -55, Math.toRadians(90));

// Create an instance of the Mecanum Drive class
MecanumDrive drive = new MecanumDrive(hardwareMap, beginPose);

// Create variables to store the Trajectory and Action
TrajectoryActionBuilder traj;
Action trajAction;

// Create a Trajectory
traj = drive.actionBuilder(drive.pose)
  // Put your functions here
  .strafeTo(new Vector2d(30, 10))
  .strafeTo(new Vector2d(-30, -10));

// Create an action that follows the created trajectory
trajAction = traj.build()

// Run the action
Actions.runBlocking(trajAction);
```
