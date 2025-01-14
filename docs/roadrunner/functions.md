---
sidebar_position: 2
---

# TrajectoryBuilder Functions

This page lists common Roadrunner TrajectoryBuilder functions along with a description and demonstration of them.

### setTangent()
<details>
  <summary><strong>Parameters</strong></summary>
  #### setTangent(Rotation2d r)
  #### setTangent(Double r)
</details>

```jsx
// sets the tangent to 90° (Pi radians)
.setTangent(Math.PI)
```

### setReversed()
<details>
  <summary><strong>Parameters</strong></summary>
  #### setReversed(Boolean reversed)
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
  #### lineToX(Double posX, VelConstraint velConstraintOverride, AccelConstraint accelConstraintOverride)
  #### lineToX(Double posX, VelConstraint velConstraintOverride)
  #### lineToX(Double posX)
</details>

```jsx
// drive to an x-value of 25
.lineToX(25)
```


### waitSeconds()

```jsx
// waits 5 seconds
.waitSeconds(5)
```
