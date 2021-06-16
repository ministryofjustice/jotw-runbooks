---
category: Runbooks
expires: 2022-01-31
---

# DockerHub upload, download images locally and in AWS

## Required

* AWS access
* LastPass access
* Docker CLI

We use a team DockerHub account to pull and push Docker images when we build our sites in AWS. This prevents us from hitting the 100 image pull Docker limit. Our team DockerHub account details are located in LastPass under Justice On The Web. If you require further access to managing this account get in touch with [Operational Engineering](https://ministryofjustice.github.io/operations-engineering/documentation/services/dockerhub.html#moj-dockerhub-account).

## Using DockerHub via your local CLI

1. Go to the team DockerHub account via the website and go to the [security section](https://hub.docker.com/settings/security) and generate a token.
2. In your terminal run the following `docker login --username "<user name here>" --password "<password here>"` replacing the username variable with the MoJ team account username and the password with you newly created token. 
3. Once logged in, you should be able to push and pull images freely using the team account.

## Using DockerHub within our AWS configuration

In the AWS environment we still use the docker CLI `docker login --username "$DOCKERUSERNAME" --password "$DOCKERPASSWORD"` to login and pull/push images (see the buildspec.yml file located in each website's repo root) however, our DockerHub credentials are managed via AWS Secrets Manager. Secrets Manager is then provided access to our various AWS resources using the correct IAM policies. These policies and configurations have been added to our [CloudFormation templates](https://github.com/ministryofjustice/wp-cloudformation-templates).





