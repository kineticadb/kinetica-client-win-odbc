KineticaODBCClient-64.msi and KineticaODBCClient-32.msi are the ODBC client installation packages.  You should install the one that matches the client you intend to use on Windows.  If your machine is 64-bit, and you want to use both 32-bit and 64-bit clients, you should install both.

For general information about ODBC client please see https://msdn.microsoft.com/en-us/library/ms714563(v=vs.85).aspx

The important fields for Kinetica ODBC driver are mentioned below.

Username and Password values are optional and can be left blank if not required by your server.

Server IP - This is the Kinetica ODBC server IP or machine name. Ask your Kinetica administrator about the server IP in your enterprise. Example - 172.31.21.241

Server Port - This is the Kinetica ODBC server port. Ask your Kinetica administrator about the server port in your enterprise. Example (and the default) - 9292

After installing, if you get error 126 when trying to add a System DSN, you may need to download and install the "Visual C++ Redistributable Packages for Visual Studio 2013" from: http://www.microsoft.com/en-us/download/details.aspx?id=40784
