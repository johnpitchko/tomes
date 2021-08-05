# Tome of PostgreSQL

## Sources
* https://medium.com/@viviennediegoencarnacion/getting-started-with-postgresql-on-mac-e6a5f48ee399
* https://devcenter.heroku.com/articles/getting-started-with-rails6#add-the-pg-gem

## Install and configure PostgreSQL

1. Install PostgreSQL. If using macOS, you can install PostgreSQL via [Homebrew](https://www.brew.sh).

```bash
$ brew install postgresql
```

Be sure to launch PostgreSQL after installing. Running command below will configure PostgreSQL to automatically launch on system start

```bash
$ brew services start postgresql
```

1. Create a user for your Rails app. 

```bash
$ psql postgres

postgres=# CREATE ROLE user WITH LOGIN PASSWORD 'password';

ALTER ROLE user SUPERUSER;

\q
```

2. Update values in `config/database.yml`.

3. Create and load the database.

```bash
$ rails db:create
$ rails db:migrate
$ rails db:seed
```

## Command quick-reference

### List users

```
/du
```
