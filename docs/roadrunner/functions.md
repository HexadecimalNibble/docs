---
sidebar_position: 3
---

# TrajectoryBuilder Functions

This page lists common Roadrunner TrajectoryBuilder functions along with a description and demonstration of them. All of the functions listed below should be put inside a trajectoryBuilder which could then be created into an action and run.
```jsx
Pose2d beginPose = new Pose2d(-16, -55, Math.toRadians(90));
MecanumDrive drive = new MecanumDrive(hardwareMap, beginPose);

TrajectoryActionBuilder traj;
Action trajAction;

traj = drive.actionBuilder(drive.pose)
  // Put your functions here
  .strafeTo(new Vector2d(30, 10))
  .strafeTo(new Vector2d(-30, -10));

trajAction = traj.build()

// Run trajectory
Actions.runBlocking(trajAction);
```
:::warning Be careful
The video demonstrations of the commands shown below are shown from the point of view of the audience which means the x-value will go up.
:::

### setTangent()
<details>
  <summary><strong>Parameters</strong></summary>
  ##### setTangent(Rotation2d r)
  ##### setTangent(Double r)
</details>

```jsx
// sets the tangent to 90° (Pi radians)
.setTangent(Math.PI)
```

### setReversed()
<details>
  <summary><strong>Parameters</strong></summary>
  ##### setReversed(Boolean reversed)
</details>

```jsx
// run trajectory with robot facing opposite direction (backwards)
.setReversed(true)
```

<br></br>
<br></br>

:::warning Be careful
`lineToX()` and `lineToY()` functions should be avoided in favor of `strafeTo()`. This will prevent errors SHOW ERROR HERE.
:::

### lineToX()
<details>
  <summary><strong>Parameters</strong></summary>
  ##### lineToX(Double posX, VelConstraint velConstraintOverride, AccelConstraint accelConstraintOverride)
  ##### lineToX(Double posX, VelConstraint velConstraintOverride)
  ##### lineToX(Double posX)
</details>

```jsx
// drive to an x-value of 25
.lineToX(25)
```
<video controls src="https://rr-playground-server.brott.dev/3ee477b3-aa4b-4be3-a43b-778964ad8023.mp4" title="Title" height="400px"></video>

### lineToXConstantHeading()
<details>
  <summary><strong>Parameters</strong></summary>
  ##### lineToXConstantHeading(Double posX, VelConstraint velConstraintOverride, AccelConstraint accelConstraintOverride)	
  ##### lineToXConstantHeading(Double posX, VelConstraint velConstraintOverride)	
  ##### lineToXConstantHeading(Double posX)
</details>

```jsx
// drive to an x-value of 25
.lineToXConstantHeading(25)
```

### lineToXLinearHeading()
<details>
  <summary><strong>Parameters</strong></summary>
  ##### lineToXLinearHeading(Double posX, Rotation2d heading, VelConstraint velConstraintOverride, AccelConstraint accelConstraintOverride)	
  ##### lineToXLinearHeading(Double posX, Rotation2d heading, VelConstraint velConstraintOverride)	
  ##### lineToXLinearHeading(Double posX, Rotation2d heading)	
  ##### lineToXLinearHeading(Double posX, Double heading, VelConstraint velConstraintOverride, AccelConstraint accelConstraintOverride)	
  ##### lineToXLinearHeading(Double posX, Double heading, VelConstraint velConstraintOverride)	
  ##### lineToXLinearHeading(Double posX, Double heading)
</details>

```jsx
// drive to an x-value of 25
.lineToXConstantHeading(25)
```

### waitSeconds()

```jsx
// waits 5 seconds
.waitSeconds(5)
```
