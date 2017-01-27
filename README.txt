<sandbox>\gpudb-client-odbc\gpudb-odbc-driver-windows\x64\GPUdbODBCClient.10.1.msi is the ODBC client side package installation - 
This is the installation package for the ODBC driver.

For general information about ODBC client please see https://msdn.microsoft.com/en-us/library/ms714563(v=vs.85).aspx

The important fields for Kinetica ODBC driver are mentioned below.

Username and Password values are not used and can be left blank.

URL is the address for your Kinetica server. Ask your Kinetica administrator about the Kinetica server IP. Example - http://172.31.21.241:9191

Parent Set - This value should normally be MASTER. But it can be set to any valid collection name which exists in Kinetica DB.

Server IP - This is the Kinetica ODBC server IP. Ask your Kinetica administrator about the server IP in your enterprise. Example - 172.31.21.241

Server Port - This is the Kinetica ODBC server port. Ask your Kinetica administrator about the server port in your enterprise. Example - 9292
