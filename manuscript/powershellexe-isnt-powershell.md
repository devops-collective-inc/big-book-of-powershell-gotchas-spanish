# PowerShell.exe no es PowerShell

Es importante entender que Windows PowerShell, detrás de escenas es en realidad un motor. Usted como un simple ser humano no puede interactuar directamente con PowerShell.

En su lugar, necesita una aplicación Host. Un Host incrusta el motor internamente, y luego le da una manera de interactuar con él. Por ejemplo, powershell.exe es una aplicación Host. Se construye alrededor de la misma consola de consola de Windows (conhost.exe) a través de la antigua shell de línea de comandos cmd.exe, pero incrustando el motor PowerShell. Se escriben los comandos y el Host los envía al motor para su ejecución. El Host también es responsable de mostrar cualquier resultado. En este caso, en pantalla.

¿Por qué es importante esta distinción?

Porque diferentes Hosts pueden comportarse de diferentes maneras. Por ejemplo, el PowerShell ISE se comporta un poco diferente que el Host de la consola, y ambos se comportan de manera muy diferente de Active Directory Administration Center, otro host de PowerShell.
