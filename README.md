<p align="right">
  <a href="#" target="_blank">
    MONARCH ETP
  </a>
</p>

# Introduction

This service is the authentication service for the MONARCH ETP, Ethiopian Trading platforms. Currently it has simple admin pannel fro the frontend but the backend server is capable of exposing both GraphQL and REST apis for JWT based auth. This service provides the different backend services related the authentication - i.e., REST APIs, GraphQL APIs, authentication, authorization, logging, data validation and the connection to the database. Additional information about the server component and the architecture around it, can be found on the [design files](https://docs.amplication.com/guides/getting-started) .

# Getting started with the backend

## Step 1: Configuration

Configuration for the server component can be provided through the use of environment variables. These can be passed to the application via the use of the `.env` file in the base directory of the generated service. Below a table can be found which show the different variables that can be passed - these are the variables which exist by default, through the use of plugins additional integrations could require additional values. These values are provided default values after generation, change them to the desired values.

| Variable             | Description                                  | Value                                                               |
| -------------------- | -------------------------------------------- | ------------------------------------------------------------------- |
| BCRYPT_SALT          | the string used for hashing                  | [random-string]                                                     |
| COMPOSE_PROJECT_NAME | the identifier of the service plus prefix    | amp_[service-identifier]                                            |
| PORT                 | the port on which to run the server          | 3000                                                                |
| DB_URL               | the connection url for the database          | [db-provider]://[username]:[password]@localhost:[db-port]/[db-name] |
| DB_PORT              | the port used by the database instance       | [db-provider-port]                                                  |
| DB_USER              | the username used to connect to the database | [username]                                                          |
| DB_PASSWORD          | the password used to connect to the database | [password]                                                          |
| DB_NAME              | the name of the database                     | [service-name] / [project-name]                                     |
| JWT_SECRET_KEY       | the secret used to sign the json-web token   | [secret]                                                            |
| JWT_EXPIRATION       | the expiration time for the json-web token   | 2d                                                                  |



## Step 2.1: Scripts - pre-requisites

After configuration of the server the next step would be to run the application. Before running the server side of the component, make sure that the different pre-requisites are met - i.e., node.js [^16.x], npm, docker. After the setup of the pre-requisites the server component can be started.

```sh
# installation of the dependencies
$ npm install

# generate the prisma client
$ npm run prisma:generate
```

## Step 2.2: Scripts - local development

```sh
# start the database where the server component will connect to
$ npm run docker:dev

# initialize the database
$ npm run db:init

# start the server component
$ npm run start
```
the default user and password are "admin" and "admin".

## Step 2.2: Scripts - container based development

```shell
# start the server component as a docker container
$ npm run compose:up
```

# Getting started with the frontend

# Getting started

## Step 1: Configuration

Configuration for the client component can be provided through the use of environment variables. These can be passed to the application via the use of the `.env` file in the base directory of the client service. Below a table can be found which show the different variables that can be passed. These values are provided default values after generation, change them to the desired values.

| Variable             | Description                                      | Value                           |
| -------------------- | ------------------------------------------------ |  ------------------------------ |
| PORT                 | the port on which to run the client              | 3001                            |
| REACT_APP_SERVER_URL | the url on which the server component is running | http://localhost:[server-port]  |



## Step 2: Scripts

After configuration of the client the next step would be to run the application. Before running the client side of the component, make sure that the different pre-requisites are met - i.e., npm, docker. Make sure that the server-side of the application is running.

```sh
# installation of the dependencies
$ npm install

# starts the application in development mode - available by default under http://localhost:3001 with a pre-configured user with the username "admin" and password "admin"
$ npm run start

# builds the application in production mode - available under 'build'
$ npm run build

# removes the single build dependency from the project
$ npm run eject
```
