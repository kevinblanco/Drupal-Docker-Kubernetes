# Docker and Kubernetes Modern Stack for Drupal

## Introduction

This repository holds the example of a modern stack configuration to run, execure and deploy Drupal with Docker and Kubernetes. This was created for the Docker Costa Rica comunity but is based on a production working project. 

## Stack

The Stack consist of the following containers:

| Container       | Versions               | Service name    | Default |
| --------------  | ---------------------- | --------------- | ------- |
| Nginx           | 1.17, 1.16             | `nginx`         | ✓       |
| Apache          | 2.4                    | `apache`        |         |
| Drupal          | 8, 7                   | `php`           | ✓       |
| PHP             | 7.4, 7.3, 7.2          | `php`           |         |
| MariaDB         | 10.4, 10.3, 10.2, 10.1 | `mariadb`       | ✓       |
| PostgreSQL      | 12, 11, 10, 9.x        | `postgres`      |         |
| Redis           | 5, 4                   | `redis`         |         |
| Memcached       | 1                      | `memcached`     |         |
| Varnish         | 6.0, 4.1               | `varnish`       |         |
| Node.js         | 12, 10, 8              | `node`          |         |
| Drupal node     | 1.0                    | `drupal-node`   |         |
| Solr            | 8, 7, 6, 5             | `solr`          |         |
| Elasticsearch   | 7, 6                   | `elasticsearch` |         |
| Kibana          | 7, 6                   | `kibana`        |         |
| OpenSMTPD       | 6.0                    | `opensmtpd`     |         |
| Mailhog         | latest                 | `mailhog`       | ✓       |
| AthenaPDF       | 2.10.0                 | `athenapdf`     |         |
| Rsyslog         | latest                 | `rsyslog`       |         |
| Blackfire       | latest                 | `blackfire`     |         |
| Webgrind        | 1                      | `webgrind`      |         |
| Xhprof viewer   | latest                 | `xhprof`        |         |
| Adminer         | 4.6                    | `adminer`       |         |
| phpMyAdmin      | latest                 | `pma`           |         |
| Selenium chrome | 3.141                  | `chrome`        |         |
| Portainer       | latest                 | `portainer`     | ✓       |
| Traefik         | latest                 | `traefik`       | ✓       |

## Documentation

- Clone this repository and switch to the docker folder (Optional: for Drupal 7 or 6 comment out corresponding DRUPAL_TAG and NGINX_TAG in .env file)
- Configure domains locally, Add `127.0.0.1 drupal.docker.localhost` to your host file.
- From project root directory run `docker-compose up -d` or `make up` to start containers. Give it 10-20 seconds to initialize after the start.
That's it! Proceed with Drupal installation at http://drupal.docker.localhost:8000. Default database user, password and database name are all `drupal`, database host is `mariadb`
You can see status of your containers and their logs via portainer: http://portainer.drupal.docker.localhost:8000

## Kubernetes

- Clone this repository and switch the kubernetes folder.
- Run `kubectl apply -f persistentvolumeclaim.yaml` to configure the Persistent Volume Claims needed.
- Run `kubectl apply -f drupal-mysql.yaml` to configure the Database containers needed.
- Run `kubectl apply -f drupal.yaml` to configure all the Drupal Deployments and Services needed. 



