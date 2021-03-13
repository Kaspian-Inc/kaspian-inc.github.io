---
title: "Construction"
linkTitle: "Construction"
date: 2021-02-13
weight: 1
description: >
  Pipelines can be constructed via a simple UI.
---

From the Task and Schema view, you can enter the pipeline builder view by pressing the `Graph` button as shown.

{{< figure src="pipelines_toggle_graph.png" width="850px">}}

## Assembling the pipeline
Pipelines are assembled via the `Pipelines` tab. Here, you can organize Tasks as nodes on a DAG. 

{{< figure src="dag_ui.png" width="850px">}}

The available bank of tasks for a given pipeline are shown in the list on the bottom right. Click `Add` next to each Task to add it to the Pipeline Builder. Click and drag to move the tasks around. Tasks can be connected together by pressing `Shift+Enter` while dragging from one Task to another. The Pipeline Builder will perform checks to ensure that any connection made is valid, e.g., the schemas match, no cycles, etc.

## Versioning
Pipeline snapshots are static, permanently fixed versions of a given pipeline. Press the `Snapshot` button above the Pipeline Builder to take a snapshot. These snapshots can then be deployed at the specified schedule from the `Overview` tab.
