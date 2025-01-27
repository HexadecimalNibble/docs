---
sidebar_position: 4
---

# Action Reference

This page lists common Roadrunner Actions along with a description and demonstration of them. Please see the official Roadrunner [docs](https://rr.brott.dev/docs/v1-0/actions/) page on actions for more information on implementing the actions in your program.

## Built-in Actions

### SequentialAction
<details>
  <summary><strong>Parameters</strong></summary>
  ##### SequentialAction(Action actions)
  ##### SequentialAction(List\<Action\> initialActions)
</details>

Executes actions one after another (sequentially).

```java
Action awesomeAction = new SequentialAction(
  coolActionHere,
  otherCoolAction
);
```

### ParallelAction
<details>
  <summary><strong>Parameters</strong></summary>
  ##### ParallelAction(Action actions)
  ##### ParallelAction(List\<Action\> initialActions)
</details>

Executes multiple actions at the same time. Action terminates when <strong>all</strong> actions finish.

```java
Action awesomeAction = new ParallelAction(
  actionOne,
  actionExecutedAtSameTime
);
```

### RaceAction
<details>
  <summary><strong>Parameters</strong></summary>
  ##### RaceActionAction(Action actions)
  ##### RaceActionAction(List\<Action\> initialActions)
</details>

Executes multiple actions at the same time. Action terminates as soon as <strong>one</strong> action finishes.

```java
Action awesomeAction = new RaceAction(
  reallySlowAction,
  reallyQuickAction // The RaceAction will finish whenever the first action returns.
);
```

### SleepAction
<details>
  <summary><strong>Parameters</strong></summary>
  ##### SleepAction(Action actions)
  ##### SleepAction(List\<Action\> initialActions)
</details>

```java
CODE HERE
```

### InstantAction
<details>
  <summary><strong>Parameters</strong></summary>
  ##### InstantAction(InstantFunction f)
</details>

Action that instantly runs. This is useful for servo movements because we don't know when the servo gets to its target position (this could be used in a SequentialAction with a delay).

```java
// Action immediately returns
Action awesomeAction = new InstantAction(
  coolAction,
  reallyCoolAction
);
```

### NullAction
Does nothing. This action can be used when ???. TODO: FINISH THIS

```java
Action boringAction = new NullAction()
```

## Custom Actions

See [https://rr.brott.dev/docs/v1-0/actions/#custom-actions](https://rr.brott.dev/docs/v1-0/actions/#custom-actions).

TODO: MAKE THIS SECTION
