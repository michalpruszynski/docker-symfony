Symfony 6, PHP 8.1 with apache, mysql 8, optional PHPmyadmin

1. Create new symfony project with composer or symfony CLI
example:
$ symfony new my_project_directory --version="6.2.*" --webapp
$ cd my_project_directory
git clone this repo

2. Create SSL and put it into docker/server/cert as mycert.crt and mycert.key

for example:
$ openssl req -newkey rsa:4096  -x509  -sha512  -days 365 -nodes -out certificate.pem -keyout privatekey.pem


3. add to .env:
APP_NAME=
APP_PORT=
APP_DB_ADMIN_PORT=
DB_PORT=

MYSQL_ROOT_PASS=
MYSQL_USER=
MYSQL_PASS=
MYSQL_DB=


4. docker compose up -d



