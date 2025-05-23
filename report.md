# Dockerized Flask App

## Steps
This Flask app was containerized using Docker with a minimal Python image. The Dockerfile installs dependencies, sets environment variables, runs the app on port 8080, and uses a non-root user.

## Volumes
Volumes or bind mounts can be added using `-v` flag to support persistent storage.

## Challenges
Initially, the app was not accessible—solved by binding to `0.0.0.0`. Non-root permission issues were fixed by creating a user.

Title: Dockerized Flask App – Report

This assignment involved containerizing a Python Flask application using Docker, while adhering to Dockerfile best practices. The application (`app.py`) returns a simple message and runs on port 8080.

To begin, I created the application and defined its dependencies in `requirements.txt`. I then developed a Dockerfile using the official `python:3.10-slim` base image, avoiding the `latest` tag to ensure version stability. I used environment variables (`PYTHONDONTWRITEBYTECODE`, `PYTHONUNBUFFERED`) to optimize runtime behavior and reduce unnecessary caching. 

I structured the Dockerfile to reduce the number of layers by copying `requirements.txt` and installing dependencies first, followed by copying source files. For security, I added a non-root user using `useradd -m myuser` and set it as the active user with `USER`. I exposed port 8080 and used `CMD` to run the application using Python.

The image was built using `docker build -t flask-docker-app:v1 .`. A screenshot was captured during this step. To run the application, I used the command `docker run -d -p 8080:8080 -v ${PWD}:/app flask-docker-app:v1`, which mapped the local directory as a bind mount for persistence and enabled port forwarding.

A key challenge was that port 8080 was already in use. I resolved this by using an alternate port (`8081`) on the host. Additionally, I encountered a Git push error due to an existing remote history, which I fixed using `git pull --allow-unrelated-histories` and resolving the merge.

Both build and run screenshots have been included. All project files are stored in the GitHub repository.

GitHub Repository: https://github.com/KeerthanaGarimella/dockercontainer
