### User Management App  ![alt text](https://scontent-waw1-1.xx.fbcdn.net/v/t1.15752-9/70408001_2223391487786755_1184256589566050304_n.png?_nc_cat=102&_nc_oc=AQn0_Ofng0dGzQY22Pby2Gpcc-T4ehS_yZdg4q_yHQQ0bSFEfxMWwiilxebafhxEWRQ&_nc_ht=scontent-waw1-1.xx&oh=a1a1a25cfdd027d59a8b45166bd80d32&oe=5E06B765) [![Build Status](https://travis-ci.org/Gintasp/user-management.svg?branch=development)](https://travis-ci.org/Gintasp/user-management)

This repository contains REST API-driven user management Symfony app.

##### Instructions

To launch the app simply issue `bash scripts/start.sh` command. To stop - `docker-compose down`.

Or follow the process manually:
1. Build and start docker containers `docker-compose -d --build`.
2. Install dependencies with `docker exec user-management-php-fpm composer install && yarn && yarn encore dev`.
3. Setup database:
    * `docker exec user-management-php-fpm bin/console d:d:c` 
    * `docker exec user-management-php-fpm bin/console d:m:m -n` 
    * `docker exec user-management-php-fpm bin/console d:f:l -n`
4. Log into admin dashboard with following credentials:
    * username: `admin`
    * password: `password`

##### Running tests
Run tests with `vendor/bin/simple-phpunit`.

##### REST API
Endpoints: 
* `/rest/v1/teams` - create new team (POST)
* `/rest/v1/teams` - fetch all teams (GET)
* `/rest/v1/teams/{id}` - delete specific team (DELETE)
* `/rest/v1/teams/{id}` - fetch specific team (GET)
* `/rest/v1/teams/{teamId}/users/{userId}` - remove specific user from specific team (DELETE)
* `/rest/v1/teams/{teamId}/users/{userId}` - add specific user to specific team (POST)
* `/rest/v1/users` - fetch all users (GET)
* `/rest/v1/users` - create new user (POST)
* `/rest/v1/users/{id}` - fetch specific user (GET)
* `/rest/v1/users/{id}` - delete specific user (DELETE)
* `/rest/v1/users/{id}/teams` - fetch all teams a user belongs to (GET)
