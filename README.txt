Use the latest 7.1 ODBC driver to connect to any Kinetica server that is 7.0 or newer. Drivers from 6.2 and earlier are not able to talk to 7.0 Kinetica servers (or later).

KineticaODBCClient-64.msi and KineticaODBCClient-32.msi are the ODBC client installation packages.  You should install the one that matches the client you intend to use on Windows.  If your machine is 64-bit, and you want to use both 32-bit and 64-bit clients, you should install both.

For general information about ODBC client please see https://msdn.microsoft.com/en-us/library/ms714563(v=vs.85).aspx

The important fields for Kinetica ODBC driver are mentioned below.

Username and Password values are optional and can be left blank if not required by your server.

URL - This is the Kinetica GPUdb REST URL. Ask your Kinetica administrator about the server port in your enterprise. Example (and the default) - http://127.0.0.1:9191

