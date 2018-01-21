# migrate.sh
> simple postgresql migration system in bash

I wrote it for some Python project I worked on and wanted to have ActiveRecord-style migrations.
Alembic was too complex and I felt that creating a new Rails project for this job is too much.
And I wanted that it'd be super fast to use the generated schema with CI services.
Since SQL is cool and Bash is super fast - that's what we've got:

* Small bash file, so it's fast
* Uses transactions for DDLs (per migration)
* Stores schema SQL file so you can _load_ schema just by `psql`ing in CI

## Download
```bash
curl -L https://raw.githubusercontent.com/Schniz/migrate.sh/master/migrate.sh > migrate.sh
```

## Update
Same as download :boom:

## Usage

### Create a migration

```bash
./migrate.sh new my_migration_name
```

creates a migration file in `db/migrations/TIMESTAMP_my_migration_name.sql`

### Apply migrations

```bash
DATABASE_URL=postgresql://... ./migrate.sh up
```

### Load schema

```bash
DATABASE_URL=postgresql://... ./migrate.sh schema:load
```

loads a schema from `db/schema.sql` to the database

### Dump schema

```bash
DATABASE_URL=postgresql://... ./migrate.sh schema:dump
```

dumps the database schema to `db/schema.sq`l

## Development
It is currently works on OSX, which is my main machine.
Contributions are welcome!
