
# Laravel Development Docker Image

## Overview

This Docker image provides a PHP 8.0 FPM environment tailored for Laravel development. It includes Composer and the required PHP extensions to run a Laravel application.

## Prerequisites

- Docker installed on your system

## Build the Docker Image

To build the image locally, navigate to the directory containing the `Dockerfile` and run:

\```bash
docker build -t your-image-name .
\```

## Push to Docker Hub

After building, you can push the image to your Docker Hub repository:

\```bash
docker login
docker tag your-local-image-name:latest khalilkasmi/nt3awno:latest
docker push khalilkasmi/nt3awno:latest
\```

## Pull and Run the Image

Team members can pull the image and run it using:

\```bash
docker pull khalilkasmi/nt3awno:latest
docker run -p 9000:9000 khalilkasmi/nt3awno:latest
\```

## Usage in a Laravel Project

For a Laravel project, this image can be used as a base in your project-specific `Dockerfile`. Add your customizations after specifying this image as the base image.

\```Dockerfile
FROM khalilkasmi/nt3awno:latest

# Your customizations here
\```
