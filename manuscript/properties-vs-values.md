# Propiedades vs. Valores

```
$names = Get-ADComputer -filter * |
 Select-Object -Property Name
 
 Get-CimInstance -Class Win32_BIOS -ComputerName $names 
 ```
 
¿Sabe por qué esto no funcionará? Porque el resultado de Get-ADComputer es un objeto que tiene propiedades. Usted probablemente sabía eso. Pero el resultado de Select-Object es también un objeto que tiene propiedades. Específicamente, en este caso, es un objeto "ADComputer " seleccionado, que tiene una sola propiedad: Name. 

Observe la ayuda del comando Get-CimInstance. El parámetro -ComputerName acepta objetos de tipo String. Así lo la ayuda. Pero un objeto ADComputer no es lo mismo que una cadena. La propiedad Name que se ha seleccionado contiene cadenas, pero no es una cadena en sí. Esto es una distinción enorme y es mejor no olvidarse de ello.

Piense en una propiedad como una caja. Esa caja puede contener cosas, pero es una cosa en y por sí misma, también. En este caso, la caja se denomina Name y contiene cadenas. Pero no se puede “empujar” toda la caja en algo que sólo estaba esperando Strings. "Hey, quería un String, no toda la caja"

Ahora piense en un Fax. ¿Recuerda esas máquinas? Recibían y transmitían páginas. Ahora suponga que tiene un sobre lleno de páginas. No se puede “empujar” el sobre en la máquina de fax y esperar resultados correctos. En esa analogía, el sobre es una propiedad, y las páginas dentro de ella son valores. Para lograr transmitir las páginas primero debe sacarlas del sobre.

Lo que quiere hacer en este caso es extraer las cadenas (Strings) de la caja, y Select-Object ofrece una manera de hacer eso:

```
$names = Get-ADComputer -filter * |
 Select-Object -ExpandProperty Name
 
 Get-CimInstance -Class Win32_BIOS -ComputerName $names
```

¿Ve la diferencia? -ExpandProperty obtiene sólo el contenido de la propiedad especificada, en lugar de devolver un objeto que sólo tiene esa propiedad. ¿Quiere una manera sencilla de probar esto en el shell? Ejecute este par de comandos:

```
Get-Service | Select -Property Name | Get-Member
Get-Service | Select -ExpandProperty Name | Get-Member
```
