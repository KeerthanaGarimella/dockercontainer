# Dockerized Flask App

## Steps
This Flask app was containerized using Docker with a minimal Python image. The Dockerfile installs dependencies, sets environment variables, runs the app on port 8080, and uses a non-root user.

## Volumes
Volumes or bind mounts can be added using `-v` flag to support persistent storage.

## Challenges
Initially, the app was not accessible—solved by binding to `0.0.0.0`. Non-root permission issues were fixed by creating a user.
