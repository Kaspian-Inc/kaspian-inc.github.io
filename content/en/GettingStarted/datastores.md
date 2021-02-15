---
title: "Adding Datastores"
date: 2020-02-13
weight: 2
description: >
  Kaspian supports popoular SQL databases and AWS S3 as datastores
---

## Postgres, Aurora, and Redshift
Kaspian supports data ingest from most Postgres-compatible data stores, including those that require SSH tunneling via a Bastion host. Simply provide the requested connection parameters.

Detailed explanation of each of those params

## Snowflake
Kaspian data pipelines also support data ingest via SQl from Snowflake data stores.

## AWS S3
Data can also be ingested directly from Parquet or CSV files on AWS S3. 
