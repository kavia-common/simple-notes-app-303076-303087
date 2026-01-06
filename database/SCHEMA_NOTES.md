# Notes table schema (MySQL)

This database container has been initialized with a `notes` table in the `myapp` database.

## Connection source of truth

`db_connection.txt` contains the canonical connection command:

```
mysql -u appuser -pdbuser123 -h localhost -P 5000 myapp
```

## Port confirmation

During execution, both ports **5000** and **5001** were reachable from the workspace environment.  
Querying the server via either port returns `@@port = 5000`, indicating the MySQL server itself is listening on **5000** and **5001** is a forwarded/exposed port that routes to the same MySQL instance.

For application configuration, use the values in `db_connection.txt` (port **5000**) as the primary source of truth.

## Schema

Table: `notes`

Columns:

- `id` INT AUTO_INCREMENT PRIMARY KEY
- `title` VARCHAR(255) NOT NULL
- `content` TEXT NOT NULL
- `created_at` TIMESTAMP DEFAULT CURRENT_TIMESTAMP
- `updated_at` TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP

The table was created with:

- Engine: InnoDB
- Charset: utf8mb4
- Collation: utf8mb4_unicode_ci
