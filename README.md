<h3 align="center" style="margin:0px">
	<img width="200" src="https://kinetica-web-assets.s3.us-east-1.amazonaws.com/assets/kinetica_logo_gray.svg" alt="Kinetica Logo"/>
</h3>
<h5 align="center" style="margin:0px">
	<a href="https://www.kinetica.com/">Website</a>
	|
	<a href="https://docs.kinetica.com/7.2/">Docs</a>
	|
	<a href="https://docs.kinetica.com/7.2/connectors/sql_guide/">ODBC Docs</a>
	|
	<a href="https://join.slack.com/t/kinetica-community/shared_invite/zt-1bt9x3mvr-uMKrXlSDXfy3oU~sKi84qg">Community Slack</a>   
</h5>


# Kinetica JDBC Driver

-  [Overview](#overview)
-  [Install](#install)
-  [Configure](#configure)
-  [Connect](#connect)
-  [Examples](#examples)
-  [Documentation](#documentation)
-  [Support](#support)
-  [Contact Us](#contact-us)
 

## Overview

The Kinetica ODBC Driver supports connections from a wide array of ODBC-aware
applications to the Kinetica database.


Ideally, the version of the driver must match that of the database; e.g., the
7.2 version of the driver is interoperable with any Kinetica 7.2.X.Y database.
However, the 7.2 driver may be compatible with 7.1 database instances for most
use cases.


## Install

Kinetica ODBC can be installed for Windows or Linux.

### Windows

`KineticaODBCClient-64.msi` and `KineticaODBCClient-32.msi` are the ODBC client
installation packages.  You should install the one that matches the client you
intend to use on Windows.  If your machine is 64-bit, and you want to use both
32-bit and 64-bit clients, you should install both.

For general information about ODBC client please see
https://msdn.microsoft.com/en-us/library/ms714563(v=vs.85).aspx

### Linux

The Kinetica ODBC client for Linux can be found on the head node of any Kinetica
cluster, here:

    /opt/gpudb/connectors/odbc/lib/libKineticaODBC.so

This library has been compiled for use on the head node, so any clients using it
should also reside there.


## Configure

Kinetica ODBC configuration parameters are the same between Windows and Linux,
though the configuration mechanism is different between the two.

### Windows

Use the Windows "ODBC Data Sources" applet to add/remove/configure connection
parameters.

### Linux

Kinetica Linux ODBC connections and driver are configured via two files:
`odbc.ini` and `kineticaODBC.ini`.

The `odbc.ini` file contains information about ODBC connections (i.e., DSN).
This file comes preconfigured with a connection to GPUdb running on the local
machine on port `9191`.  The `odbc.ini` file is looked for in the following
places, in this order:

* `~/.odbc.ini` (i.e., in the user's home directory, with a leading `.`)
* `ODBCINI` environment variable
* `/opt/gpudb/connectors/odbc/etc`

This file contains the standard Kinetica connection parameters, as well as the
following Linux-specific one:

* **Driver**: The file name and path of the `libKineticaODBC.so`

The `kineticaODBC.ini` file is used by the Kinetica ODBC Driver.  It is looked
for in the following places, in this order:

* The driver directory, as a non-hidden `.ini` file
* The directory that the client application is launched from.
* `~/.kineticaODBC.ini`
* In `/etc/` as a non-hidden `.ini` file

This file is where you set:

* **LogLevel**: Controls how much information is written to the logs - the
  higher the number, the more info that is written.  `6` = Trace, `5` = Debug,
  `4` = Info, `3` = Warn, `2` = Error, `1` = Fatal, `0` = Off (Default: `0`)
* **LogPath**: Folder to write log files to
* **ErrorMessagesPath**: Path to error messages files (`*.xml`)

### Common Connection Parameters

For the full parameter set, see
[ODBC/JDBC Connection Guide](https://docs.kinetica.com/7.2/connectors/sql_guide/#odbc-jdbc-configuration).

| Parameter      | Description
| :---           | :---
| `URL`          | Kinetica connection URL; used in lieu of the default host/port configuration for SSL or failover connections
| `UID`          | Connection user ID
| `PWD`          | Connection user password
| `Timeout`      | Minutes to wait for a server response; no timeout is `0` (default)
| `RowsPerFetch` | Number of rows to be requested in a query at a time; default is 10,000 rows


### SSL Parameters

| Parameter              | Description
| :---                   | :---
| `BypassSslCertCheck`   | Allow (`1`) or disallow (`0`) the Kinetica certificate host name and server host name to be different
| `SslCACertPath`        | Path to client's trust store, used to validate the certificate from the Kinetica server


## Documentation
- [Full Documentation](https://docs.kinetica.com/7.2/)
- [ODBC/JDBC Connection Guide](https://docs.kinetica.com/7.2/connectors/sql_guide/)


## Support

For bugs, please submit an
[issue on Github](https://github.com/kineticadb/kinetica-client-win-odbc/issues).

For support, you can post on
[stackoverflow](https://stackoverflow.com/questions/tagged/kinetica) under the
``kinetica`` tag or
[Slack](https://join.slack.com/t/kinetica-community/shared_invite/zt-1bt9x3mvr-uMKrXlSDXfy3oU~sKi84qg).


## Contact Us

* Ask a question on Slack:
  [Slack](https://join.slack.com/t/kinetica-community/shared_invite/zt-1bt9x3mvr-uMKrXlSDXfy3oU~sKi84qg)
* Follow on GitHub:
  [Follow @kineticadb](https://github.com/kineticadb) 
* Email us:  <support@kinetica.com>
* Visit:  <https://www.kinetica.com/contact/>
