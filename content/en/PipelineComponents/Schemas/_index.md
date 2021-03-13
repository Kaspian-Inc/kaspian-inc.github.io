---
title: "Schemas"
date: 2021-02-13
weight: 1
description: >
  Flexible data structures
---


Schemas define the structure of data at any point within a Pipeline graph.
Because they are required at every transformation within a graph, schemas ensure that 
Kaspian Pipelines are strongly typed and thereby protect the data integrity of downstream data sinks.

{{< figure src="schema.png" width="850px">}}

The Schema editor can be accessed via the Pipelines tab: after navigating to Pipelines,
the Components view and the Graph Builder view can be toggled using the top right button.

{{< figure src="pipelines_toggle_components.png" width="850px">}}

Like Tasks, Schemas can be scoped to specific Pipelines or be configured to have global scope
(i.e. used in any Pipeline). Scoping serves both to help organize Schemas and to facilitate 
their reuse in different Pipelines. Note that while the scope of a Schema cannot be changed 
after it has been created, Schemas can be cloned into other Pipelines scopes or into the global 
scope using the Schema editor.

The editor also enables Schema to be edited and deleted. 
Schemas cannot be deleted until all Tasks, Pipelines, and 
Datastores that use them are also deleted and Kaspian will present the user with the 
relevant dependency conflict chain if a delete operation is requested.


## Task Schemas

All Tasks have either an input Schema or an output Schema; many require both. 
The input Schema defines the structure of data entering a Task while the output Schema defines the 
structure of data exiting a Task.

{{< figure src="schema_field.png" width="850px">}}

A Schema consists of an ordered array of fields. 
A field has four elements: `name`, `description`, `datatype`, and `nullable`.
`name` refers to the column name being referenced. Note that this value must be unique within a given Schema. 
`description` is meant to provide a space for users to add any useful documentation about the field. 
`datatype` values must be selected from the following list of supported options:

|Datatype | Description                            |
|---------|----------------------------------------|
|ARRAY    |Array-type values                       |
|BINARY   |Binary values                           |
|BOOLEAN  |True or false values                    |
|BYTE     |Byte values                             |
|DATE     |Dates without time values               |
|DECIMAL  |Rational values with specified precision|
|DOUBLE   |Double precision values                 |
|FLOAT    |Floating point values                   |
|INTEGER  |Integer values                          |
|LONG     |32-bit signed integer values            |
|MAP      |Key-value pairs                         |
|SHORT    |16-bit signed integer values            |
|STRING   |Text or varchar values                  |
|TIMESTAMP|Dates with time(zone) values            |

In general, Kaspian is compatible with any datatype supported by Apache Spark and 
maps types from Datastores to this list the same way a Spark engine would.

The `nullable` flag is a boolean option that specifies if the value for that specific field is allowed to be null.
This option can serve as a valuable data integrity check for required fields.


## Datastore Schemas
Tables registered in flat file/data lake environments such as AWS S3 can be added as [Datastores]({{<ref "GettingStarted/AddingDatastores#aws-s3">}}). This abstraction allows these resources to behave identically to SQL Datastores such as Snowflake and Postgres within the Kaspian compute layer. Kaspian requires that these Datastores have a Schema attached so that data integrity can be programmatically enforced. It is recommended that Datastore Schemas have global scope so that they can be reused by other Pipelines.
