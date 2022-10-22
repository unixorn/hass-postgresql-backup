# hass-postgresql-backup

Backup Home Assistant's database from a postgres server

## Pre-requisites

- `docker`

## Configuration

`hass-postgresql-backup` picks up its configuration from the session environment. It has some reasonable defaults that you can override by setting environment variables

### ENV variables used

- `COMPRESSOR` - If you set this, also set `EXTENSION`. Defaults looking for `bzip2` and `gzip`, and will use `bzip2` if both are found.
- `DUMP_D` - What directory to write the dump file to. If you don't set this, it will use the current directory
- `HASS_D` - What database to back up. Defaults to `homeassistant_db`
- `PG_PASSWORD` - The user's password
- `PG_SERVER` - What server to connect to
- `PG_USERNAME` - Used to log into your postgres server. Defaults to `homeassistant`
- `POSTGRESQL_IMAGE` - What docker image to use. Defaults to `postgres:14.5`

## Usage

You only need to specify the parameters you wish to override from their default value. If you don't specify `COMPRESSOR`, it will check for `gzip` and `bzip2` programs and use that to compress the dump file.

`PG_PASSWORD=ha_pg_password PG_USER=ha_pg_user PG_SERVER=pg.example.com HASS_DB=homeassistant_db DUMP_D=/path/to/directory hass-postgresql-backup`
