# JHipster Deployment Options

This repo demonstrates various CI/CD options using JHipster generated source code. This repo is designed to be split into two repositories, but is contained in this single repository for readability. The two repositories are:
- gateway: Standard JHipster generated Gateway component.
- rancher: Standalone repository, with a `jhipster rancher-compose` option used to generate.

See the `generated_code` branch for a copy of the unaltered generated source code.

## Jenkins + CI/
Standard configuration, with only the `Jenkinsfile` modified to use the [Credentials Binding Plugin](https://wiki.jenkins-ci.org/display/JENKINS/Credentials+Binding+Plugin).

## Gitlab + Rancher
A number of changes where made to the `.gitlab-ci.yml` to allow the Docker Image to be generated on a Docker-build runner, using a custom build image which contained Docker (for Docker-in-Docker). Also a new stage was introduced to call the pipeline defined in the rancher repository.

The rancher repository, although based off a standard `jhipster rancher-compose` run, contains a new `.gitlab-ci.yml` file which builds and pushes the associated configuration image, and then deploys the entire stack to rancher.
