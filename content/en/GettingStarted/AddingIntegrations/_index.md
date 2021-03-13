---
title: "Adding Integrations"
linkTitle: "Adding Integrations"
date: 2021-02-13
weight: 1
description: >
  Kaspian supports integrations with several external services, including AWS, Github, and Slack.
---

## Amazon Web Services (AWS)
Kaspian relies on an existing AWS account where it will host the compute and some elements of data storage. An IAM role for Kaspian services to assume should be created to facilitate this. The IAM Role ARN and AWS region are required for Kaspian to function.

<!-- ![AWS Integration](/aws_integration.png) -->

{{< figure src="aws_integration.png" width="850px">}}

The role ARN should have the following policies to access services from your account:
* `AmazonEC2ReadOnlyAccess`
* A custom policy allowing AWS STS AssumeRole permissions. The following JSON policy template can be used
```
{
    "Version": "2012-10-17",
    "Statement": {
        "Effect": "Allow",
        "Action": "sts:AssumeRole",
        "Resource": "arn:aws:iam::<Amazon account id>:role/*"
    }
}
```
* A custom policy allowing access to your staging bucket. The following JSON policy template can be used
```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "VisualEditor0",
            "Effect": "Allow",
            "Action": [
                "s3:*"
            ],
            "Resource": [
                "arn:aws:s3:::<S3 staging bucket>",
                "arn:aws:s3:::<S3 staging bucket>/*"
            ]
        }
    ]
}
```
* In addition, this role requires a few cross-account access policies to have access to Kaspian-specific resources. Please contact us for instructions on setting this up.

Support for Google Cloud Platform (GCP) and Microsoft Azure is coming soon.

## Github
Code storage for Kaspian pipelines is primarily handled via Github. In order to access the Github repo, Kaspian needs a Github personal access token (PAT) with read permissions for the account. This is a required piece of information.

{{< figure src="github_integration.png" width="850px">}}

Instructions to create a personal access token can be found [here](https://docs.github.com/en/github/authenticating-to-github/creating-a-personal-access-token). Only `repo` permissions need to be provided.

## Slack
An optional integration is support for Slack channel notifications of pipeline failures. Provide an access token for the desired Slack workspace to enable the ability to receive Slack messages when scheduled pipelines encounter errors.

{{< figure src="slack_integration.png" width="850px">}}

To receive notifications over Slack refer to these [instructions](https://api.slack.com/authentication/basics) to make a custom Slack App. This can be called whatever you wish. When configuring the scope for the app, at a minimum, you will need to provide `channels:join`, `channels:read`, and `chat:write` permissions as the Bot Token Scope. Once the App is created and linked to your Slack workspace, you can pick specific channels to give it access. Then, simply copy the access token from the App and provide it to Kaspian. Kaspian will automatically be able to detect which channels you the App has access to. You can configure which one receives the notification when setting up a pipeline.
