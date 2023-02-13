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

![User Graphic](_docs/week0/Users.JPG)


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

![User Graphic](_docs/week0/STS.JPG)

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

![User Graphic](_docs/week0/Budget.JPG)