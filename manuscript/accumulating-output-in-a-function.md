# Acumulando la salida en una función


Esto es un truco un poco "avanzado", pero es uno en que muchos desarrolladores experimentados caen. Aquí hay un ejemplo, sólo para demostrar el punto (no es funcional, ya que el comando utilizado es ficticio):

![image009.png](images/image009.png)

El problema es que la función puede generar múltiples objetos de salida, y el programador está acumulándolos en la variable de $output. Esto significa que esta función no emitirá nada hasta que su ejecución esté completamente terminada. No es así como los comandos PowerShell (y las funciones) suelen estar diseñados para funcionar.

Los comandos de PowerShell _normalmente_ deben enviar cada objeto a la canalización (pipeline), uno a la vez, apenas esos objetos estén listos. Esto permite que la canalización (pipeline) acumule la salida, e inmediatamente la pase a lo largo de la siguiente función o comando en la canalización (pipeline). Así funcionan los comandos en PowerShell. Ahora, siempre hay excepciones. Sort-Object, por ejemplo, _tiene_ que acumular su salida, porque en realidad no puede ordenar nada hasta que tenga _todos_ los elementos. Es por esto que se le llama un comando _blocking, porque "bloquea" la canalización (pipeline) completamente hasta que se produce su salida. Pero eso es una excepción.

Normalmente esto es muy fácil de solucionar, simplemente enviando a la canalización (pipeline) directamente en lugar de acumular:

![image011.png](images/image011.png)
