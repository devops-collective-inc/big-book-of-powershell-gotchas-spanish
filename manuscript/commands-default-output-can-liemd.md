# La salida predeterminada de los comandos puede mentir
Bien, tal vez no "mentir", pero ciertamente si "engañar".

Intente ejecutar Get-EventLog -LogName Security en su equipo. ¿Nota los encabezados de columna en la salida?

* La salida no incluye todas las propiedades que están disponibles tras bambalinas.
* Algunos de los encabezados de columna realmente no muestran el nombre correcto para esa propiedad.

Esto puede ser realmente frustrante, porque si intenta usar Select-Object con un nombre incorrecto, solo obtendrá espacios en blanco. La confusión surge porque la salida de muchos comandos se pre-formatea usando una vista predeterminada. Eso significa que en realidad no está viendo la "salida" del comando, sino viendo una versión "maquillada" de la misma

Para ver la salida completa, con los nombres de propiedad correctos, ejecute su comando y canalícelo a `| Format-List *` (o fl * si lo prefiere). Los comandos que producen una gran cantidad de datos de salida pueden tomar algún tiempo para ejecutar y crear una pantalla “sucia”. Una versión más corta puede ser enviar mediante la canalización (pipeline) de su comando a  `| Select -First 1 | Format-List *`. Verá un objeto de salida con todas sus propiedades y los nombres correctos de las mismas listos para usar en otros comandos.



