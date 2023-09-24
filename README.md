
# Laravel Development Docker Image

## Overview

This Docker image provides a PHP 8.0 FPM environment tailored for Laravel development. It includes Composer and the required PHP extensions to run a Laravel application.

## Prerequisites

- Docker installed on your system
- Docker Compose installed on your system

## Build the Docker Image

To build the image locally, navigate to the directory containing the `Dockerfile` and run:

\```bash
docker build -t nt3awno .
\```

## Docker Compose and Nginx Setup

We use Docker Compose to orchestrate the PHP-FPM container along with an Nginx web server. The `docker-compose.yml` and `nginx.conf` files are provided for this setup.

1. Place the `docker-compose.yml` and `nginx.conf` files in the same directory as your Dockerfile.
2. Run the following command to start both containers:

\```bash
docker-compose up
\```

This will start the PHP-FPM server and Nginx web server. You can access your Laravel application at `http://localhost:8080`.

### Adding a Test Laravel App

#### Option 1: Use an Existing Laravel Project

1. Copy your existing Laravel project into a folder named `laravel-app` in the same directory as your `docker-compose.yml` and `nginx.conf` files.
2. Run Docker Compose:

\```bash
docker-compose up
\```

#### Option 2: Create a New Laravel Project Inside the Container

1. Start the containers:

\```bash
docker-compose up
\```

2. Exec into the PHP-FPM container:

\```bash
docker exec -it laravel_app bash
\```

3. Inside the container, install Laravel:

\```bash
composer create-project --prefer-dist laravel/laravel .
\```

## Push to Docker Hub

After building, you can push the image to your Docker Hub repository:

\```bash
docker login
docker tag nt3awno:tag khalilkasmi/nt3awno:tag
docker push khalilkasmi/nt3awno:tag
\```

## Pull and Run the Image

Team members can pull the image and run it using:

\```bash
docker pull khalilkasmi/nt3awno:tag
docker run -p 9000:9000 khalilkasmi/nt3awno:tag
\```

## Usage in a Laravel Project

For a Laravel project, this image can be used as a base in your project-specific `Dockerfile`. Add your customizations after specifying this image as the base image.

\```Dockerfile
FROM khalilkasmi/nt3awno:tag

# Your customizations here
\```
