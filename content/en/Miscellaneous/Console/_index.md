---
title: "SQL Query Console"
date: 2021-02-13
weight: 1
description: >
  The query console allows you to create and share worksheets for running SQL on datastores.
---

## Running SQL queries
Kaspian provides a fully-featured query console for users to run SQL statements on their connected SQL databases.

{{< figure src="query_console.png" width="850px">}}

The query console comes with 3 main components: a workspace for writing SQL queries, a database inspector, and a query preview table.

### Workspace
Switching to the Workspace view changes the left-hand panel to the following.

{{< figure src="workspace.png" width="350px">}}

Kaspian provides two folders for saving your SQL worksheets. The Personal folder includes all SQL scripts that only the given user can view. The Shared folder allows SQL scripts to be shared across your organization. Files can be dragged between these folders to change their visibility. Currently Kaspian only supports saving SQL files, but support is coming for other file-types and for allowing file uploads.

### Datastore Tree
Switching to the Datastores view will bring up a hierarchical view of a given SQL database.

{{< figure src="datastores.png" width="350px">}}

By expanding the tree, Kaspian provides metadata about the structure of your database down to the individual column names and types.

### Query preview
At the bottom of the console, when a SELECT statement has finished executing, a preview of the resulting data is shown. This data can be downloaded as a CSV and is automatically limited to the first 1,000,000 rows of the query.
