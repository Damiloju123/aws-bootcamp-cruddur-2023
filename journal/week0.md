# Week 0 — Billing and Architecture

## AWS CLI

### Setting up AWS CLI
- Installed AWS CLI on Gitpod following the [AWS CLI Install Instructions](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html)
- Updated my .gitpod.yml to include the below:

```sh
tasks:
  - name: aws-cli
    env:
      AWS_CLI_AUTO_PROMPT: on-partial
    init: |
      cd /workspace
      curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
      unzip awscliv2.zip
      sudo ./aws/install
      cd $THEIA_WORKSPACE_ROOT
```

### Created a New User and Generated AWS Credentials

The steps below were used to accomplish this task

- Searched for IAM Users via the home Console
- Created a new `user` Damiloju
- Enabled console access for the `user` Damiloju
- Created a new `Admin` Group and apply `AdministratorAccess`
- Created the `user` and selected the `user`
- Selected the `Security Credentials` and `Create Access Key`
- Chose AWS CLI Access
- Downloaded the CSV with the credentials

![User Graphic](https://github.com/Damiloju123/aws-bootcamp-cruddur-2023/blob/3a2a0fad875a758d5e3b0c7b4a175b6b3ed0bb6c/_docs/assets/Users.JPG)


### Set the Environment Vars

The commands below were used to set the credentials via the bash terminal

```sh
tasks:
gp env AWS_ACCESS_KEY_ID=""
gp env AWS_SECRET_ACCESS_KEY=""
gp env AWS_DEFAULT_REGION=us-east-1
```

### Verification checks on AWS CLI & AWS User

```sh
aws sts get-caller-identity
```

![User Graphic](https://github.com/Damiloju123/aws-bootcamp-cruddur-2023/blob/3a2a0fad875a758d5e3b0c7b4a175b6b3ed0bb6c/_docs/assets/STS.JPG)

## Created AWS Budgets

## Created a Zero Sped Budget

This was done using the AWS Documentation [aws budgets create-budget](https://docs.aws.amazon.com/cli/latest/reference/budgets/create-budget.html)

- Provided my AWS Account ID
- Updated the json files

Ran the Command below

```sh
aws budgets create-budget \
    --account-id AccountID \
    --budget file://aws/json/budget.json \
    --notifications-with-subscribers file://aws/json/budget-notifications-with-subscribers.json
```

![User Graphic](https://github.com/Damiloju123/aws-bootcamp-cruddur-2023/blob/3a2a0fad875a758d5e3b0c7b4a175b6b3ed0bb6c/_docs/assets/Budget.JPG)


## Set up Billing & Created a Billing Alarm

To receive alerts the Billing Alerts has to be put on

This was done via the Root Account, under the `Billing Preferences` in the Billing Section

![User Graphic](https://github.com/Damiloju123/aws-bootcamp-cruddur-2023/blob/3a2a0fad875a758d5e3b0c7b4a175b6b3ed0bb6c/_docs/assets/Billing.JPG)



## Creating the Billing Alarm

### Created SNS Topic

This is required before proceeding to create an alarm.

This was done using the AWS Documentation [aws sns create-topic](https://docs.aws.amazon.com/cli/latest/reference/sns/create-topic.html)

The command below was run to return the TopicARN.

```sh
aws sns create-topic --name billing-alarm
```
![User Graphic](https://github.com/Damiloju123/aws-bootcamp-cruddur-2023/blob/3a2a0fad875a758d5e3b0c7b4a175b6b3ed0bb6c/_docs/assets/Topics.JPG)

Created a Subscription with the TopicARN Output & Email Address

```sh
aws sns subscribe \
    --topic-arn TopicARN \
    --protocol email \
    --notification-endpoint your@email.com
```

Received email and confirmed the subscription

![User Graphic](https://github.com/Damiloju123/aws-bootcamp-cruddur-2023/blob/3a2a0fad875a758d5e3b0c7b4a175b6b3ed0bb6c/_docs/assets/SNS.JPG)

### Created Alarm

This was done using the AWS Documentation [aws cloudwatch put-metric-alarm](https://docs.aws.amazon.com/cli/latest/reference/cloudwatch/put-metric-alarm.html)
For creation via CLI, [Create an Alarm via AWS CLI](https://aws.amazon.com/premiumsupport/knowledge-center/cloudwatch-estimatedcharges-alarm/)

```sh
aws cloudwatch put-metric-alarm --cli-input-json file://aws/json/alarm_config.json
```

![User Graphic](https://github.com/Damiloju123/aws-bootcamp-cruddur-2023/blob/3a2a0fad875a758d5e3b0c7b4a175b6b3ed0bb6c/_docs/assets/Alarm.JPG)


### Created Conceptual Diagram in Lucid Charts

![image](https://github.com/Damiloju123/aws-bootcamp-cruddur-2023/blob/6056a8a3e71953a9ed5c524c66c3178c862fff54/_docs/assets/Napkin.JPG)

- Created [Conceptual Diagram](https://lucid.app/lucidchart/invitations/accept/inv_b8735dcc-9946-4f64-84e2-72d524e319d6)

### Created Logical Architectual Diagram in Lucid Charts
