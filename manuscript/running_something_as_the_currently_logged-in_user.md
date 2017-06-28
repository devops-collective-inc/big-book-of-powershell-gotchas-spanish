# Ejecutando algo como el "usuario actualmente conectado"
Una solicitud de PowerShell común es poder iniciar de forma remota algún código que se ejecuta bajo la cuenta del usuario que está conectado actualmente a una máquina remota o el usuario que más a menudo utiliza la máquina remota.

Esto es realmente difícil, y generalmente impráctico.

Primero, entender que Windows es inherentemente un sistema operativo multiusuario. No tiene un concepto para "el usuario actualmente conectado" porque puede haber muchos usuarios conectados. Aunque las versiones cliente de Windows no permiten técnicamente múltiples inicios de sesión interactivos, el sistema operativo base actúa como si pudiera.

Segundo, como un sistema operativo multiusuario, el trabajo de Windows es mantener un estricto aislamiento alrededor del espacio de proceso de cada usuario. Usted no quiere que un usuario salte en el espacio de trabajo a otro, porque eso sería un gran riesgo para la seguridad y la estabilidad. Es por esto que no puede iniciar sesión como un usuario y ejecutar algo que otro usuario puede "ver".

Por ejemplo, una versión común de esta solicitud es para que un administrador de manera remota abra el Bloc de Notas como una ventana (pop up) en frente de los usuarios, para presentar de forma remota mensajes importantes. Por desgracia, el Bloc de Notas no es una buena aplicación de mensajería instantánea y Windows no hace que esto sea fácil. Si lo piensa con más detalle, ¿se imagina que podría hacer el malware si esto fuera posible? Sería horrible!

Con muy pocas excepciones, realmente no se puede ejecutar algo "como otro usuario en una máquina remota". Una excepción es si conoce el nombre de usuario y la contraseña del usuario remoto. Si lo conoce, puede iniciar una sesión de acceso remoto en la computadora mediante sus credenciales y, potencialmente, ejecutar aplicaciones en el espacio de proceso de ese usuario. Aunque eso es muy poco práctico en la mayoría de situaciones.

