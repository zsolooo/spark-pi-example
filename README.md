# Spark Pi Example

Spark Pi is a sample project to trigger a short lived Spark CI/CD workflow on Banzai Cloud's [Pipeline](https://github.com/banzaicloud/pipeline) PaaS platform.

## Prerequisites

* Account on one of the following cloud providers: Amazon, Azure, GoogleCloud
* A Banzai Cloud Control Plane needs to be running and accessible
* Oauth2 authentication enabled on the control plane

## Setup

* fork the project into your repository
* make a copy of the flow descriptor template corresponding to your chosen cloud provider:
```
cp .pipeline.yml.[azure|aws|gke].template .pipeline.yml
```
* check the flow descriptor file and replace the placeholders with your specific values (cluster name, bucket / folder names etc ...)

> In short: the CI/CD flow descriptor file contains the steps needed from provisioning the environment, building the code, running tests to being deployed and executed along with project specific variables (eg.:credentials, program arguments, etc ...).

* navigate to the CI/CD user interface (that usually runs on the Banzai Cloud Control plane instance)
* enable the project build from the list of available repositories
* add the following secrets to the build:

```
PLUGIN_ENDPOINT = [control-plane]/pipeline/api/v1
PLUGIN_TOKEN = "oauthToken"
```

The project is configured now for the Banzai Cloud CI/CD flow. On each commit to the repository a new flow will be triggered. You can check the progress on the CI/CD user interface.
