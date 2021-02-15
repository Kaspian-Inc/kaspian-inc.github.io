---
title: "Tasks"
date: 2017-01-05
weight: 2
description: >
  Read, write, and transform
---
Tasks are the principal units of work in a Pipeline graph.
They enable data to be read in, transformed, and written back out to connected Datastores and thereby greatly 
simplify data manipulation in any environment at any scale.

[PICTURE OF EXAMPLE TASK]

The Task editor can be accessed via the Pipelines tab: after navigating to Pipelines,
the Components view and the Graph Builder view can be toggled using the top right button.

[PICTURE OF TAB TOGGLE BUTTON]

Like Schemas, Tasks can be scoped to specific Pipelines or be configured to have global scope
(i.e. used in any Pipeline). Scoping serves both to help organize Tasks and to facilitate their reuse
in different Pipelines. Note that while the scope of a Task cannot be changed after it has been created, 
Tasks can be cloned into other Pipeline scopes or into the global scope using the Task editor.

The editor also enables Tasks to be edited and deleted.
Tasks cannot be deleted until all Pipeline that use them are also deleted and 
Kaspian will present the user with the relevant dependency conflict chain if a delete operation is requested.

All Tasks require `name`, `type`, and `description` fields and the 
`name` field is required to be unique for Tasks of a given `type` within a given Pipeline.


## Data Readers
Data Readers are used to read data from registered Datastores.
As they are the only task with this capability, Data Readers serve as the root nodes for 
all Pipeline graphs. In a Pipeline graph, Data Readers may only have outbound edges.

[PICTURE OF DATA READER]

Additionally, Data Readers have the following fields:


**Source Datastore**: The datastore to read from.

**Code Source**: A link to a `.sql` file on GitHub. The SQL query must be Spark SQL compliant. 
The file can be on any branch in any repository so long as the connected GitHub integration 
[LINK GITHUB INTEGRATION] has read access to it. 
The SQL file contains the query to be run against the source Datastore in order to load in data.

[SQL CODE BLOCK]

For S3 datastores, note that the special constant `data` is used to indicate the table object 
(see above example).

**Output Schema**: The schema of the data produced by the query contained in the code source.

## Data Writers
Data Writers are used to write data to registered Datastores. As they are the only task with this capability,
Data Writers serve as the leaf (terminal) nodes for all Pipeline graphs. In a Pipeline graph,
Data Writers may only have inbound edges.

[PICTURE OF DATA WRITER]

Additionally, Data Writers have the following fields:

**Destination Datastore**: The Datastore to write to.

**Input Schema**: The Schema of the data being written to the specified Datastore. For S3 Datastores 
this should exactly match the Schema specified for that Datastore on the Datastore page.

**Write Mode**: A directive specifying the write mode behavior of the task. 
Data Writers can either `append` to or `overwrite` the specified table 
(or for S3 Datastores, the contents of the associated S3 path).

**Destination Table**: The Datastore table to write to.
This field is only enabled for SQL Datastores.
It is advisable to explicitly specify the full table path (`schema.table`). 

## SQL Transforms
SQL Transforms allow for the manipulation of data, either from outputs of other 
transformations or directly from Data Readers, using SQL.
This source-agnostic nature of the Kaspian execution engine means that a single SQL query is
capable of accessing and operating upon data from multiple Datastores and/or Pipeline branches. 
In a Pipeline graph, SQL Transforms may have any number of both inbound and outbound edges.

[PICTURE OF SQL TRANSFORM]

Additionally, Data Writers have the following fields:

**Output Schema**: The schema of the data produced by the query contained in the code source.

**Input Schemas**: Each inbound edge to a SQL Transform represents a different data source,
corresponding either to a Data Reader output or to an intermediate output of another transform Task.
In order to distinguish between these inbound edges when writing the transformation 
query each edge must be configured with an alias and a schema.

[PICTURE OF ALIASES NEXT TO DAG]

While the same schema can be used multiple times within a SQL Transform if the data sources being read from have
the same structure, aliases must be unique. An alias refers to the name that the input source table is referred to
in the SQL query contained in the code source (see example below). This abstraction means that any intermediate
data stage can be referred to and operated upon as if it were a materialized table even if this isn't the case.

**Code Source**: A link to a `.sql` file on GitHub.
The file can be on any branch in any repository so long as the connected GitHub integration
[LINK GITHUB INTEGRATION] has read access to it.
The SQL file contains the query to be run using the aliases provided in the Input Schemas as table names.
The query must be Spark SQL compliant.
Below is an example query that utilizes the aliases above:

[PICTURE OF QUERY THAT UTILIZES ALIASES PROVIDED]


## Python Function Transforms
## Python DataFrame Transforms
