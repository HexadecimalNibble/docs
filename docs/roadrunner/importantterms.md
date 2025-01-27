---
sidebar_position: 2
---

# Important Terms to Know

## Heading
Heading refers to the direction that the robot is facing. In Roadrunner, headings are measured in [radians](https://en.wikipedia.org/wiki/Radian). For example, a heading of *0* indicates the robot is facing to the right. A heading of *Pi / 2* indicates the robot is facing forward.

## Vector2D
<details>
  <summary><strong>Parameters</strong></summary>
  ##### Vector2d(Double x, Double y)
</details>
Stores x and y coordinates.

```java
new Vector2D()
```

## Pose2D
<details>
  <summary><strong>Parameters</strong></summary>
  ##### Pose2d(Vector2d position, Double heading)	
  ##### Pose2d(Double positionX, Double positionY, Double heading)	
  ##### Pose2d(Vector2d position, Rotation2d heading)
</details>
Stores x and y coordinates and a heading.

```java
new Pose2D()
```