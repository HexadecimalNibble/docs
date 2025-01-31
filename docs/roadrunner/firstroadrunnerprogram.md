---
sidebar_position: 6
---

# Making Your First Roadrunner Program
This page will walk you through the creation of a simple Roadrunner program. If you have not yet downloaded Roadrunner, see [here](/roadrunner/about#installation).

## Imports
The first lines of code needed in every Roadrunner program are the import statements. These will vary based on what you are programming and generally [IDEs](https://en.wikipedia.org/wiki/Integrated_development_environment) like Android Studio will automatically add them. But, for demonstration purposes, we will import these.
```java
import com.acmerobotics.roadrunner.Pose2d;
import com.acmerobotics.roadrunner.Vector2d;
import com.acmerobotics.roadrunner.ftc.Actions;
import com.qualcomm.robotcore.eventloop.opmode.LinearOpMode;
import org.firstinspires.ftc.teamcode.roadrunner.MecanumDrive;
```

## Starting Pose
Next, you need to specify a starting pose. This is used in the creation of the Mecanum Drive class (next step) to tell Roadrunner where it is starting. This should be modified to your starting position in autonomous. In the following code, the starting position is set to a coordinate of *(0.0, -54.0)* facing forward (a heading of *90.0°*).
:::tip Notice
Be careful to make sure your starting heading is specified in radians. You can do this with either a `Math.toRadians()` function call or by specifying the heading in radians manually like `Math.PI`.
:::
```java
Pose2d beginPose = new Pose2d(0.0, -54.0, Math.toRadians(90.0));
```

## Mecanum Drive
After creating a starting pose, you can then create an instance of the Roadrunner Mecanum Drive class. `beginPose`, the variable we just created, is passed into MecanumDrive specifying the starting pose of the robot.
```java
MecanumDrive drive = new MecanumDrive(hardwareMap, beginPose);
```

## Variables
Next, you can create a variable to store the trajectory that the robot will follow and a variable to store the action to run this trajectory.
```java
TrajectoryActionBuilder traj;
Action trajAction;
```

## Trajectory Creation
We then create the trajectory itself. This consists of the following actions.
Strafing to the coordinate *(72.0, -54.0)*.
Setting the start tangent for the next movement to 90.0°.
Moving in a spline to the coordinate *(0.0, 0.0)* with an end tangent of 90.0°.
```java
traj = drive.actionBuilder(drive.pose)
  // Put your movements here
  .strafeTo(Vector2d(72.0, -54.0))
  .setTangent(Math.toRadians(90.0))
  .splineToConstantHeading(Vector2d(0.0, 0.0), Math.toRadians(90.0))
```

## Trajectory Action
Finally, we build the trajectory into an Action and execute that action.
```java
trajAction = traj.build()

Actions.runBlocking(trajAction);
```


## Putting it all together
Here is the completed code.
```java
import com.acmerobotics.roadrunner.Pose2d;
import com.acmerobotics.roadrunner.Vector2d;
import com.acmerobotics.roadrunner.ftc.Actions;
import com.qualcomm.robotcore.eventloop.opmode.LinearOpMode;
import org.firstinspires.ftc.teamcode.roadrunner.MecanumDrive;

public class MyOpmode extends LinearOpMode {
  @Override
  public void runOpMode() {
    // Specify a starting pose
    Pose2d beginPose = new Pose2d(0.0, -54.0, Math.toRadians(90.0));

    // Create an instance of the Mecanum Drive class
    MecanumDrive drive = new MecanumDrive(hardwareMap, beginPose);

    // Create variables to store the Trajectory and Action
    TrajectoryActionBuilder traj;
    Action trajAction;

    // Create a Trajectory
    traj = drive.actionBuilder(drive.pose)
      // Put your functions here
      .strafeTo(Vector2d(72.0, -54.0))
      .setTangent(Math.toRadians(90.0))
      .splineToConstantHeading(Vector2d(0.0, 0.0), Math.toRadians(90.0))

    // Create an action that follows the created trajectory
    trajAction = traj.build()

    // Run the action
    Actions.runBlocking(trajAction);
  }
}
```

## Demonstration
This video shows a demonstration of this program.

<video controls src="https://rr-playground-server.brott.dev/a108ce58-7a40-4653-b257-3e51491edcf7.mp4" title="Title" height="400px"></video>