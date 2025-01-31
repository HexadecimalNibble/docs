---
sidebar_position: 1
---

# Trajectory Builder Heading and Tangent
This page describes how to properly using headings and tangents when creating trajectories.

## Trajectory Builder Heading Functions

### No heading
These trajectories keep the heading the same throughout the trajectory. This doesn't seem to be true for splines??? Todo: fix this

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

### Linear Heading
The heading linearly throughout a trajectory from a start heading to an end heading. The start heading is simply the current heading (end heading of previous trajectory movement). The end heading is specified in the trajectory function.

#### Examples
```java
lineToXLinearHeading()
lineToYLinearHeading()
strafeToLinearHeading()
splineToLinearHeading()
```

### Spline Heading
The heading changes in accordance with the spline throughout a trajectory. The start heading is simply the current heading (end heading of previous trajectory movement). The end heading is specified in the trajectory function.

#### Examples
```java
lineToXSplineHeading()
lineToYSplineHeading()
strafeToSplineHeading()
splineToSplineHeading()
```

## Trajectory Builder Tangents
### Start and End Tangents
These are used to specify the starting and ending tangent of a trajectory.

The starting tangent can be specified with `setTangent()` and the end tangent is specified in the trajectory function as a parameter. A demonstration of this behavior is shown below.


### Examples

:::warning
The video demonstrations are shown from the point of view of the audience which means the x-axis is vertical.
:::

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
  <video controls src="https://rr-playground-server.brott.dev/f05701f3-2d3e-4e69-8311-4eaa8926320d.mp4" title="Title" height="400px"></video>
  ### Explanation
  This function moves to the coordinates (-50, 50) with an end heading of `Math.toRadians(0.0)` and an end tangent of `Math.toRadians(-90.0)`. When a begin tangent, the current heading is used. In this case that is the heading stored in `beginPose` which is `Math.toRadians(45.0)`.
  ```java
  .splineToSplineHeading(new Pose2d(-50.0, 50.0, Math.toRadians(0.0)), Math.toRadians(-90.0))
  ```
</details>