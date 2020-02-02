# Manage IAM Access for a Multi-Account Architecture


There are two repositories to manage IAM access.
    1. To manage IAM users, groups and roles in Jump Account aka Identity Account in AWS terms
    2. A common repo which will be used to manage cross-accounts IAM roles in each sub-account

I would suggest to create separate repos for the same to avoid unneccesary triggers after every merge to a branch on CodePipeline

#### Step 1: Setup Jump-account pipeline

- Upload `jump-account/pipeline.yaml` as a CloudFormation template in your Jump/Identity Account. This will setup all the IAM groups, roles and users.
- Follow the steps mentioned in `jump-account/readme.md` before uploading the CloudFormation template.

#### Step 2: Setup Cross-Account pipeline in all the Sub-Accounts

- Upload `sub-accounts/base-pipeline.yaml` in each of the sub-accounts under your organization. This `sub-account` repo will act a central place to manage IAM access originated from the Jump Account.
- Follow the steps mentioned in `sub-account/readme.md` before uploading the CloudFormation template.

#### Step 3: Use Assume link to login to Sub-Accounts

Generate assume links and share them.

Format to create assume link : https://signin.aws.amazon.com/switchrole?region={region}&account={account_id}&roleName={role_name}&displayName={display_name}

Note: It is suggested you enable 2FA for all the IAM users as best practice. For more refer [AWS Security Best Practices White Paper](https://d0.awsstatic.com/whitepapers/Security/AWS_Security_Best_Practices.pdf)