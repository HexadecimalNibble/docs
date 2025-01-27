---
sidebar_position: 3
---

# Trajectories and Actions
Trajectories and Actions are used extensively when creating a Roadrunner-based autonomous but what are they?

## Trajectory
Simply put, trajectories store a series of movements to be executed by the robot. The following code demonstrates the creation of a trajectory in Roadrunner that moves forward 45 inches. The trajectory builder syntax will be explained later on.
```java
// Create a trajectory
TrajectoryActionBuilder traj = drive.actionBuilder(new Pose2d(0, 0, 0))
  .lineTo(new Vector2d(0, 45));
```

## Action
Lorem ipsum