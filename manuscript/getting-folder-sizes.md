# Obtener tamaños de carpetas

La gente suele preguntar cómo usar PowerShell para obtener el tamaño de una carpeta. Por ejemplo la carpeta de documentos de un usuario.

El problema es que _las carpetas no tienen un tamaño_. Windows literalmente no rastrea el tamaño de los objetos de carpeta. El tamaño de una carpeta es simplemente la suma de los tamaños de los archivos en dicha carpeta, lo que significa que para obtener el tamaño de la carpeta se tiene que sumar el tamaño de los archivos.

```
Get-ChildItem -Path <whatever> -File -Recurse |
Measure-Object -Property Length -Sum
```

Veamos un ejemplo. Primero, es necesario obtener todos los archivos, y luego sumar sus propiedades de tamaño.



