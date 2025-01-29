---
sidebar_position: 1
---

# Trajectory Builder Heading
This page describes properly using heading when creating trajectories.

## Trajectory Builder Heading Functions

### No heading
These trajectories keep the heading the same throughout the trajectory. IDK WHAT IS DIFFERENCE BETWEEN THIS ONE AND CONSTANT HEADING???

#### Examples
```java
lineToX()
lineToY()
strafeTo()
splineTo()
```

### Constant Heading
Constant heading trajectories keep the heading the same throughout the trajectory.

#### Examples
```java
lineToXConstantHeading()
lineToYConstantHeading()
strafeToConstantHeading()
splineToConstantHeading()
```

:::tip Notice
PROB REMOVE BC DOESN'T MAKE SENSE
The start and end trajectory actually change the start and end [tangent](https://en.wikipedia.org/wiki/Tangent) lines of the spline.
:::
### Linear Heading
Heading changes linearly throughout a trajectory from a start heading to an end heading. The start heading can be specified with a `setTangent()` function before the trajectory movement otherwise it is the heading from the end of the previous trajectory (see below) CHECK THIS. The end heading is specified in the trajectory function.

#### Examples
```java
lineToXLinearHeading()
lineToYLinearHeading()
strafeToLinearHeading()
splineToLinearHeading()
```

### Spline Heading
Heading changes in accordance with a spline throughout a trajectory. The start tangent can be specified with a `setTangent()` function before the trajectory movement otherwise it is the heading from the end of the previous trajectory (see below) CHECK THIS. The end heading is specified in the trajectory function.

#### Examples
```java
lineToXSplineHeading()
lineToYSplineHeading()
strafeToSplineHeading()
splineToSplineHeading()
```

## Start and End Tangents
These are used to specify the starting and ending tangent of a trajectory.

The starting tangent can be specified with `setTangent()` and the end tangent is specified in the trajectory function as a parameter. A demonstration of this behavior is shown below.


### Examples

<details>
  <summary><strong>Example 1</strong></summary>

  ```java
  // Specify a starting pose - coordinate (0,0) facing forward
  Pose2d beginPose = new Pose2d(0.0, 0.0, Math.toRadians(45.0));

  // Create an instance of the Mecanum Drive class
  MecanumDrive drive = new MecanumDrive(hardwareMap, beginPose);

  // Create variables to store the Trajectory and Action
  TrajectoryActionBuilder traj;
  Action trajAction;

  // Create a Trajectory
  traj = drive.actionBuilder(drive.pose)
  // Put your functions here
  .splineToSplineHeading(new Pose2d(-50.0, 50.0, Math.toRadians(0.0)), Math.toRadians(-90.0))

  // Create an action that follows the created trajectory
  trajAction = traj.build()

  // Run the action
  Actions.runBlocking(trajAction);
  ```
  ### Explanation
  This function moves to the coordinates (-50, 50) with an end heading of `Math.toRadians(0.0)` and an end tangent of `Math.toRadians(-90.0)`. When a begin tangent/heading is not specified, the current heading is used. In this case that is the heading stored in `beginPose` which is `Math.toRadians(45.0)`.
  ```java
  .splineToSplineHeading(new Pose2d(-50.0, 50.0, Math.toRadians(0.0)), Math.toRadians(-90.0))
  ```
</details>