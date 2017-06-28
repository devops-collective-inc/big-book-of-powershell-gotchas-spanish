# Escribiendo en SQL Server
Guardar datos en un servidor SQL - frente a Excel o algún otro formato - es muy fácil.

Suponga que tiene SQL Server Express instalado localmente. Ha creado una base de datos llamada mydb y una tabla llamada mytable. La tabla tiene dos columnas ColumnA y ColumnB, y ambas son campos de cadenas (varchar). El archivo de base de datos está ubicado en c:\myfiles\mydb.mdf. Esto es muy fácil de configurar en un GUI si descarga la versión de SQL Server Express "con herramientas". Es gratis!

```
$cola = "Data to go into ColumnA"
$colb = "Data to go into ColumnB"

$connection_string = "Server=.\SQLExpress;AttachDbFilename=C:\Myfiles\mydb.mdf;Database=mydb;Trusted_Connection=Yes;"
$connection = New-Object System.Data.SqlClient.SqlConnection
$connection.ConnectionString = $connection_string
$connection.Open()
$command = New-Object System.Data.SqlClient.SqlCommand
$command.Connection = $connection

$sql = "INSERT INTO MYTABLE (ColumnA,ColumnB) VALUES('$cola','$colb')"
$command.CommandText = $sql
$command.ExecuteNonQuery()

$connection.close()
```

Puede insertar una gran cantidad de valores simplemente haciendo un bucle a través de las tres líneas que definen la sentencia SQL y ejecutarla:

```
$cola = @('Value1','Value2','Value3')
$colb = @('Stuff1','Stuff2','Stuff3')

$connection_string = "Server=.\SQLExpress;AttachDbFilename=C:\Myfiles\mydb.mdf;Database=mydb;Trusted_Connection=Yes;"
$connection = New-Object System.Data.SqlClient.SqlConnection
$connection.ConnectionString = $connection_string
$connection.Open()
$command = New-Object System.Data.SqlClient.SqlCommand
$command.Connection = $connection

for ($i=0; $i -lt 3; $i++) {
  $sql = "INSERT INTO MYTABLE (ColumnA,ColumnB) VALUES('$($cola[$i])','$($colb[$i])')"
  $command.CommandText = $sql
  $command.ExecuteNonQuery()
}

$connection.close()
```

Es igual de fácil ejecutar consultas de actualización o eliminación. Las consultas de selección usan ExecuteReader() en lugar de ExecuteNonQuery() y devuelven un objeto SqlDataReader que se puede utilizar para leer datos de cada columna o avanzar a la siguiente fila en el conjunto de resultados.
