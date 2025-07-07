# Kinetica OBDC Connector Changelog


## Version 7.2

### Version 7.2.0.0 - 2024-06-26

*   Releasing version


## Version 7.1

### Version 7.1.9.16 - 2024-02-07

*   Releasing version

### Version 7.1.9.15 - 2023-12-20

*   Releasing version

### Version 7.1.8.5 - 2022-12-03

*   Releasing version

### Version 7.1.5.3 - 2021-10-25

*   Releasing version

### Version 7.1.4.0 - 2021-07-14

*   Releasing version

### Version 7.1.0.0 - 2020-08-04

*   Releasing version


## Version 7.0

### Version 7.0.14.0 - 2020-03-23

*   Releasing version

### Version 7.0.10.0 - 2019-11-14

*   Releasing version

### Version 7.0.9.0 - 2019-10-29

*   Releasing version

### Version 7.0.8.0 - 2019-09-18

*   Releasing version

### Version 7.0.7.0 - 2019-08-23

*   Releasing version

### Version 7.0.6.2 - 2019-08-14

*   Releasing version

### Version 7.0.6.0 - 2019-07-24

*   Releasing version

### Version 7.0.5.0 - 2019-06-26

*   Releasing version

### Version 7.0.4.0 - 2019-06-12

*   Releasing version

### Version 7.0.3.0 - 2019-05-02

*   Releasing version

### Version 7.0.2.0 - 2019-04-15

*   Releasing version

### Version 7.0.1.0 - 2019-03-10

*   Releasing version

### Version 7.0.0.0 - 2019-02-25

*   Releasing version


## Version 6.2

### Version 6.2.0.0 - 

*   Added `ROLLUP`, `CUBE`, and `GROUPING SETS`
*   Added `WINDOW`/`PARTITION`
*   Added `PIVOT` and `UNPIVOT`
*   Added Query Caching
*   Added Materialized Views

    -   `CREATE [OR REPLACE] [TEMP | VRAM] [MATERIALIZED] VIEW <name> [REFRESH {OFF | ON CHANGE | EVERY <number> {MINUTE[S] | HOUR[S] | DAY[S]} [STARTING AT <YYYY-MM-DD [HH:MM[:SS]]>]}] AS SELECT ...`
    -   `DROP [MATERIALIZED] VIEW [IF EXISTS] <name>`
    -   `REFRESH [MATERIALIZED] VIEW <name>`
    -   `ALTER [MATERIALIZED] VIEW <name> SET REFRESH {OFF | ON CHANGE | EVERY <number> {MINUTE[S] | HOUR[S] | DAY[S]} [STARTING AT <YYYY-MM-DD [HH:MM[:SS]]>]}`
    -   `ALTER [MATERIALIZED] VIEW <name> RENAME TO <new_name>`
    -   `ALTER [MATERIALIZED] VIEW <name> SET TTL ttl`
    -   `ALTER [MATERIALIZED] VIEW <name> SET PROTECTED (TRUE | FALSE)`
    -   `ALTER [MATERIALIZED] VIEW <name> (SET SCHEMA|MOVE TO) <schema_name>`
    -   `ALTER [MATERIALIZED] VIEW <name> SET ACCESS MODE {NO_ACCESS | READ_ONLY | WRITE_ONLY | READ_WRITE}`

*   Added `KI_MATCH_COLUMN(col)` to create a dummy column to match up with
    `KI_FORCE_REPLICATED()`.  It also takes a parameter.
*   Improved `SQL_BIT`, `SQL_TINYINT`, and `SQL_SMALLINT`
*   Use `__TEMP` as default collection for temp tables (instead of `TEMP`)
*   Use Bulk Ingestor to insert data
*   Added `KI_HINT_CHUNK_SIZE(n)`
*   Added `KI_HINT_NO_DICT_PROJECTION`
*   Bug fixes


## Version 6.1

### Version 6.1.0.12 - 2017-12-08

*	Added `KI_HINT_NO_JOIN_COUNT` hint

