---
sidebar_position: 8
---

# Common Issues
This page will offer solutions to some common issues and errors experienced with Roadrunner 1.0.

TODO: PUT THAT lineTo STRAFING ERROR

## Path tangent orthogonal to the x-axis, try using lineToY() instead
## Path tangent orthogonal to the y-axis, try using lineToX() instead
### The Issue
These errors both occur when using a lineTo function when the robot is not facing straight (it is trying to strafe).

### Solution
In order to address this error, you could either use strafeTo instead of lineTo or change your start heading to face the direction of your path.