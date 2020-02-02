## Create assume roles in sub-accounts

Upload `base-pipeline.yaml` in all the sub-accounts under your organization.

Pre-req before uploading the `base-pipeline.yaml` CloudFormation template:

- Add Account IDs in `iam-roles.yaml` under IAM role ARN
- Create a repo on Github or any other version platform, have the application token aka. GithubOauthToken ready.

Note: `base-pipeline.yaml` will retain S3 buckets created to store pipeline versions.