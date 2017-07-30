# Docker Bootstrap

This repository demonstrates a basic docker image and shows the pipeline for 
developing docker images within GitLab.
Once the image has been developed, the master branch is mirrored on Github 
and that latest tagged image is deployed to DockerHub.

## Pipeline

> Development and Continuous Integration on GitLab

![gitlab_logo](https://raw.githubusercontent.com/TheYorkshireDev/docker-bootstrap/master/resources/gitlab.png)

> Publish to GitHub

![github_logo](https://raw.githubusercontent.com/TheYorkshireDev/docker-bootstrap/master/resources/github.png)

> Release to DockerHub

![dockerhub_logo](https://raw.githubusercontent.com/TheYorkshireDev/docker-bootstrap/master/resources/dockerhub.png)

## Build & Release Status

### Build

[![Build Status](https://gitlab.com/TheYorkshireDev/docker-bootstrap/badges/master/build.svg)](https://gitlab.com/TheYorkshireDev/docker-bootstrap/pipelines)
[![GitHub tag](https://img.shields.io/github/tag/theyorkshiredev/docker-bootstrap.svg)](https://github.com/theyorkshiredev/docker-bootstrap/releases)
[![license](https://img.shields.io/github/license/theyorkshiredev/docker-bootstrap.svg)](https://github.com/theyorkshiredev/docker-bootstrap/blob/master/LICENCE)

### Release

[![Docker Build Status](https://img.shields.io/docker/build/theyorkshiredev/docker-bootstrap.svg)](https://hub.docker.com/r/theyorkshiredev/docker-bootstrap/)
[![Docker Automated build](https://img.shields.io/docker/automated/theyorkshiredev/docker-bootstrap.svg)](https://hub.docker.com/r/theyorkshiredev/docker-bootstrap/)
[![Docker Pulls](https://img.shields.io/docker/pulls/theyorkshiredev/docker-bootstrap.svg)](https://hub.docker.com/r/theyorkshiredev/docker-bootstrap/)
[![Docker Stars](https://img.shields.io/docker/stars/theyorkshiredev/docker-bootstrap.svg)](https://hub.docker.com/r/theyorkshiredev/docker-bootstrap/)

## GitLab Development Environment

### GitLab General Settings

* Merge Requests: *Fast-forward merge*
* Only allow merge requests to be merged if the pipeline succeeds

### GitLab Repository Settings

#### Push Rule

Set the following rules:

* Do not allow users to remove git tags with git push
* Prevent committing secrets to Git

## GitHub Deployment

### Github Setup

* Create a GitHub repository mirroring the same name as the GitLab repository.
* Create a personal token on GitHub with the permission `Access public repositories` allowing the user to push to the repository.
* Add the personal token as an environment variable for the pipeline called `GITHUB_TOKEN`

### Github Repository

Within the repository settings:

* Uncheck the `Wikis` feature
* Uncheck the `Restrict editing to collaborators only` feature
* Uncheck the `Issues` feature
* Uncheck the `Projects` feature

## DockerHub Release

* Create an automated-build within docker hub
* Link the DockerHub repository and the github repository
* Add build step: `TAG`, `/^[0-9.]+$/`, `/`, `latest`
* Add build step: `TAG`, `/^[0-9.]+$/`, `/`
* Uncheck automatic build on push
* Activate triggers
* Store the trigger token in an environment variable `$DOCKERHUB_TOKEN`

## Contribute

* [Report Issues on Gitlab](https://gitlab.com/TheYorkshireDev/docker-bootstrap/issues)
