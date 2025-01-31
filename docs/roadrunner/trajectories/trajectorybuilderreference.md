---
sidebar_position: 3
---

# TrajectoryBuilder Reference

This page lists common Roadrunner TrajectoryBuilder functions along with a description and demonstration of them. All of the functions listed below should be put inside a trajectoryBuilder which could then be created into an action and run. The following code shows a demonstration of how the following trajectories could be run.

:::warning Notice
This page only covers functions for the TrajectoryBuilder. TrajectoryActionBuilder includes these functions along with other ones for turning and other actions.
TODO: Should we make a separate page for this? Also build() technically not TrajectoryBuilder function.
:::

```java
Pose2d beginPose = new Pose2d(-16.0, -55.0, Math.toRadians(90.0));
MecanumDrive drive = new MecanumDrive(hardwareMap, beginPose);

TrajectoryActionBuilder traj;
Action trajAction;

traj = drive.actionBuilder(drive.pose)
  // Put your functions here
  .strafeTo(new Vector2d(30.0, 10.0))
  .strafeTo(new Vector2d(-30.0, -10.0));

trajAction = traj.build()

// Run trajectory
Actions.runBlocking(trajAction);
```
:::warning Be careful
The video demonstrations of the commands shown below are shown from the point of view of the audience which means the x-axis is vertical.
:::

## setTangent()
<details>
  <summary><strong>Parameters</strong></summary>
  ##### setTangent(Rotation2d r)
  ##### setTangent(Double r)
</details>

```java
// Sets the tangent to 90°
// This is used to specify the start tangent of the next movement command
.setTangent(Math.toRadians(90.0))
```

## setReversed()
<details>
  <summary><strong>Parameters</strong></summary>
  ##### setReversed(Boolean reversed)
</details>
This internally calls `setTangent(180.0)`.

```java
// Run trajectory with robot facing opposite direction (backwards)
.setReversed(true)
```

<br></br>
<br></br>

