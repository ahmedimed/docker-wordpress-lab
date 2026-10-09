# Docker WordPress Infrastructure Lab

## Overview

A containerized WordPress application connected to a MySQL database using Docker Compose. This project demonstrates container management, networking, persistent storage, and environment-based configuration.

## Architecture

* **WordPress:** Web application exposed on port `8080`.
* **MySQL 8:** Database service accessible internally to WordPress.
* **Docker Compose:** Manages both services.
* **Docker network:** Enables communication between containers.
* **Named volumes:** Persist database and WordPress data.
* **Environment variables:** Keep configuration separate from the Compose file.

## Prerequisites

* Docker Desktop or Docker Engine
* Docker Compose

## Deployment

1. Clone this repository.

2. Create a local `.env` file containing:

   ```dotenv
   MYSQL_ROOT_PASSWORD=change_me
   MYSQL_DATABASE=wordpress
   MYSQL_USER=wpuser
   MYSQL_PASSWORD=change_me_too
   ```

3. Start the services:

   ```bash
   docker compose up -d
   ```

4. Check container status:

   ```bash
   docker compose ps
   ```

5. Open `http://localhost:8080` in your browser.

## Useful Commands

```bash
docker compose logs
docker compose logs mysql
docker compose logs wordpress
docker compose down
docker compose up -d
docker volume ls
docker compose config --quiet
```

## Persistence Test

Created a test post in WordPress, stopped and removed the containers using `docker compose down`, then recreated them with `docker compose up -d`. Verified that the post remained available because the named volumes persisted.

## Security Notes

* The `.env` file is excluded from Git using `.gitignore`.
* Do not commit real passwords or production secrets.
* The credentials used in this lab are for local practice only.

## Skills Demonstrated

Docker, Docker Compose, Linux-style service troubleshooting, container networking, MySQL, persistent volumes, environment variables, Git, and GitHub.
