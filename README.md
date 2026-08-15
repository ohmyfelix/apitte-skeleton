# Apitte Skeleton

Nette API project skeleton built with [contributte/apitte](https://github.com/contributte/apitte), Nettrine, and Symfony components.

## Requirements

- PHP 8.4 or newer
- [Composer](https://getcomposer.org/)
- `make` for the provided development commands
- Docker Compose for the container stack

## Create a project

```bash
composer create-project contributte/apitte-skeleton acme
cd acme
make init
make project
make build
make dev
```

`make init` creates `config/local.neon` from `config/local.neon.example`. It defaults to PostgreSQL on `0.0.0.0:5432` with the `contributte` database and credentials. `make build` recreates the schema, runs migrations, and loads fixtures.

## Docker Compose

Start the stack with:

```bash
docker compose up
```

The application is available at `http://localhost:8000`, HTTPS at `https://localhost:8443`, Adminer at `http://localhost:8080`, PostgreSQL on port `5432`, and MariaDB on port `3306`. The Compose PHP service installs dependencies, runs migrations, and loads fixtures at startup.

For Compose, set the database host in `config/local.neon` to `postgres` or `mariadb` as appropriate.

## API and OpenAPI

- `GET http://localhost:8000/api/public/v1/openapi/meta` — OpenAPI document
- `GET http://localhost:8000/api/v1/users`
- `GET http://localhost:8000/api/v1/static/text`

Additional routes are defined by controllers under `app/Module`.

## Development

```bash
make qa       # coding standard and static analysis
make tests    # Nette Tester suite
make cs       # coding standard check
make csf      # fix coding standard issues
make phpstan  # static analysis
make coverage # generate coverage.xml
```
