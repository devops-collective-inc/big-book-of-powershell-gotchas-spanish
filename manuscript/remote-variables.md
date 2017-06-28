# Variables Remotas

Cuando utilice PowerShell Remoting, debe recordar que se trata de dos o más equipos que no comparten información entre ellos. Por ejemplo, el siguiente comando funcionará correctamente en su equipo local:

```
$f1 = 'D:\Scripts\folder1'
$f2 = 'D:\Scripts\folder2'
Copy-Item -Path $f1 -Recurse -Destination $f2 -Verbose -Force
```

Sin embargo, si intenta ejecutar el comando Copy-Item en un equipo remoto, se producirá un error:

```
 $f1 = "D:\Scripts\folder1"
 $f2 = "D:\Scripts\folder2"

 Invoke-Command -ComputerName MemberServer -ScriptBlock {Copy-Item -Path $f1 - Recurse -Destination $f2 -Verbose -Force}
 
 Cannot bind argument to parameter 'Path' because it is null.
 + CategoryInfo : InvalidData: [:] [Copy-Item], ParameterBindingValidationException
 + FullyQualifiedErrorId : ParameterArgumentValidationErrorNullNotAllowed,Microsoft.PowerShell.Commands.CopyItemCommand
 + PSComputerName : MemberServer

```

El problema es que $f1 y $f2 se definen en su equipo local, pero no en el equipo remoto. El bloque de secuencia de comandos enviado a Invoke-Command no se evalúa en su computadora, simplemente se pasa como está (as-is).

Hay dos posibles soluciones. La primera es simplemente incluir las definiciones de variables en el bloque de secuencia de comandos:

```
 Invoke-Command -ComputerName MemberServer -ScriptBlock {
 $f1 = "D:\Scripts\folder1"
 $f2 = "D:\Scripts\folder2"
 Copy-Item -Path $f1 -Recurse -Destination $f2 -Verbose -Force
 }
 ```
 
Otra técnica, disponible en PowerShell v3 y posterior, es utilizar el designador de variable $using. PowerShell pre-escanea el bloque de secuencia de comandos y pasará los valores de la(s) variable(s) local(es) al (los) equipo(s) remoto(s).

```
 $f1 = "D:\Scripts\folder1"
 $f2 = "D:\Scripts\folder2"
 
 Invoke-Command -ComputerName MemberServer -ScriptBlock {
 Copy-Item -Path $using:f1 -Recurse -Destination $using:f2 -Verbose -Force}
```

El uso de la sintaxis especial $using: es lo que hace que esta versión del comando funcione.
 
