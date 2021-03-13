---
title: "Adding Datastores"
linkTitle: "Adding Datastores"
date: 2021-02-13
weight: 2
description: >
  Kaspian supports popoular SQL databases and AWS S3 as datastores
---

## Postgres, Aurora, and Redshift
Kaspian supports data ingest from most Postgres-compatible data stores. Simply select the `Postgres` engine and fill out the form that appears.

{{< figure src="postgres_datastore.png" width="850px">}}

* __Datastore Name:__ Name by which you will refer to this SQL datastore
* __Host:__ Host name or IP address of the SQL datastore
* __Port:__ Port number of the SQL datastore
* __User:__ Username used to connect to the SQL datastore
* __Password:__ Password for the user to connect to the SQL datastore
* __Database:__ Database this connection will used for in the SQL datastore

### Support for SSH Tunneling via Bastion host
For SQL databases, SSH tunneling is also supported through Bastion host servers. To configure this, simply provide enable `Use Bastion Host` and provide the corresponding connection details. You must upload a `.pem` file with the private key to connect to the Bastion host.

{{< imgproc bastion_host Fit "850x450" >}}
{{< /imgproc >}}

* __Bastion User:__ Username used to SSH into the Bastion host
* __Bastion Host:__ Host name or IP address of the Bastion host
* __Bastion Port:__ Port number of the Bastion host
* __Private Key:__ `.pem` file containing the private key used to SSH into the Bastion host

Note, SSH tunneling to a SQL datastore will add additional latency to the SQL statements that are run

## Snowflake
Kaspian data pipelines also support data ingest via SQl from Snowflake data stores.

{{< figure src="snowflake_datastore.png" width="850px">}}

* __Datastore Name:__ Name by which you will refer to this Snowflake datastore
* __Account:__ Snowflake full account URL, e.g., `xy12345.us-east-1.snowflakecomputing.com`
* __User:__ Username used to connect to the Snowflake datastore
* __Password:__ Password for the user to connect to the Snowflake datastore
* __Warehouse:__ Specifies the virtual warehouse to use once connected. The specified warehouse should be an existing warehouse for which the specified default role has privileges.
* __Role:__ Specifies the default access control role to use in the Snowflake session. Ensure this role is assigned to the user
* __Database:__ Specifies the default database to use once connected

Kaspian currently does not support SSH tunneling to Snowflake datastores.

## AWS S3
Data can also be ingested directly from Parquet or CSV files on AWS S3. 

{{< figure src="s3_datastore.png" width="850px">}}

* __Name:__ Name by which you will refer to this S3 datastore
* __Path:__ S3 path this datastore is located at, e.g., `s3://<bucket>/<path>/<to>/<file or folder>`
* __Data Format:__ Format of the data located at the provided S3 path. Currently, `Parquet` and `CSV` are supported. If `CSV`, an additional dropdown will appear to indicate whether the CSV file contains a header row.
* __Schema:__ Dropdown to indicate the Kaspian schema that defines the data stored at the S3 path
* __AWS Integration:__ Dropdown to select AWS Role ARN used to access this S3 datastore (currently only 1 ARN role is supported at a time per account)
