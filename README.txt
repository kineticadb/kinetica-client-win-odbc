The 7.1 ODBC Driver will not work with GPUdb Servers lower than 7.1.  Or vice versa -- the previous ODBC Drivers will not connect to a GPUdb Server version 7.1 or later.

KineticaODBCClient-64.msi and KineticaODBCClient-32.msi are the ODBC client installation packages.  You should install the one that matches the client you intend to use on Windows.  If your machine is 64-bit, and you want to use both 32-bit and 64-bit clients, you should install both.

For general information about ODBC client please see https://msdn.microsoft.com/en-us/library/ms714563(v=vs.85).aspx

The important fields for Kinetica ODBC driver are mentioned below.

Username and Password values are optional and can be left blank if not required by your server.

URL - This is the Kinetica GPUdb REST URL. Ask your Kinetica administrator about the server port in your enterprise. Example (and the default) - http://127.0.0.1:9191

