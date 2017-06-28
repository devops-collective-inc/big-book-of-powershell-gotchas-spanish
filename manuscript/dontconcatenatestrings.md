# No+Concatene+Strings
Realmente me disgusta la concatenación de cadenas. Es como obligar a alguien a acurrucarse con alguien que ni siquiera conocen. Grosero.

![image043.png](images/image043.png)

Y completamente innecesario, cuando se utilizan comillas dobles.

![image045.png](images/image045.png)

Mismo efecto al final. Usando comillas dobles, PowerShell buscará el carácter $. Cuando lo encuentre:

1. Si el siguiente carácter es { entonces PowerShell llevará todo a la concordancia } como un nombre de variable, y reemplazará todo con el contenido de esa variable. Por ejemplo, poner $ {mi variable} dentro de comillas dobles reemplazará con el contenido de $ {mi variable}.
2. Si el siguiente carácter es un ( entonces PowerShell llevará todo a la coincidencia ) y lo ejecutara como si fuera código. Por lo que, ejecuté $wmi.serialnumber para acceder a la propiedad serialnumber del objeto que se encontraba en la variable $wmi.
3. De lo contrario, PowerShell tomará todos los caracteres que sean legales para un nombre de variable, hasta el primer carácter de nombre de variable ilegal, y lo reemplazará con esa variable. Así es como funciona $computer en mi ejemplo. El espacio después de la r no es legal para un nombre de variable, por lo que PowerShell sabe que el nombre de la variable se detiene en r.

Una cosa para resaltar aquí:

![image047.png](images/image047.png)

Esto no funcionará como se esperaba. En la mayoría de los casos, $wmi será reemplazado por un nombre de tipo de objeto y .serialnumber seguirá allí. Eso ocurre porque . no es un nombre de variable legal, por lo que PowerShell deja de “observar” la variable con la letra i. Entonces, reemplaza $wmi con su contenido. Usted vio en el ejemplo anterior, el uso de $($wmi.serialnumber), que es una subexpresión y funciona. Los paréntesis hacen que su contenido se ejecute como código..
