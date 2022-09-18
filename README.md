# gitlab-cicd
Gitlab CICD integration

CICD Integration requires de following variables:

* CLIENT_ID: SENTRIO client id
* CLIENT_SECRET: SENTRIO client secret
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

2. Integrate the .sentrioDeployment call into your existing deployment stages

```
deploy_dev:
  stage: deploy
  script:
    - echo "Deploying to dev"
    - echo "Deployed to dev"
    - !reference [.sentrioDeployment, script]
  variables:
    PROJECT_ID: XX
    APPLICATION_NAME: "gitlab-app"
    APPLICATION_VERSION: 1.0.0-SNAPSHOT
    ENVIRONMENT: "dev"
```
