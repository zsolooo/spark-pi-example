# Spark Pi Example

Spark Pi is a sample project to trigger a short lived Spark CI/CD workflow on Banzai Cloud's [Pipeline](https://github.com/banzaicloud/pipeline) PaaS platform.

## Prerequisites

* A Banzai Cloud Control Plane needs to be running and accessible

## Configuration required to hook in into the [Banzai Pipeline](https://github.com/banzaicloud/pipeline) CI/CD workflow

In order for a project to be part of the Banzai Pipeline CI/CD workflow it **must contain** a specific configuration file: ```.pipeline.yml``` in its root folder.

> In short: the configuration file contains the steps the project needs to go through the workflow from provisioning the environment, building the code, running tests to being deployed and executed along with project specific variables (eg.:credentials, program arguments, etc needed to assemble the execution command - `spark-submit` in this case).

The configuration file for this project is [.pipeline.yml](.pipeline.yml)

## Set these secrets on the CI user interface

### URL endpoint for the Pipeline API

    plugin_endpoint: http://<host/ip>/pipeline/api/v1

The pipeline runs on the Banzai Cloud Control Plane, so this value should point to the hostname/ip of the machine hosting it.

### Credentials for the Pipeline API

    plugin_user: <admin>
    plugin_password: <example>

These credentials specify the user of the Pipeline API.
