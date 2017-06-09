# keycloak-openshift-mysql

Fork of the [Keycloak Openshift docker image](https://github.com/jboss-dockerfiles/keycloak/tree/master/server-openshift) modified to extend the [Keycloak MySql docker image](https://github.com/jboss-dockerfiles/keycloak/tree/master/server-mysql)

## Usage

### Start a MySQL instance

First start a MySQL instance using the MySQL docker image:

    docker run --name mysql -e MYSQL_DATABASE=keycloak -e MYSQL_USER=keycloak -e MYSQL_PASSWORD=password -e MYSQL_ROOT_PASSWORD=root_password -d mysql

### Start a Keycloak instance

Start a Keycloak instance and connect to the MySQL instance:

    docker run --name keycloak --link mysql:mysql jboss/keycloak-mysql

### Environment variables

When starting the Keycloak instance you can pass a number of environment variables to configure how it connects to MySQL. For example:

    docker run --name keycloak --link mysql:mysql -e MYSQL_DATABASE=keycloak -e MYSQL_USERNAME=keycloak -e MYSQL_PASSWORD=password jboss/keycloak-mysql

#### MYSQL_DATABASE

Specify name of MySQL database (optional, default is `keycloak`).

#### MYSQL_USER

Specify user for MySQL database (optional, default is `keycloak`).

#### MYSQL_PASSWORD

Specify password for MySQL database (optional, default is `keycloak`).

#### PROXY_ADDRESS_FORWARDING

Set to true when running Keycloak behind a reverse proxy
