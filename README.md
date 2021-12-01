# Docker IBM Informix database for dev

This repository shows how to start a Informix database and connect a C# application into it.


Docker
---------------------

Clone this repository and start the informix container:

```
$ docker-compose up
```

Based on docker image:
https://github.com/informix/informix-dockerhub-readme/blob/master/14.10.FC6/informix-developer-database.md


CSharp
---------------------

You follow the steps bellow to connect your C# application to informix database:

  * Install a NuGet package: IBM.Data.DB2.Core
  * Configure the connection string: "Server=localhost:9089;Database=<dbname>;UID=informix;PWD=<password>;Persist Security Info=True;Authentication=Server"

  
Example:
```
using (DB2Connection connection = new DB2Connection(connectionString))
{
  var comando = new DB2Command(@"SELECT * FROM Table", connection);
  connection.Open();
}
```

References:
https://github.com/andresrsanchez/ARS.IfxConnection
