# Database

ZaminShop supports database-backed player data.

Default:

```yaml
database:
  type: sqlite
```

Supported config values:

```yaml
database:
  type: sqlite
  mySQLHost: localhost
  mySQLPort: 3306
  mySQLDatabase: db
  mySQLUser: root
  mySQLPassword: ""
  tableNames:
    players: "players"
```

## SQLite

Use SQLite for simple servers or first setup.

## MySQL

Use MySQL if you need external database storage.

Set:

```yaml
database:
  type: mysql
```

Then configure host, port, database, user, and password.
