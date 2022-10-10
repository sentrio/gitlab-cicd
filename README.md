# gitlab-cicd
Gitlab CICD integration

CICD Deployment Frequency Integration requires the following variables:

* SENTRIO_CLIENT_ID: SENTRIO client id
* SENTRIO_CLIENT_SECRET: SENTRIO client secret
* PROJECT_ID: The Jira project id associated to this applications
* APPLICATION_NAME: the application name (generally the artifactId)
* APPLICATION_VERSION: the application version
* ENVIRONMENT: name of the deployment environment

In order to notify application deployments to the SENTRIO VSM platform:

1. Include the remote sentrio deploy script:

```
include:
  - remote: 'https://raw.githubusercontent.com/sentrio/gitlab-cicd/main/gitlab-ci-deploy.yml'
```

2. add a sentrio_deployment_ENV call to your pipeline referencing the `.sentrio_deployment` job, e.g.:
 
```
sentrio_deploy_dev:
  stage: deploy
  extends: .sentrio_deployment
  variables:
    PROJECT_ID: XX
    APPLICATION_NAME: "gitlab-app"
    APPLICATION_VERSION: 1.0.0-SNAPSHOT
    ENVIRONMENT: "dev"  
```
