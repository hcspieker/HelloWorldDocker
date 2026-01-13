# HelloWorldDocker

This is a simple Docker project that uses dockerfile and docker-compose to set up a ASP.NET Core web application. The project includes both development and production configurations.

There are two dockerfiles included in this project:
1. [`Dockerfile.dev`](HelloWorldDocker/Dockerfile.dev): This docker image resolves dependencies andd starts the application using the `dotnet watch` command for development purposes.
1. [`Dockerfile`](HelloWorldDocker/Dockerfile): Includes a multi-stage build to create a smaller production image.

And two docker-compose files:
1. [`docker-compose.dev.yml`](HelloWorldDocker/docker-compose.dev.yml): Uses the `Dockerfile.dev` to set up a development container for the web application behind a traefik reverse proxy.
1. [`docker-compose.yml`](HelloWorldDocker/docker-compose.yml): Uses the `Dockerfile` to set up a production container for the web application behind a traefik reverse proxy.
