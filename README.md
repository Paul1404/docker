# Grav CMS with Nginx and PHP 8.0 FPM using Docker Compose

This repository contains a Docker Compose configuration file for running the [Grav CMS](https://getgrav.org/) with Nginx and PHP 8.0 FPM.

## Requirements

- [Docker Engine](https://docs.docker.com/engine/) installed
- [Docker Compose](https://docs.docker.com/compose/) installed

## Usage

1. Clone this repository:

   ```sh
   git clone https://github.com/your_username/grav-nginx-php8.git

2. Change into the cloned directory:
cd grav-nginx-php8

3. Edit the db service environment variables in the docker-compose.yml file to set your desired MySQL/MariaDB root password and username:
db:

  ```sh
  image: mariadb:latest
  container_name: grav-mariadb
  restart: always
  volumes:
    - ./db:/var/lib/mysql
  environment:
    - MYSQL_ROOT_PASSWORD=your_password
    - MYSQL_DATABASE=grav
    - MYSQL_USER=grav
    - MYSQL_PASSWORD=your_password
  healthcheck:
    test: ["CMD", "mysqladmin", "ping", "-h", "localhost"]
    interval: 30s
    timeout: 10s
    retries: 5

   '''

4. Run the docker-compose up command to start the containers:
docker-compose up -d

5. Access the Grav CMS at http://localhost.

## Configuration

    The web service is an Nginx web server that listens on port 80 and serves static content from the html directory.
    The app service runs PHP 8.0 FPM and serves the Grav CMS application. The PHP configuration can be edited in the php.ini file.
    The db service runs a MySQL/MariaDB database server and stores data in the db directory.
    
## License

This project is licensed under the MIT License.
