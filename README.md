# Apitte Skeleton

Nette API project skeleton built with [contributte/apitte](https://github.com/contributte/apitte), Nettrine, and Symfony components.

## Requirements

- PHP 8.4 or newer
- [Composer](https://getcomposer.org/)
- `make` for the provided development commands

## Create a project

```bash
composer create-project contributte/apitte-skeleton acme
cd acme
make init
make project
```

`make init` creates `config/local.neon` from `config/local.neon.example`. Choose and configure the database in that file before building or starting the application.

## Run with a native database

Configure `config/local.neon` for the PostgreSQL or MariaDB instance available on your host, then build the schema and start the server:

```bash
make build
make dev
```

`make build` recreates the schema, runs migrations, and loads fixtures.

## Run with Docker Compose

Docker Compose is an alternative to a native database. Before starting it, set the `database.host` in `config/local.neon` to `postgres` or `mariadb` to match the selected Compose service.

```bash
docker compose up
```

The tracked Compose file publishes the application on <http://localhost:8000> and also binds host ports `5432`, `3306`, `8080`, and `8443`. If any of those ports is already in use, Compose cannot start without changing the tracked port mapping.

## Verify and discover the API

The public OpenAPI endpoint verifies a successful request without authentication:

```bash
curl -s -o /dev/null -w '%{http_code}\n' http://localhost:8000/api/public/v1/openapi/meta
# 200
```

Open <http://localhost:8000/api/public/v1/openapi/meta> for the API definition. Routes below `/api/v1` require authentication; the tracked authenticator accepts an `X-Token` header or `_access_token` query parameter and matches it to a user API key. No token value is provided by this skeleton.

## Development

```bash
make qa       # coding standard and static analysis
make tests    # Nette Tester suite
make cs       # coding standard check
make csf      # fix coding standard issues
make phpstan  # static analysis
make coverage # generate coverage.xml
```