:::warning Be Careful of Starting Heading
`lineToX()` and `lineToY()` do not allow strafing. Therefore, these functions should be avoided in favor of `strafeTo()`. See [this](../commonissues.md#path-tangent-orthogonal-to-the-x-axis-try-using-linetoy-instead) section on the Common Issues page for more details.
:::

:::tip Notice
  The behavior of all of the below lineTo functions are the same when the heading does not change.
:::
## lineTo commands
<details>
  <summary><strong>lineToX(),	lineToXConstantHeading(),	lineToXLinearHeading(), lineToXSplineHeading()<br></br>lineToY(),	lineToYConstantHeading(),	lineToYLinearHeading(), lineToYSplineHeading()</strong></summary>

  ### lineToX()
  <details>
    <summary><strong>Parameters</strong></summary>
    ##### lineToX(Double posX, VelConstraint velConstraintOverride, AccelConstraint accelConstraintOverride)
    ##### lineToX(Double posX, VelConstraint velConstraintOverride)
    ##### lineToX(Double posX)
  </details>

  ```java
  // Drive to an x-value of 25.0
  .lineToX(25.0)
  ```
  <video controls src="https://rr-playground-server.brott.dev/3ee477b3-aa4b-4be3-a43b-778964ad8023.mp4" title="Title" height="400px"></video>

  ### lineToXConstantHeading()
  <details>
    <summary><strong>Parameters</strong></summary>
    ##### lineToXConstantHeading(Double posX, VelConstraint velConstraintOverride, AccelConstraint accelConstraintOverride)	
    ##### lineToXConstantHeading(Double posX, VelConstraint velConstraintOverride)	
    ##### lineToXConstantHeading(Double posX)
  </details>

  ```java
  // Drive to an x-value of 25.0, keeping the heading constant
  .lineToXConstantHeading(25.0)
  ```

  ### lineToXLinearHeading()
  <details>
    <summary><strong>Parameters</strong></summary>
    ##### lineToXLinearHeading(Double posX, Rotation2d heading, VelConstraint velConstraintOverride, AccelConstraint accelConstraintOverride)	
    #####	lineToXLinearHeading(Double posX, Rotation2d heading, VelConstraint velConstraintOverride)	
    #####	lineToXLinearHeading(Double posX, Rotation2d heading)	
    #####	lineToXLinearHeading(Double posX, Double heading, VelConstraint velConstraintOverride, AccelConstraint accelConstraintOverride)	
    #####	lineToXLinearHeading(Double posX, Double heading, VelConstraint velConstraintOverride)	
    #####	lineToXLinearHeading(Double posX, Double heading)
  </details>

  ```java
  // Drive to an x-value of 25.0, changing the heading linearly
  .lineToXLinearHeading(25.0, Math.toRadians(90.0))
  ```

  ### lineToXSplineHeading()
  <details>
    <summary><strong>Parameters</strong></summary>
    ##### lineToXSplineHeading(Double posX, Rotation2d heading, VelConstraint velConstraintOverride, AccelConstraint accelConstraintOverride)	
    #####	lineToXSplineHeading(Double posX, Rotation2d heading, VelConstraint velConstraintOverride)	
    #####	lineToXSplineHeading(Double posX, Rotation2d heading)	
    #####	lineToXSplineHeading(Double posX, Double heading, VelConstraint velConstraintOverride, AccelConstraint accelConstraintOverride)	
    #####	lineToXSplineHeading(Double posX, Double heading, VelConstraint velConstraintOverride)	
    #####	lineToXSplineHeading(Double posX, Double heading)
  </details>

  ```java
  // Drive to an y-value of 25.0, changing the heading according to a spline
  .lineToXSplineHeading(25.0, Math.toRadians(90.0))
  ```

  ### lineToY()
  <details>
    <summary><strong>Parameters</strong></summary>
    ##### lineToY(Double posY, VelConstraint velConstraintOverride, AccelConstraint accelConstraintOverride)
    ##### lineToY(Double posY, VelConstraint velConstraintOverride)
    ##### lineToY(Double posY)
  </details>

  ```java
  // Drive to an y-value of 25.0
  .lineToY(25.0)
  ```

  ### lineToYConstantHeading()
  <details>
    <summary><strong>Parameters</strong></summary>
    ##### lineToYConstantHeading(Double posY, VelConstraint velConstraintOverride, AccelConstraint accelConstraintOverride)	
    ##### lineToYConstantHeading(Double posY, VelConstraint velConstraintOverride)	
    ##### lineToYConstantHeading(Double posY)
  </details>

  ```java
  // Drive to an y-value of 25.0, keeping the heading constant
  .lineToYConstantHeading(25.0)
  ```

  ### lineToYLinearHeading()
  <details>
    <summary><strong>Parameters</strong></summary>
    ##### lineToYLinearHeading(Double posY, Rotation2d heading, VelConstraint velConstraintOverride, AccelConstraint accelConstraintOverride)	
    #####	lineToYLinearHeading(Double posY, Rotation2d heading, VelConstraint velConstraintOverride)	
    #####	lineToYLinearHeading(Double posY, Rotation2d heading)	
    #####	lineToYLinearHeading(Double posY, Double heading, VelConstraint velConstraintOverride, AccelConstraint accelConstraintOverride)	
    #####	lineToYLinearHeading(Double posY, Double heading, VelConstraint velConstraintOverride)	
    #####	lineToYLinearHeading(Double posY, Double heading)
  </details>

  ```java
  // Drive to an y-value of 25.0, linearly changing the heading
  .lineToYLinearHeading(25.0, Math.toRadians(90.0))
  ```

  ### lineToYSplineHeading()
  <details>
    <summary><strong>Parameters</strong></summary>
    ##### lineToYSplineHeading(Double posY, Rotation2d heading, VelConstraint velConstraintOverride, AccelConstraint accelConstraintOverride)	
    #####	lineToYSplineHeading(Double posY, Rotation2d heading, VelConstraint velConstraintOverride)	
    #####	lineToYSplineHeading(Double posY, Rotation2d heading)	
    #####	lineToYSplineHeading(Double posY, Double heading, VelConstraint velConstraintOverride, AccelConstraint accelConstraintOverride)	
    #####	lineToYSplineHeading(Double posY, Double heading, VelConstraint velConstraintOverride)	
    #####	lineToYSplineHeading(Double posY, Double heading)
  </details>

  ```java
  // Drive to an y-value of 25.0, changing the heading according to a spline
  .lineToYSplineHeading(25.0, Math.toRadians(90.0))
  ```
</details>

## strafeTo commands
<details>
  <summary><strong>strafeTo(), strafeToConstantHeading(), strafeToLinearHeading(), strafeToSplineHeading()</strong></summary>

  ### strafeTo()
  <details>
    <summary><strong>Parameters</strong></summary>
    ##### strafeTo(Vector2d pos, VelConstraint velConstraintOverride, AccelConstraint accelConstraintOverride)	
    #####	strafeTo(Vector2d pos, VelConstraint velConstraintOverride)	
    #####	strafeTo(Vector2d pos)
  </details>

  ```java
  // Strafe to (24.0, 24.0), keeping the heading the same
  .strafeToConstantHeading(new Vector2d(24.0, 24.0))
  ```

  ### strafeToConstantHeading()
  <details>
    <summary><strong>Parameters</strong></summary>
    ##### strafeToConstantHeading(Vector2d pos, VelConstraint velConstraintOverride, AccelConstraint accelConstraintOverride)	
    #####	strafeToConstantHeading(Vector2d pos, VelConstraint velConstraintOverride)	
    #####	strafeToConstantHeading(Vector2d pos)
  </details>
  idk what is difference between strafeToConstantHeading() and strafeTo()?

  ```java
  // Strafe to (24.0, 24.0), keeping the heading constant
  .strafeToConstantHeading(new Vector2d(24.0, 24.0))
  ```

  ### strafeToLinearHeading()
  <details>
    <summary><strong>Parameters</strong></summary>
    ##### strafeToLinearHeading(Vector2d pos, Rotation2d heading, VelConstraint velConstraintOverride, AccelConstraint accelConstraintOverride)	
  	##### strafeToLinearHeading(Vector2d pos, Rotation2d heading, VelConstraint velConstraintOverride)	
    #####	strafeToLinearHeading(Vector2d pos, Rotation2d heading)	
    #####	strafeToLinearHeading(Vector2d pos, Double heading, VelConstraint velConstraintOverride, AccelConstraint accelConstraintOverride)	
    #####	strafeToLinearHeading(Vector2d pos, Double heading, VelConstraint velConstraintOverride)	
    #####	strafeToLinearHeading(Vector2d pos, Double heading)
  </details>

  ```java
  // Strafe to (24.0, 24.0), changing the heading linearly
  .strafeToLinearHeading(new Vector2d(24.0, 24.0), Math.toRadians(0.0))
  ```

  ### strafeToSplineHeading()
  <details>
    <summary><strong>Parameters</strong></summary>
    ##### strafeToSplineHeading(Vector2d pos, Rotation2d heading, VelConstraint velConstraintOverride, AccelConstraint accelConstraintOverride)	
    #####	strafeToSplineHeading(Vector2d pos, Rotation2d heading, VelConstraint velConstraintOverride)	
    #####	strafeToSplineHeading(Vector2d pos, Rotation2d heading)	
    #####	strafeToSplineHeading(Vector2d pos, Double heading, VelConstraint velConstraintOverride, AccelConstraint accelConstraintOverride)	
    #####	strafeToSplineHeading(Vector2d pos, Double heading, VelConstraint velConstraintOverride)	
    #####	strafeToSplineHeading(Vector2d pos, Double heading)
  </details>

  ```java
  // Strafe to (24.0, 24.0), changing the heading according to a spline
  .strafeToSplineHeading(new Vector2d(24.0, 24.0), Math.toRadians(0.0))
  ```
</details>

## splineTo commands
<details>
  <summary><strong>splineTo(), splineToConstantHeading(), splineToLinearHeading(), splineToSplineHeading()</strong></summary>

  ### splineTo()
  <details>
    <summary><strong>Parameters</strong></summary>
    ##### splineTo(Vector2d pos, Rotation2d tangent, VelConstraint velConstraintOverride, AccelConstraint accelConstraintOverride)	
    #####	splineTo(Vector2d pos, Rotation2d tangent, VelConstraint velConstraintOverride)	
    #####	splineTo(Vector2d pos, Rotation2d tangent)	
    #####	splineTo(Vector2d pos, Double tangent, VelConstraint velConstraintOverride, AccelConstraint accelConstraintOverride)	
    #####	splineTo(Vector2d pos, Double tangent, VelConstraint velConstraintOverride)	
    #####	splineTo(Vector2d pos, Double tangent)
  </details>

  ```java
  // Spline to (24, 24) with an ending tangent of 0.0, changing the heading with the spline
  .splineTo(new Vector2d(24.0, 24.0), Math.toRadians(0.0))
  ```

  ### splineToConstantHeading()
  <details>
    <summary><strong>Parameters</strong></summary>
    ##### splineToConstantHeading(Vector2d pos, Rotation2d tangent, VelConstraint velConstraintOverride, AccelConstraint accelConstraintOverride)	
    #####	splineToConstantHeading(Vector2d pos, Rotation2d tangent, VelConstraint velConstraintOverride)	
    #####	splineToConstantHeading(Vector2d pos, Rotation2d tangent)	
    #####	splineToConstantHeading(Vector2d pos, Double tangent, VelConstraint velConstraintOverride, AccelConstraint accelConstraintOverride)	
    #####	splineToConstantHeading(Vector2d pos, Double tangent, VelConstraint velConstraintOverride)	
    #####	splineToConstantHeading(Vector2d pos, Double tangent)
  </details>

  ```java
  // Spline to (24, 24) with an ending tangent of 0.0, keeping the heading constant
  .splineToConstantHeading(new Vector2d(24.0, 24.0), Math.toRadians(0.0))
  ```

  ### splineToLinearHeading()
  <details>
    <summary><strong>Parameters</strong></summary>
    ##### splineToLinearHeading(Pose2d pose, Rotation2d tangent, VelConstraint velConstraintOverride, AccelConstraint accelConstraintOverride)	
    #####	splineToLinearHeading(Pose2d pose, Rotation2d tangent, VelConstraint velConstraintOverride)	
    #####	splineToLinearHeading(Pose2d pose, Rotation2d tangent)	
    #####	splineToLinearHeading(Pose2d pose, Double tangent, VelConstraint velConstraintOverride, AccelConstraint accelConstraintOverride)	
    #####	splineToLinearHeading(Pose2d pose, Double tangent, VelConstraint velConstraintOverride)	
    #####	splineToLinearHeading(Pose2d pose, Double tangent)
  </details>

  ```java
  // Spline to (24, 24) with an ending tangent of 0.0, linearly changing the heading from the previous heading to 90.0 degrees
  .splineToLinearHeading(new Pose2d(24.0, 24.0, Math.toRadians(90.0)), Math.toRadians(0.0))
  ```

  ### splineToSplineHeading()
  <details>
    <summary><strong>Parameters</strong></summary>
    ##### splineToSplineHeading(Pose2d pose, Rotation2d tangent, VelConstraint velConstraintOverride, AccelConstraint accelConstraintOverride)	
    #####	splineToSplineHeading(Pose2d pose, Rotation2d tangent, VelConstraint velConstraintOverride)	
    #####	splineToSplineHeading(Pose2d pose, Rotation2d tangent)	
    #####	splineToSplineHeading(Pose2d pose, Double tangent, VelConstraint velConstraintOverride, AccelConstraint accelConstraintOverride)	
    #####	splineToSplineHeading(Pose2d pose, Double tangent, VelConstraint velConstraintOverride)	
    #####	splineToSplineHeading(Pose2d pose, Double tangent)
  </details>

  ```java
  // Spline to (24, 24) with an ending tangent of 0.0, changing the heading from the previous heading to 90.0 degrees according to a spline
  .splineToSplineHeading(new Pose2d(24.0, 24.0, Math.toRadians(90.0)), Math.toRadians(0.0))
  ```
</details>

## build()
Used to assemble a trajectory into an action. This action can then be executed to run the trajectory.
```java
// Specify a starting pose
Pose2d beginPose = new Pose2d(-16.0, -55.0, Math.toRadians(90.0));

// Create an instance of the Mecanum Drive class
MecanumDrive drive = new MecanumDrive(hardwareMap, beginPose);

// Create a Trajectory
TrajectoryActionBuilder traj = drive.actionBuilder(drive.pose)
  // Put your functions here
  .strafeTo(new Vector2d(30.0, 10.0))
  .splineTo(new Vector2d(-30.0, -10.0));

// Create an action that follows the created trajectory
Action trajAction = traj.build()

// Run the action
Actions.runBlocking(trajAction);
```
