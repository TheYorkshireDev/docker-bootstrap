# Docker Bootstrap

This repository demonstrates a basic docker image and shows the pipeline for 
developing docker images within GitLab.
Once the image has been developed, the master branch is mirrored on Github 
and that latest tagged image is deployed to DockerHub.

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
