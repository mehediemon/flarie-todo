# Flaire Todo - Dockerized Node.js Application

## Overview

This repository contains a Node.js Todo application, which has been Dockerized and is ready to be deployed to a Kubernetes cluster.

## Steps to Deploy

1. **Forked Repository**: You can find the repository [here](https://github.com/YOUR_USERNAME/flarie-todo).
2. **Docker Image**: The Docker image for the application is publicly available on Docker Hub [here](https://hub.docker.com/repository/docker/YOUR_DOCKER_USERNAME/flarie-todo).
3. **CI Pipeline**: The CI pipeline automatically builds and pushes the Docker image on each push/merge to the `main` branch. It is set up using GitHub Actions.
4. **Kubernetes Deployment**:
   - You can deploy the application using the Kubernetes manifests `deployment.yaml` and `service.yaml`.
   - The application is exposed via a `NodePort` on port `34567` on the cluster.