### Version 6.1.0.0 - 2017-11-13

*	Added `Timeout` setting for GPUdb API timeout
*	Added support to access other GPUdb collections via SQL schema (e.g.,
    `<schema>.<table_name>`)
*	Added support for `OFFSET` (`LIMIT` with 2 parameters, first is `OFFSET`,
    second is `LIMIT`)
*	Added `DSN` called `KINETICA` (to start the same as `GPUDBDSN`)
*	Added support for list expressions like: `WHERE (x, y) = ('a', 42)`
*	Added support for writing to file (CSV) tables, including creating them
    (e.g., `CREATE TABLE AS`)
*	Added `GEOMETRY`, `ST_GEOMETRY`, and `WKT` types (to make GPUdb columns that
    are `STRING` with `WKT` attribute)
*   Added support for `BINARY` columns (creating, and supporting tables with
    such columns)
*   Added support for `DATETIME` GPUdb attribute
*   Added support for `DICT`, `INT8`, and `INT16` GPUdb attributes
*   Added support for queries without a `FROM` clause (which `SELECT`
    expressions without references to columns) (i.e., like Oracle's `DUAL`)
*	Added `TempCollection` setting (where to put temp tables)
*   Added support for new auto-increment type parameter
*   Added support for `ATTR` aggregate function (determines if all values of a
    column are the same)
*   Added `CertPath` and `SslAllowHostMismatch` config options
*   Added support for `CREATE VRAM TABLE AS` (only supported with `AS` command)
*   Added support for `CREATE TEMP TABLE` (without `AS` option)
*   Added hint `KI_HINT_JOBID_PREFIX(x)` to add "x" to the JobId (ODBC_x_GUID)
*	Catalogs, schemas, and tables can be unquoted, quoted with double-quotes
    ("), back-ticks (`), or square-brackets ([])
*	`CATALOG` is now `KINETICA`
*   Improved `INSERT INTO` support to make it more efficient (and avoid
    transfering data)
*	Changed `TTL` and `MaxQueryDimensions` to be strings.  Blank string means do
    not override server setting.  Default `TTL` is now 1 hour.
*   Renamed log files: `GPUdbODBC_driver.log` -> `odbc.log` and
    `odbcserver.log` -> `odbcconsole.log`
*   Renamed ini file: `GISFederal.GPUdbODBC.ini` -> `gpudbodbc.ini`
*   `GPUDB_RANK()`, `GPUDB_CHUNK()`, and `GPUDB_TOM()` now take optional
    parameters, so you can specify a column there to help use the functions in
    `GROUP BY` expressions.
*	Support security and additional `ALTER TABLE`/`SCHEMA` commands:

	- `CREATE USER @u`
	- `CREATE USER u [[WITH] PASSWORD [=] 'p']`
	- `CREATE ROLE r`
	- `DROP ROLE r`
	- `DROP USER u`
	- `GRANT r TO ur`
	- `GRANT SYSTEM {ADMIN | WRITE |READ} TO ur`
	- `GRANT {SELECT | INSERT | UPDATE | DELETE | ALL} [PRIVILEGES] ON [TABLE] t TO ur`
	- `REVOKE r FROM ur`
	- `REVOKE SYSTEM {ADMIN | WRITE |READ} FROM ur`
	- `REVOKE {SELECT | INSERT | UPDATE | DELETE | ALL} [PRIVILEGES] ON [TABLE] t TO ur`
	- `ALTER TABLE t SET ACCESS MODE {NO_ACCESS | READ_ONLY | WRITE_ONLY | READ_WRITE}`
	- `SHOW SECURITY [FOR ur [, ur [...]]]`
    - `ALTER TABLE table_name SET COLUMN column_name COMPRESSION [TO] compression_type`
    - `ALTER TABLE table_name SET PROTECTED (TRUE | FALSE)`
    - `ALTER TABLE table_name (SET SCHEMA|MOVE TO) schema_name`
    - `ALTER TABLE x ADD/DROP INDEX (y)`
    - `CREATE SCHEMA x (synonym: CREATE COLLECTION x)`
    - `DROP SCHEMA [IF EXISTS] x [CASCADE] (synonym: DROP COLLECTION ...)`
    - `ALTER SCHEMA schema_name ALLOW HOMOGENEOUS [TABLES] (TRUE | FALSE)`
    - `ALTER SCHEMA schema_name SET PROTECTED (TRUE | FALSE)`
	- `ALTER SCHEMA schema_name RENAME TO new_schema_name`
	- `ALTER SCHEMA schema_name SET TTL ttl`
	- `ALTER SCHEMA t SET ACCESS MODE {NO_ACCESS | READ_ONLY | WRITE_ONLY | READ_WRITE}`

*   Experimental feature: `KI_SHARD_KEY(col1, col2, ...)`
*	Bug fixes


## Version 6.0

### Version 6.0.1.0 - 2017-04-03

*	Added support for `CREATE TEMP TABLE AS`
*	Added support for `CREATE TABLE AS`, for persisted tables
*	Added support for hints
*	Added support for `DELETE` and `UPDATE`
*	Added support for security
*	Column names are case insensitive, unless enclosed in double quotes
*	Optimized cross joins in most cases
*	Use `TTL` option when creating tables, rather than separate alter table call
*	Added support for GPUdb-specific aggregate functions: `stddev_samp`,
    `var_samp`.
*	Added support for creating replicated tables.  Use:
    `CREATE REPLICATED TABLE ...`
*	Added support for `DATEDIFF` (MySQL).
*	Added support for `DECODE`
*	Added support for `ALTER TABLE`

	- `ALTER TABLE table_name ADD column_name datatype`
	- `ALTER TABLE table_name DROP COLUMN column_name`
	- `ALTER TABLE table_name ALTER COLUMN column_name datatype`
	- `ALTER TABLE table_name MODIFY COLUMN column_name datatype`
	- `ALTER TABLE table_name MODIFY column_name datatype`
	- `ALTER TABLE table_name RENAME COLUMN old_name TO new_name`
	- `ALTER TABLE table_name CHANGE COLUMN old_name TO new_name`
	- `ALTER TABLE table_name RENAME TO new_table_name`
	- `ALTER TABLE table_name SET TTL ttl`

*	Added support for `EXCEPT` and `INTERSECT`
*	Added support for Common Table Expressions (CTE) -- i.e., `WITH`
*	Added support for `INTERVAL` syntax
*	Added `CacheTimeoutSeconds` support
*	Added support for having `GROUP BY` result in a replicated table

	- Add dummy aggregate function `force_replicated(column)` to the `SELECT`
	  list to have just that `GROUP BY` be replicated
	- Hint: `KI_HINT_GROUP_BY_FORCE_REPLICATED` to have all `GROUP BY` calls in
	  that query be replicated
	- Setting: `GroupByForceReplicated` can be set at the server and overridden
	  by a client connection string, to have all `GROUP BY` statements for that
	  connection be replicated

*	Added support for `TRUNCATE TABLE`
*	Bug fixes

## Version 6.0.0 - 2017-01-27

*	Removed `store_only` and unlimited string restrictions (from ODBC)
*	Setting for case sensitive column nmaes (all-or-nothing)
*	Added support for `CREATE TABLE` and `DROP TABLE` commands
*	Added support for `SQL_TSI_FRAC_SECOND` date/time units
*	Added support for `CURRENT_DATE`, `CURRENT_TIME`, and `CURRENT_TIMESTAMP`
    functions
*	Added support for `UNION DISTINCT` clause
*	Added support for `DECIMAL`, `DATE`, and `TIME` data types
*	Added support for logging in with username and password
*	Added support for `CASE` function
*	Added support for `LIKE` function
*	Added support for fixed-width character string types and nullability
*	Optimization: Combine multiple joins into a single call, when possible
*	Optimization: Reuse temp tables when possible
