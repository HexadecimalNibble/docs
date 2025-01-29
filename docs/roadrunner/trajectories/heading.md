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
Heading changes in accordance with a spline throughout a trajectory. The start heading can be specified with a `setTangent()` function before the trajectory movement otherwise it is the heading from the end of the previous trajectory (see below) CHECK THIS. The end heading is specified in the trajectory function.

#### Examples
```java
lineToXSplineHeading()
lineToYSplineHeading()
strafeToSplineHeading()
splineToSplineHeading()
```

## Start and End Tangents
These are used to specify the heading of the start and end of a path.

The start heading or start tangent can be specified with `setTangent()` and the end heading or end tangent is specified in the trajectory function as a parameter. A demonstration of this behavior is shown below.

```java
finish
```