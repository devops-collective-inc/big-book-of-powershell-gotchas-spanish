# Formato a la derecha

Todo el mundo se encuentra con esto. Comienza escribiendo un comando verdaderamente impresionante.

![image005.png](images/image005.png)

Y luego piensa, "Wow, esto quedaría muy bien en un archivo HTML."

![image007.png](images/image007.png)

¿¡¿¡¿Un momento QUÉ?!?!?

Sucede todo el tiempo. Si desea una manera fácil de recordar lo que no se debe hacer, es esto: nunca canalice (enviar al pipeline) la salida de un comando de formato. Esa no es toda la verdad (llegaremos a toda la verdad en un momento), pero si sólo quiere una respuesta rápida, eso es todo. En la comunidad, lo llamamos la regla del "formato a la derecha", porque tiene que ver con mover su comando Format al extremo derecho de la línea de comandos. Es decir, el comando Format va  al final, y nada más viene después de él.

La razón es que todos los comandos de formato producen códigos de salida internos especiales, que están destinados a generar una visualización en pantalla. Canalizar esos códigos (enviarlos al pipeline) a cualquier otro comando - ConvertTo-HTML, Export-CSV, lo que sea – solo hará que se obtenga una salida ilegible.

De hecho, hay algunos comandos que pueden venir después de un comando de formato en la canalización (pipeline):

1. Out-Default. Técnicamente siempre está al final de la canalización (pipeline), aunque sea “invisible”. Es el encargado de redirigir la salida al Host. Por eso es que vemos siempre la salida en pantalla.
2. Out-Host también entiende la salida de los comandos de formato, porque Out-Host es la forma en la que los códigos de formato obtienen la información de lo que se debe mostrar en pantalla.
3. Out-Printer también entiende los códigos de formato de salida y además, construye una página impresa que se vería exactamente como la salida normal en pantalla.
4. Out-File, como Out-Printer, redirecciona la salida en pantalla, pero esta vez a un archivo de texto en disco.
5. Out-String utiliza los códigos de formato de salida y produce una cadena simple que contiene el texto que de otro modo habría aparecido en pantalla.

Aparte de esas excepciones -y de ellas, usualmente sólo se utiliza Out-File- no se puede canalizar la salida de un comando Format a otro comando si desea obtener cualquier cosa que parezca útil.
