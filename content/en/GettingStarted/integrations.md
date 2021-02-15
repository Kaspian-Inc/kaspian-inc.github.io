---
title: "Adding Integrations"
date: 2020-02-13
weight: 1
description: >
  Kaspian supports integrations with several external services, including AWS, Github, and Slack.
---
## AWS
Kaspian relies on an existing AWS account where it will host the compute and some elements of data storage. An IAM role for Kaspian services to assume should be created to facilitate this. The Role ARN and AWS region are required for Kaspian to function.

## Github
Code storage for Kaspian pipelines is primarily handled via Github. In order to access the Github repo, Kaspian needs a Github personal access token (PAT) with read permissions for the account. This is a required piece of information.

## Slack
An optional integration is support for Slack channel notifications of pipeline failures. Provide an access token for the desired Slack workspace to enable the ability to receive Slack messages when scheduled pipelines encounter errors.
