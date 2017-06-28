# Comandos que necesitan un perfil de usuario pueden fallar cuando se ejecuta de forma remota

Muchos comandos actúan utilizando el perfil del usuario que ha iniciado sesión actualmente. Estos comandos a veces pueden fallar cuando los ejecuta a través de una conexión remota, como con Invoke-Command o Enter-PSSession. Por ejemplo, muchos instaladores predeterminan la creación de iconos por usuario y pueden fallar cuando se ejecutan remotamente, incluso cuando se ejecutan en un modo de "instalación silenciosa".

El problema es que, cuando se conecta a un equipo remoto, no está generando un entorno de usuario completo. Técnicamente no está "conectándose" a la máquina en el sentido usual. Se está autenticando, sí, pero de la misma manera que si se autenticara a una carpeta compartida. Su conexión remota no tiene un perfil de usuario completo, por lo que cualquier cosa que se espere puede obtener errores y fallar (incluso si no muestran esos errores).

No hay solución fácil para esto, por desgracia.
