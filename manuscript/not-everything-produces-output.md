# No todo produce una salida
Veo esto a menudo:

![image031.png](images/image031.png)

Si esperaba algo en la pantalla en términos de salida, estará decepcionado. El truco aquí es hacer un seguimiento de lo que cada comando produce como salida, y es allí donde hay un posible punto de confusión.

En el mundo de PowerShell, la salida es lo que aparecería en la pantalla si ejecutamos el comando y no lo canalizamos (enviar al pipeline) a nada más. Sí, Export-CSV hace algo - crea un archivo en disco - pero en el mundo de PowerShell ese archivo no se ve en pantalla. Export-CSV no produce ninguna salida, hablando de algo que aparecería en la pantalla. Por ejemplo:

![image033.png](images/image033.png)

¿Lo ve? nada. Ya que no hay nada en la pantalla, no hay nada en la canalización (pipeline). No puede canalizar Export-CSV a otro comando, porque no hay nada que canalizar.

Algunos comandos pueden incluir un parámetro -PassThru. Cuando lo tienen y se utiliza, harán lo que hagan normalmente, pero también pasarán sus objetos de entrada a través de la canalización (pipeline), para que luego se puedan canalizar a otra cosa. Export-CSV no es uno de esos comandos, - nunca produce una salida, por lo que nunca tendrá sentido para canalizarlo a otra cosa.


