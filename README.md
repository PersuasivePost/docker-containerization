# Docker Containerization Demo

This project demonstrates how to containerize and serve a simple static web
application using **Docker** and **NGINX**. The webpage runs inside an
Alpine-based NGINX container and is exposed on port `80`.

## Project information

- **Subject:** Advanced Cloud Computing
- **Topic:** Containerization and Cloud Application Deployment
- **Type:** Continuous Assessment (CA) project

### Team members

| Name | Roll number |
| --- | --- |
| Ashvatth Joshi | 16010123085 |
| Atharv Mulye | 16010123087 |
| Gandharva Ugale | 16010123119 |

## Project structure

```text
.
├── Dockerfile
├── README.md
└── index.html
```

- `Dockerfile` defines the NGINX-based Docker image.
- `index.html` contains the static webpage served by NGINX.

## Prerequisites

Install Docker Desktop or Docker Engine before running the project. Verify
that Docker is available with:

```bash
docker --version
```

## Build the Docker image

From the project directory, run:

```bash
docker build -t docker-containerization-demo .
```

## Run the container

Start the container and map port `8080` on the host to port `80` in the
container:

```bash
docker run --name docker-containerization-demo -p 8080:80 docker-containerization-demo
```

Open [http://localhost:8080](http://localhost:8080) in a web browser. The
page should confirm that the application is running from an NGINX Docker
container.

## Run in detached mode

To run the container in the background:

```bash
docker run -d --name docker-containerization-demo -p 8080:80 docker-containerization-demo
```

Check the running container:

```bash
docker ps
```

View the application logs:

```bash
docker logs docker-containerization-demo
```

## Stop and remove the container

When the container is no longer needed, stop and remove it with:

```bash
docker stop docker-containerization-demo
docker rm docker-containerization-demo
```

## How it works

The `Dockerfile` uses the lightweight `nginx:alpine` image as its base. The
project's `index.html` file is copied into NGINX's default web root:

```text
/usr/share/nginx/html/index.html
```

The container exposes port `80`, while the `-p 8080:80` option makes the
application available at port `8080` on the host machine.
