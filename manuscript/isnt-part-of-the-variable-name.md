# $ no forma parte del nombre de la variable
Gran “trampa”.

![image049.png](images/image049.png)

¿Puede predecir el resultado?

![image051.png](images/image051.png)

Observe que el símbolo de moneda $ no forma parte del nombre de la variable. Si tiene una variable llamada example, que es como tener una caja con la palabra " example" escrito al costado. Cuando se refiere a example significa que está hablando de la caja misma. Cuando se refiere a $ example significa que está haciendo referencia al contenido de la caja.

Así que en mi ejemplo, he utilizado $example = 5 para poner un 5 en la caja. Luego, cree una nueva variable. El nombre de la nueva variable fue $example – que como lleva el símbolo de moneda, en realidad hace referencia al valor de la variable $example que es 5. Así que lo que ocurrió en realidad fue que se creó una variable llamada 5, que tiene asignado el valor 6, a la que se puede hacer referencia por el nombre  $5.

Difícil, ¿verdad? Lo es:

![image053.png](images/image053.png)

En ese ejemplo, utilicé el parámetro -ErrorVariable para especificar una variable en la que se almacenaría cualquier error que se produzca. El problema es, he utilizado $x cuando debería haber utilizado solo x (sin el símbolo de moneda):

![image055.png](images/image055.png)

Ahora la forma correcta. Utilizando solo x, a la que más tarde se puede acceder usando $x para obtener su contenido, es decir, cualquier error que haya sido almacenado allí.
