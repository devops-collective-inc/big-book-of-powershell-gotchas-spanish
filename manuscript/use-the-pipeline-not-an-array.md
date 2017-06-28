# Utilizar la canalización (pipeline), no una matriz
Un error muy común cometido por programadores tradicionales que recién llegan a PowerShell:

![image057.png](images/image057.png)

Esta persona ha creado una matriz vacía en $output, y mientras recorre la lista de ordenadores y ejecuta consultas WMI, están agregando nuevos objetos de salida al contenido de la matriz. Finalmente, envía la matriz a la canalización (pipeline).

Mala práctica. Como se ve, esto obliga a PowerShell a esperar mientras se completa la ejecución del comando. Cualquier comando subsecuente en la canalización (pipeline) se sentará a esperar con los brazos cruzados. ¿Un mejor enfoque? Utilizar la canalización (pipeline), cuyo propósito es acumular la salida por usted - sin necesidad de que usted mismo la acumule en una matriz.

![image059.png](images/image059.png)

Ahora, los comandos posteriores recibirán la salida, dejando que varios de esos comandos se ejecuten más o menos simultáneamente en la canalización (pipeline).
