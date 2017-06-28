# [Sangriento] {Horrible} (Puntuación)
Esto no un “truco” pero vale la pena revisarlo para que no resulte confuso. Las tuercas de PowerShell con la puntuación.

![image041.png](images/image041.png)

(Paréntesis) se utilizan para encerrar expresiones, como la expresión foreach() y en ciertos casos para resaltar alguna sintaxis declarativa. Por ejemplo el bloque param() y en el atributo [parameter()].

[Corchetes cuadrados] se utilizan alrededor de algunos atributos, como en [CmdletBinding()], y alrededor de tipos de datos como [string]. También se utilizan para indicar arrays - como en [string[]]. Pueden aparecer en otros lugares.

{Corchetes} casi siempre contienen código ejecutable, como en el bloque try{}, el bloque begin{} y la función en sí. También se utilizan para expresar literales de tablas hash (como @{}).

Si el teclado tuviera algunos botones más, PowerShell no habría tenido que tener todos estos usos “incorporados” de caracteres de puntuación. Pero lo hace. En este punto, son casi una parte del "coste de entrada" del Shell, por lo que tendrá que acostumbrarse a ellos.


