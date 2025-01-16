---
sidebar_position: 4
---

# Making Your First Roadrunner Program
This page will walk you through the creation of a simple Roadrunner program. If you have not yet downloaded Roadrunner, see [here](/roadrunner/about#installation).

## Imports
The first lines of code needed in every Roadrunner program are the import statements. These will vary based on what you are programming and generally [IDEs](https://en.wikipedia.org/wiki/Integrated_development_environment) like Android Studio will automatically add them. But, for demonstration purposes, we will just import these.
```java
import com.acmerobotics.roadrunner.Pose2d;
import com.acmerobotics.roadrunner.Vector2d;
import com.acmerobotics.roadrunner.ftc.Actions;
import com.qualcomm.robotcore.eventloop.opmode.LinearOpMode;
import org.firstinspires.ftc.teamcode.roadrunner.MecanumDrive;
```

## Starting Pose
Next, you need to specify a starting pose. This is used in the creation of the Mecanum Drive class (next step) to tell Roadrunner where it is starting. This should be modified to your starting position in autonomous. In the following code, the starting position is set to a coordinate of *(-16, -55)* facing forward (a heading of *90°*).
:::tip Notice
Be careful to make sure your starting heading is specified in radians. You can do this with either a `Math.toRadians()` function call or by specifying the heading in radians manually like `Math.PI`.
:::
```java
Pose2d beginPose = new Pose2d(-16, -55, Math.toRadians(90));
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
We then create the trajectory itself. This consists of strafing to the coordinate *(30, 10)* and then moving in a spline to the coordinate *(-30, -10)*.
```java
traj = drive.actionBuilder(drive.pose)
  // Put your functions here
  .strafeTo(new Vector2d(30, 10))
  .splineTo(new Vector2d(-30, -10));
```

## Trajectory Action
Finally, we build the trajectory into an Action and execute that action.
```java
trajAction = traj.build()

Actions.runBlocking(trajAction);
```


## Putting it all together
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
      .splineTo(new Vector2d(-30, -10));

    // Create an action that follows the created trajectory
    trajAction = traj.build()

    // Run the action
    Actions.runBlocking(trajAction);
  }
}
```

## Demonstration
This video shows a demonstration of how this program would move the robot.

TODO: ADD VIDEO