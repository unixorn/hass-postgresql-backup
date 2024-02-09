<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
# hass-postgresql-backup

## Table of Contents

- [hass-postgresql-backup](#hass-postgresql-backup)
  - [Pre-requisites](#pre-requisites)
  - [Configuration](#configuration)
    - [ENV variables used](#env-variables-used)
  - [Usage](#usage)
  - [Updates](#updates)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Backup Home Assistant's database from a postgres server. If it finds a compression program (`bzip2`, `pbzip2`, `gzip` or `pigz`) it will also compress the SQL dump file.

## Pre-requisites

- `docker`

## Configuration

`hass-postgresql-backup` picks up its configuration from the session environment. It has some reasonable defaults that you can override by setting environment variables.

### ENV variables used

- `COMPRESSOR` - If you set this, also set `EXTENSION`. Defaults looking for `bzip2` and `gzip`, and will use `bzip2` if both are found.
- `DUMP_D` - What directory to write the dump file to. If you don't set this, it will use the current directory
- `HASS_D` - What postgres database to back up. Defaults to `homeassistant_db`
- `PG_PASSWORD` - The ha user's password
- `PG_SERVER` - What server to connect to
- `PG_USERNAME` - Used to log into your postgres server. Defaults to `homeassistant`. You can use the same username & password your Home Assistant is using.
- `POSTGRESQL_IMAGE` - What docker image to use. Defaults to `postgres:14.5`

## Usage

You only need to specify the parameters you wish to override from their default value. If you don't specify `COMPRESSOR`, it will check for `bzip2` and `gzip` programs (preferring `bzip2` when both are present) and automagically use what it finds to compress the dump file.

Example: `PG_PASSWORD=ha_pg_password PG_USER=ha_pg_user PG_SERVER=pg.example.com HASS_DB=homeassistant_db DUMP_D=/path/to/directory hass-postgresql-backup`

## Updates

As of 2024-02-07, the current version of Postgres is 16, and that's what this tool defaults to using.
