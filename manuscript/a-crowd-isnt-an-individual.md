# Una multitud no es un individuo

Un error muy común de novato:

![image067.png](images/image067.png)

Aquí, el problema es que se está tratando todo como si estuviera compuesto de un sólo un valor. Pero aqupi $computername puede contener varios nombres de equipo (eso es lo que significa  ([string[]]), lo que significa que tanto $bios como $os podrían contener también varios elementos. El truco está en enumerar $computername para conseguir el resultado deseado:

![image069.png](images/image069.png)

Algunas veces también se encontrará con esto, incluso en situaciones sencillas. Por ejemplo:

![image071.png](images/image071.png)

PowerShell v2 no reaccionará tan bien, pero en PowerShell v3, la variable dentro de comillas dobles $procs es una variable que contiene varios objetos. PowerShell los enumera implícitamente, además de buscar una propiedad llamada name. Fíjese en ".name" al final de la cadena - PowerShell no hizo nada con eso.

Es probable que mejor desee enumerar así:

![image073.png](images/image073.png)
