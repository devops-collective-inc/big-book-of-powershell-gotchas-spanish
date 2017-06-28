# -Contains y -Like son diferentes


Si tuviera un centavo por cada vez que he visto esto:

![image015.png](images/image015.png)

Entiendo cómo sucede. El operador -Contains parece que debería comprobar si el nombre de un proceso contiene las letras "notepad". Pero eso no es lo que hace.

El enfoque correcto es utilizar el operador -Like, que de hecho hace una comparación de cadena con comodines:

![image017.png](images/image017.png)

Voy a dejar pasar la idea de que la respuesta realmente correcta es ejecutar Stop-Process -Name *notepad *, porque estaba apuntando a un ejemplo simple aquí. Pero ... no piense demasiado. A veces un script en un bucle foreach no es el mejor enfoque.

Así que de todos modos, ¿qué hacen -Contains (y su amigo, -NotContains) en realidad? Son similares a los operadores -In y -NotIn introducidos en PowerShell v3. Estos operadores pueden causar un poco de confusión. Lo que hacen es comprobar si una colección de objetos contiene un único objeto dado. Por ejemplo:

![image019.png](images/image019.png)

De hecho, este ejemplo es probablemente la mejor manera de verlo funcionar. El truco es que, cuando se utiliza un objeto complejo en lugar de un valor simple (como lo hice en ese ejemplo), -Contains e -In buscan en todas las propiedades del objeto para encontrar una coincidencia. Si piensa en algo como un proceso, ellos siempre estarán cambiando. De cuando en cuando, la CPU y la memoria de un proceso, pueden ser diferentes.

![image021.png](images/image021.png)

En este ejemplo, he iniciado el bloc de notas. He puesto su objeto de proceso en $single_proc, y se puede ver que he verificado que estaba allí. Pero cuando ejecuto Get-Process para comprobar si la colección contenía mi Notepad, el resultado fue falso. Eso es porque el objeto en $single_proc está desactualizado. Notepad está en ejecución, pero ahora se ve diferente, por lo que -Contains no puede encontrarlo.

Los operadores -in y -contains son mejores con valores simples, o con objetos que no tienen valores de propiedad que cambian constantemente. Pero no son operadores de coincidencia de cadenas de caracteres comodines. Use-like (o -notlike) para eso.
