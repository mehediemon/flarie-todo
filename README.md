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

## Kubernetes Commands

- To deploy the application:
  ```bash
  kubectl apply -f deployment.yaml
  kubectl apply -f service.yaml
  ```

- To check the status:
  ```bash
  kubectl get pods
  kubectl get services
  ```

- Access the application at `http://<node-ip>:34567`.

## Links

- **Forked GitHub Repository**: [YOUR_REPOSITORY_LINK]
- **Docker Image**: [Docker Hub link]

## Additional Information

This project was created as part of a task to dockerize and deploy a Node.js application to Kubernetes. The CI/CD pipeline automatically builds the Docker image and pushes it to Docker Hub.
```

### 6. **Final Steps**

1. **Set Up DockerHub Secrets**: For the CI pipeline to push to DockerHub, you must store your DockerHub username and password as secrets in GitHub. Go to your repository settings → Secrets → New repository secret.
   - `DOCKER_USERNAME` = Your Docker Hub username
   - `DOCKER_PASSWORD` = Your Docker Hub password

2. **Push the Changes**: Commit and push all your changes to your forked repository:
   ```bash
   git add .
   git commit -m "Add Dockerfile, CI pipeline, and Kubernetes manifests"
   git push origin main
   ```

3. **Verify**: After pushing the changes, verify that the Docker image is built and pushed to Docker Hub, and the CI pipeline ran successfully.

4. **Deploy to Kubernetes**: You can deploy your Kubernetes manifests using the following commands:
   ```bash
   kubectl apply -f deployment.yaml
   kubectl apply -f service.yaml
   ```

5. **Access the Application**: The app should be accessible via `http://<node-ip>:34567` on your Kubernetes cluster.

### Conclusion

By completing these steps, you'll have:
- A Dockerized Node.js application.
- A working CI pipeline using GitHub Actions to automatically build and push the Docker image.
- Kubernetes manifests to deploy the app as a NodePort service.
- A clear `README.md` file with all the necessary details.

Let me know if you need any further assistance!
