# Wordpress Server

This repository contains the configuration of Wordpress in a docker container. You can run it on your local machine or on your server. The Wordpress server is configured to run with the latest version of Wordpress and MariaDB and can be easily customized to your needs.

You can find further information on the following websites:<br>
https://de.wordpress.org<br>
https://github.com/docker/awesome-compose/tree/master/official-documentation-samples/wordpress/<br>

<br>

## Table of contents

1. [Prerequisites](#prerequisites)
2. [Quickstart](#quickstart)
3. [Usage](#usage)
4. [Checklist](project-checklist.pdf)

<br>

## Prerequisites

-   Server with Docker and Docker Compose installed
-   Alternatively, you can run it on your local machine
-   Git installed to clone the repository

<br>

## Quickstart

This section describes how to run the Wordpress server with Docker Compose on port `8080`. Only Docker Compose and Git are required to run the server.

1. Clone the repository:

```shell
git clone git@github.com:mikemeyer186/wordpress-server.git
```

2. Change to directory `/wordpress-server`:

```shell
cd wordpress-server
```

3. Create a `.env` file with the following content or copy the `example.env` file to `.env` and replace the values:

```shell
# WordPress
WORDPRESS_DB_NAME=<your_database_name>
WORDPRESS_DB_USER=<your_database_user>
WORDPRESS_DB_PASSWORD=<your_database_password>

# MariaDB
MYSQL_ROOT_PASSWORD=<your_root_password>
MYSQL_DATABASE=<your_database_name>
MYSQL_USER=<your_database_user>
MYSQL_PASSWORD=<your_database_password>
```

> [!NOTE]
> The database name, user and password can be anything you want. Just make sure to use the same values for both Wordpress and MariaDB.

4. Run the Docker Compose file:

```shell
docker compose up -d
```

5. Install Wordpress:

-   Open your browser and go to `http://<your_host>:8080`
-   Select your language and click on "Continue"
-   Enter your site title, username, password and email address
-   Click on "Install WordPress"
-   Log in to Wordpress and start your blog

5. Stop the server:

```shell
# Stop the server, but keep the data saved
docker compose down

# or stop the server and remove all data
docker compose down -v
```

<br>

## Usage

The Wordpress server is configured to run with some basic settings. You can configure these settings in the `docker-compose.yaml` file.

### Configuration

There are two services in the `docker-compose.yaml` file: `wordpress` and `db`. The `wordpress` service is for the Wordpress container and the `db` service is for the MariaDB container. You can configure the following settings:

#### Wordpress Service

-   `image`: The image that is used for the service. The default image is `wordpress:latest`.
-   `ports`: The ports that are exposed to the host. The default port is `8080`.
-   `volumes`: The volumes that are mounted to the host. The default volume is `wp_data`.
-   `networks`: The network that is used by both services containers. The default network is `wp_network`.
-   `restart`: The restart policy for the container. The default policy is `unless-stopped`.

#### MariaDB Service

-   `image`: The image that is used for the service. The default image is `mariadb:latest`.
-   `ports`: The ports that are exposed to the host. The default port is `3306`.
-   `volumes`: The volumes that are mounted to the host. The default volume is `db_data`.
-   `networks`: The network that is used by both services containers. The default network is `wp_network`.
-   `restart`: The restart policy for the container. The default policy is `unless-stopped`.
