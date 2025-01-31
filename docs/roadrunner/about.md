---
sidebar_position: 1
---

# What is Roadrunner?
Roadrunner is an FTC library for planning robot paths.

These docs only cover version 1.0+ of the Roadrunner Library. If you are using an older version (0.5) of Roadrunner, please see [learnroadrunner.com](https://learnroadrunner.com/).

# Why make this?
There are other sites (shown below) detailing some functionality of Roadrunner, however, these sites lack a lot of detail, leaving a lot up to the end user to figure out. The goal of this website is to provide a more comprehensive guide to RR 1.0+.

[https://rr.brott.dev/docs](https://rr.brott.dev/docs/)
[https://cookbook.dairy.foundation/roadrunner_10/complete_trajectorybuilder_reference.html](https://cookbook.dairy.foundation/roadrunner_10/complete_trajectorybuilder_reference.html)

## Coordinate Frame
Roadrunner operates on an alliance-centric coordinate frame with coordinate (0.0, 0.0) being the center of the field and coordinate (-72.0, -72.0) being the bottom left corner from the point of view of the alliance.

Roadrunner's coordinates coorespond to inches. For example, the coordinate (20.0, 30.0) would be located here:
PUT HERE

## Installation
For installation instructions, please see: [https://rr.brott.dev/docs/v1-0/installation/](https://rr.brott.dev/docs/v1-0/installation/).

## Sample Program
The following is a simple program showcasing some basic features of Roadrunner.

```java
// Specify a starting pose
Pose2d beginPose = new Pose2d(-16.0, -55.0, Math.toRadians(90.0));

// Create an instance of the Mecanum Drive class
MecanumDrive drive = new MecanumDrive(hardwareMap, beginPose);

// Create variables to store the Trajectory and Action
TrajectoryActionBuilder traj;
Action trajAction;

// Create a Trajectory
traj = drive.actionBuilder(drive.pose)
  // Put your functions here
  .strafeTo(new Vector2d(30.0, 10.0))
  .splineTo(new Vector2d(-30.0, -10.0));

// Create an action that follows the created trajectory
trajAction = traj.build()

// Run the action
Actions.runBlocking(trajAction);
```
