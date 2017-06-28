# ¿Dónde está el comando \<SuNombreAqui\>? He instalado la última versión de PowerShell y no puedo encontrarlo!

Una cosa difícil es entender que hay un cierto número de comandos que _vienen con PowerShell_ y otros que simplemente no vienen.

Cada nueva versión de PowerShell incluye al menos algunos nuevos comandos. Por ejemplo, Start-Job apareció por primera vez en PowerShell v2, mientras que Invoke-AdWorkflow fue introducido en PowerShell v3.

Lo que confunde a la gente es que una nueva versión de PowerShell también tiende a corresponder con una nueva versión del sistema operativo Windows. Y el Sistema Operativo viene con cientos de comandos. Por ejemplo, puede haber utilizado Get-SmbShare por primera vez en Windows Server 2012, que incluye PowerShell v3. Pero Get-SmbShare es parte del sistema operativo, no parte de PowerShell. Es decir, no tendrá Get-SmbShare en cada sistema que tenga PowerShell v3 o posterior, porque el comando no es una "característica de PowerShell ", es una "característica de Windows".

Así que… ¿De dónde se obtienen los comandos?

Normalmente, los comandos son parte de algún producto. ¿Necesita los comandos de Exchange Server? Instale las herramientas de administración de Exchange Server. ¿Necesita los comandos de Windows Server 2012? Instale el kit de herramientas de administración remota del servidor (RSAT), que contiene las herramientas de administración del servidor.
