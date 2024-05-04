# Minikube
Using minikube in GitHub Actions for testing my app
# Flask Web Application Deployment to Minikube with Docker and GitHub Actions

The setup provided here is geared towards deploying a simple Flask web application to a Minikube cluster using Docker and GitHub Actions. Let's break down what each component does:

## Dockerfile

This file contains instructions for building a Docker image for the Flask web application. It specifies the base image (Python 3.8), sets the working directory, installs the required Python dependencies listed in `requirements.txt`, and copies the application code into the image. Finally, it specifies the command to run the Flask application (`python main.py`) when a container is started from this image.

## GitHub Actions Workflows

### PR Workflow (.github/workflows/pr.yml)

This GitHub Actions workflow is triggered on each pull request (PR). It's responsible for building the Docker image for the Flask application, tagging it with the PR number, and pushing it to the Docker Hub registry. This workflow enables continuous integration (CI) by automatically building and testing the application whenever a new PR is opened.

### Deployment to Minikube Workflow (.github/workflows/deploy-to-minikube.yaml)

Similar to the PR workflow, this GitHub Actions workflow is responsible for deploying the Flask application to Minikube. It's triggered on each push to the main branch. It sets up Minikube, builds the Docker image for the Flask application, applies Kubernetes manifests (`deployment.yaml` and `service.yaml`) to deploy the application to the Minikube cluster.

## HTML Template (app/templates/index.html)

This HTML template file defines the structure and layout of the web page that users interact with. It contains a form where users can input a number, and a message area to display whether the number is prime or not.

## Flask Application (app/main.py)

This Python file contains the Flask application logic. It defines a route `/` that renders the `index.html` template. It also contains a function `is_prime()` to check whether a given number is prime or not.

## Requirements (requirements.txt)

This file lists the Python dependencies required by the Flask application. In this case, it only includes `Flask==2.0.1`, which is the version of Flask used by the application.

Overall, this setup enables automated building, testing, and deployment of the Flask web application to a Minikube cluster using Docker and GitHub Actions. It streamlines the development process and ensures consistency and reliability in deploying the application.

