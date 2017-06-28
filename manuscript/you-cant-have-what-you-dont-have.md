# No puede tener lo que no se tiene

¿Puede ver lo que está mal?

![image023.png](images/image023.png)

Quiero decir, estoy bastante seguro de que tengo algunos servicios en ejecución. Se supone que algo se debía mostrar.

Si no ve la respuesta de inmediato - o no la ve - es un buen momento para hablar acerca de cómo solucionar problemas con algunas líneas de comandos. Para empezar, como siempre digo, retrocediendo un paso. Elimine el último comando, y vea si eso hace alguna diferencia.

![image025.png](images/image025.png)

En este caso, quité el comando Sort-Object (Sort) y no ocurrió nada diferente, así que eso no era la causa del problema. A continuación, eliminé el comando Where-Object (Where, en la sintaxis corta de v3), y ah-ha! Apareció la salida. Así que el comando Where-Object está “rompiendo” algo. Vamos a revisar lo que funcionó y a canalizarlo a Get-Member, para ver qué hay en la canalización (pipeline) después de ejecutar Select-Object.

![image027.png](images/image027.png)

OK, tengo un objeto que tiene una propiedad DisplayName y una propiedad Name.

Y mi comando Where-Object estaba comprobando la propiedad Status. ¿Ve una propiedad Status? No, no se ve. Mi error es que quité la propiedad Status cuando no la incluí en la lista de salida del comando Select-Object. Así que el objeto no tenía nada contra qué trabajar y no devolvió nada.

(Sí, sería mejor si PowerShell lanzara un error - "hey, pidio filtrar la propiedad Status, y no hay una!" - pero eso no así cómo funciona).

Moraleja de la historia: prestar atención a lo que está en la canalización (pipeline). No se puede trabajar con algo que no se tiene. No siempre obtendrá un mensaje de error útil, por lo que a veces tendrá que escarbar y averiguarlo de otra manera - como retrocediendo un paso.

