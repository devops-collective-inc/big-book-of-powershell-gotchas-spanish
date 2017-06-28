# Una página HTML a la vez, por favor
Esto me vuelve loco:

![image037.png](images/image037.png)

Lo que está pasando es que alguien ejecutó dos comandos, canalizando la salida de cada uno a ConvertTo-HTML, y esencialmente combinando ambas páginas HTML en un solo archivo. Lo que me realmente me vuelve loco es que Internet Explorer está bien con esa tontería.

Los archivos HTML pueden empezar con una etiqueta de nivel superior, pero si se echa un vistazo a ese archivo verá que contiene dos:

![image039.png](images/image039.png)

He resaltado las líneas que terminan una página HTML y comienzan la siguiente. Esto es técnicamente un archivo HTML malformado. Algunos navegadores Web lo admiten (unos si, otros no), difícil de analizar si alguna vez necesita para manipular el contenido mediante programación, y ... bueno, es esta mal. Es como el incesto o algo así. Inaceptable.

Si necesita combinar varios elementos en un único archivo HTML, utilice el parámetro -Fragment de ConvertTo-HTML. Produzca sólo una parte del HTML o varias porciones de ese tipo y luego combínelas en una sola página completa. Ahhh bien. Todo el proceso al respecto de la creación de informes HTML en PowerShell lo encuentra en nuestro otro libro electrónico gratuito que viene con este.
