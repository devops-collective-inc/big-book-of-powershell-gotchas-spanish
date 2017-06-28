# Backtick, Grave Accent, Escape

A menudo va a encontrarse con esto

![image061.png](images/image061.png)

No, no es un píxel muerto en el monitor o un trozo de tóner perdido en la página, es la marca de acento grave o backtick. \` Es el carácter de escape de PowerShell. En este ejemplo, está "escapando" el retorno de carro invisible al final de la línea, eliminando su propósito especial como final de línea lógica, simplemente haciendo que sea un retorno de carro literal.

No me gusta el backtick utilizado de esta manera.

Primero, es difícil de ver. Segundo, si se deja un espacio en blanco extra después de él, ya no estará escapando el retorno de carro, y el script se romperá:

![image063.png](images/image063.png)

Observe cuidadosamente el parámetro -computername - en este segundo ejemplo. Fíjese como se muestra un  color incorrecto para un nombre de parámetro. Ocurre porque he añadido un espacio después del backtick en la línea anterior. IMPOSIBLE de rastrear.

Y el backtick es innecesario como carácter de continuación de línea. Permítanme explicar por qué:

PowerShell ya le permite agregar un “Enter” en ciertas situaciones. Usted solo tiene que aprender cuáles son esas situaciones, y luego tomar ventaja de ellas. Entiendo totalmente el deseo de tener código perfectamente formateado - predico sobre eso todo el tiempo - pero no tiene que confiar en un personaje como el backtick para obtener código bien formateado.

Sólo tiene que ser más listo.

![image065.png](images/image065.png)

Para empezar, he puesto mis comandos Get-WmiObject en una tabla hash, por lo que ahora puedo dar un formato agradable y bonito. Cada línea termina en un punto y coma, y PowerShell me permite romper la línea después de cada punto y coma. Incluso si agrego un espacio adicional o un Tab después del punto y coma, funcionará bien. Entonces hago “Splat” de esos parámetros al comando Get-WmiObject.

Después de Get-WmiObject, tengo un carácter Pipe, y PowerShell admite un “Enter” luego de un carácter Pipe.

Usted notará al final de Select-Object que se puede utilizar una coma también.

Así termino con un formato que parece al menos tan bueno, si no mejor, porque no tiene un backtick \` flotando por todas partes.

