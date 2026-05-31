# Database Setup

ZaminShop stores player-related data through its configured database backend.

This matters for features such as:

- favorites
- recent transactions
- player modifier data
- sell-related tracking

## Available backends

The current config supports:

- `sqlite`
- `mysql`

Default:

```yaml
database:
  type: sqlite
```

## SQLite

Use SQLite when:

- you run a single server
- you want the simplest setup
- you do not need an external database service

SQLite is the easiest starting point for most servers.

## MySQL

Use MySQL when:

- you prefer external database management
- you want the database managed outside the server folder
- you are operating in an environment where central SQL infrastructure is standard

Example:

```yaml
database:
  type: mysql
  mySQLHost: localhost
  mySQLPort: 3306
  mySQLDatabase: db
  mySQLUser: root
  mySQLPassword: ""
  tableNames:
    players: "players"
```

## What to check if MySQL fails

Check these first:

- host
- port
- database name
- username
- password
- firewall or container networking

## Practical advice

If you are still building the server:

- start with SQLite
- finish your menus and pricing
- switch to MySQL later only if you actually need it

That reduces setup complexity while you are still iterating on the shop itself.
