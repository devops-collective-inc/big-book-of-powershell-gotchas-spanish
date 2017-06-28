# -Filter y la diversidad de valores
Esta es una de las cosas más difíciles de acostumbrarse en PowerShell:

![image029.png](images/image029.png)

Aquí vemos tres comandos, cada uno usando un parámetro -Filter. Cada uno de esos filtros es diferente.

1. Con Get-ChildItem, -Filter acepta los comodines del sistema de archivos como *.
2. Con Get-WmiObject, -Filter requiere una cadena, y utiliza operadores de estilo de programación (como = para la igualdad).
3. Con Get-ADUser, -Filter requiere un bloque de script, y acepta operadores de comparación de estilo PowerShell (como -eq para la igualdad)

Esto es lo que pienso cuando se utiliza un parámetro –Filter. PowerShell no está procesando el filtrado. En su lugar, los criterios de filtrado se están transmitiendo a la tecnología subyacente, como el sistema de archivos, o WMI, o al directorio activo. Es esta tecnología la que decide qué tipo de criterios de filtro se van a aceptar. PowerShell es sólo el intermediario. Así que es mejor leer cuidadosamente la ayuda, y tal vez buscar ejemplos, para entender cómo la tecnología subyacente necesita que especifique su filtro.

Sí, sería bueno si PowerShell tradujera para usted (que es realmente lo que hace Get-ADUser - el comando traduce eso en un filtro de LDAP tras bambalinas). Pero, por lo general, no lo hace.
