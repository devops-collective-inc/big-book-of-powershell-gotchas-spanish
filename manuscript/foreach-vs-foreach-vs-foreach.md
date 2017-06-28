# ForEach vs ForEach vs ForEach
PowerShell tiene comandos de aspecto similar que pueden confundir, especialmente a los recién llegados. Por ejemplo, usted tiene dos entidades ForEach:

- El Cmdlet ForEach-Object, que tiene un alias ForEach (también tiene el alias %). Está destinado a funcionar en la canalización (pipeline), y utiliza un parámetro de proceso que acepta un ScriptBlock.

- La declaración ForEach. Tiene una sintaxis específica, no está destinado a ser utilizado en la canalización (pipeline) y no tiene un alias.

Aquí están los tres en acción, en un ejemplo muy simple:

![image013.png](images/image013.png)

La gran diferencia es que, en la canalización (pipeline), ForEach-Object procesa un objeto a la vez. _Esto significa que puede ser más lento,_ ya que ese ScriptBlock debe interpretarse en cada iteración. También tiende a usar menos memoria, ya que los objetos fluyen por la canalización (pipeline) uno a la vez y no tienen que ser agrupados en una variable primero.

La declaración ForEach tiende a ser más rápida, pero a menudo tiene más sobrecarga de memoria, ya que tiene que iterar sobre toda la colección de objetos a la vez, en lugar de transmitir objetos de uno en uno cada vez.

Ambos usan una sintaxis parecida, pero hay diferencias. Es importante entender que no son los mismos comandos, y que se ejecutan de manera diferente. Es confuso porque "ForEach" es tanto un alias como una declaración de Scripting. El Shell determina qué se está utilizando mirando el contexto en el que lo está utilizando.
