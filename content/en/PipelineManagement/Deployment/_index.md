---
title: "Deployment"
linkTitle: "Deployment"
date: 2021-02-13
weight: 2
description: >
  Pipelines are easily deployed in a few clicks.
---

## Setting a Schedule
Schedules can be configured via a number of pre-defined intervals or a custom one defined by a user-provided 5-character cron string. This is compatible with the standard cron spec and can be generated via cron string calculators available [online](https://crontab.guru/).

{{< figure src="schedule.png" width="450px">}}

## Configuring Notifications
Notifications can be configured to trigger on any pipeline exeuction failure. Kaspian offers support for Slack, email, and text notifications. These can be selected via the `Notifications` dropdown.

{{< figure src="notifications.png" width="450px">}}

## Pipeline Actions
There are 2 main modes for a pipeline: an `Activated` state and a `Deactivated` state. When a pipeline is activated, it will run at the specified schedule. When a pipeline is inactive, it will not run. When activating a pipeline, a pop-up appears to select a specific pipeline snapshot. Only pipeline snapshots can be activated, so one must be created first.

{{< figure src="pipeline_actions.png" width="850px">}}

In the activated state, a pipeline can be started ad-hoc at any point in time. In addition, a currently-running pipeline can be stopped at any time.

Previous pipeline executions are depicted as a series of colored dots within the same row as each active Pipeline. The colors correspond to the following statuses:
* Blue: currently executing
* Red: failed
* Green: succeeded
* Gray: cancelled

Each dot can be clicked to visit the Inspector view of that specific execution.
