# Overview

Laravel docker environment sample.

# Requirement

* Docker version 20.10.11, build dea9396
* PHP 7.4.29
* Composer version 1.10.26
* mysql  Ver 15.1 Distrib 10.5.15-MariaDB
* phpMyAdmin 5.2.0

# Usage

1. Clone the laravel repository from github.
```bash
# command
git clone https://github.com/shogohayakawa/docker.git
```
2. Set database information in ```db-variables.env```.
```bash
# path
/docker/laravel/docker/db/db-variables.env
```
3. Copy the source code of your laravel project to the ```src``` directory.
```bash
# path
/docker/laravel/src/
```
4. Build docker.
```bash
# command
cd ~/docker/laravel # Directory where the repository is cloned
docker-compose build
```