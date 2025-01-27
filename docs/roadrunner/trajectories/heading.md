---
sidebar_position: 1
---

# Trajectory Builder Heading
Lorem ipsum.

### Constant Heading
Constant heading trajectories keep the heading the same throughout the trajectory.

:::tip Notice
The start and end trajectory actually change the start and end [tangent](https://en.wikipedia.org/wiki/Tangent) lines of the spline.
:::
### Linear Heading
Heading changes linearly throughout a trajectory from a start heading to an end heading. The start heading can be specified with a setTangent() function before the trajectory movement otherwise it is the heading from the end of the previous trajectory CHECK THIS. The end heading is specified in the trajectory function.

### Spline Heading
Heading changes in accordance with a spline throughout a trajectory. The start heading can be specified with a setTangent() function before the trajectory movement otherwise it is the heading from the end of the previous trajectory CHECK THIS. The end heading is specified in the trajectory function.