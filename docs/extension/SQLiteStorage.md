---
id: SQLiteStorage
title: SQLite Storage
sidebar_label: SQLite Storage
---

stores all *data points* and *events* on a hard drive.

It accumulates historical data and enables access for visualization or analysis.

Properties:

```ini
databasePath = %ProgramData%\Automation Garage\AutoBits
databaseName = Database.sqlite
```

- `databasePath` - path to a folder where the database is created
- `databaseName` - name of database file

It is also possible to configure SQLite to store *data points* and *events* in memory:

```ini
storeDatabase = in memory
```

In the case of in-memory storage, properties `databasePath` and `databaseName` are not required.

*(Note, that if you use in-memory storage, all data is lost when you exit or restart AutoBits. In-memory data will also be lost, when you restart this extension, for example by updating and saving the configuration)*