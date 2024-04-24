# Learning the Shell: https://linuxcommand.org/lc3_learning_the_shell.php 

## Contenido:

## What is "the Shell?

El "shell" es un programa que actúa como interfaz entre el usuario y el sistema operativo, permitiendo la ejecución de comandos y la interacción con el sistema. Por otro lado, la "terminal" es un programa llamado emulador de terminal que proporciona una ventana de texto donde los usuarios pueden interactuar con el shell, ejecutar comandos y realizar tareas en el sistema operativo a través de la línea de comandos. Ambos conceptos son fundamentales para la interacción con sistemas Unix y Linux a través de la línea de comandos.

### Probando el teclado
- ¡Excelente! Ahora escribe algunos caracteres sin sentido y presiona la tecla Intro.

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/51139afc-6085-4e51-bc31-b2765b80fba6)

- Si todo salió bien, deberíamos haber recibido un mensaje de error quejándonos de que no puede entender el comando:

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/f2f6cc86-2c80-4fa8-b2a2-a58e9357007b)

- Cuando presionamos la flecha hacia arriba:

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/c00c8ce3-a027-49ed-af4c-38a0c423c18f)

- Cuando presionamos la flecha hacia abajo:

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/691708a1-e080-4e33-8fe7-4720058cbc49)

#### No estás operando como root, ¿verdad?

No estamos operando como root, ya que sí contamos con el carácter de $ en la consola.

### Usando el mouse

Además de usar el mouse para desplazar el contenido de la ventana del terminal, podemos usarlo para copiar texto. Arrastre el mouse sobre algún texto (por ejemplo, "kdkjflajfks" aquí mismo en la ventana del navegador) mientras mantiene presionado el botón izquierdo. El texto debe resaltar. Suelte el botón izquierdo, mueva el puntero del mouse a la ventana de terminal y presione el botón central del mouse (alternativamente, presione los botones izquierdo y derecho al mismo tiempo cuando trabaje en un panel táctil). El texto que resaltamos en la ventana del navegador debe copiarse en la línea de comando.

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/e3389b5c-432d-46c4-bb74-64871dcdc6e7)

## Navigation

El contenido es una introducción a los conceptos básicos de la navegación en sistemas Linux a través de la línea de comandos. Se centra en la organización del sistema de archivos en Linux, que se basa en una estructura jerárquica de directorios, similar a la estructura de carpetas en Windows, donde se mencionan tres comandos fundamentales para la navegación en la línea de comandos: `pwd` (print working directory) para imprimir el directorio de trabajo actual, `cd` (change directory) para cambiar de directorio y `ls` para listar los archivos y directorios en el directorio actual. Además, se explica la diferencia entre la organización del sistema de archivos en Linux y Windows, destacando que Linux no utiliza letras de unidad y tiene un único árbol de directorios. Se utiliza la metáfora de un laberinto para representar el sistema de archivos, donde estamos ubicados en un directorio y podemos ver sus archivos y subdirectorios, así como la ruta hacia el directorio principal y los subdirectorios.

- Colocar el comando pwd:

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/a94a3e9e-0129-425e-b05d-b8e0f2804566)

- Para enumerar los archivos en el directorio de trabajo, usamos el ls comando.

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/4f33c949-33e4-40fe-a0e1-6e7a41419e99)

Cuando colocamos el comando ls, no os enúmera el directorio, y eso puede deberse a una vinculación no correccta por parte del dispositivo.

### cd

- probemos esto:

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/b266132f-5c4c-457d-81d9-f8c4b5c0fe36)

Una de haber ejecutado los comandos, nos sale  que "El fichero o directorio no existe", entonces al no exstir no nos muestra ninngun valor o información. 

- El "." La notación se refiere al directorio de trabajo en sí y la notación ".." se refiere al directorio principal del directorio de trabajo. Así es como funciona. Cambiemos nuevamente el directorio de trabajo a /usr/bin:

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/39709352-ff4d-4b13-851a-7b695738ba7d)

Al no existir ningún tipo de direcctorio no nos proporciona el directorio, donde no podemos guardarlo.

- Bien, ahora digamos que queremos cambiar el directorio de trabajo a /usr/bincuyo padre es /usr. Podríamos hacerlo de dos maneras diferentes. Primero, con una ruta absoluta:

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/6f102314-f243-4530-8ade-51b9a9c9cf10)

Seguimos mantiendo el msmo problema.

- O, con una ruta de acceso relativa:

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/05237df4-5fff-4529-a30b-d373273011dc)

Considerando los resultados correspondientes, puedo decir que el programa esta presentando problemas ya que nos indica que el comando cd.. no funciona lo cual no deberia ser asi.

- Asimismo, podemos cambiar el directorio de trabajo de /usra /usr/binde dos formas diferentes. Primero usando una ruta de acceso absoluta, o con una ruta de acceso relativa:

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/0c2f584e-1542-4965-85a6-9709c1e9c14d)

Al no presentar un directorio existente podemos obtener resultados concisos.

- Ahora bien, hay algo importante que debemos señalar aquí. En la mayoría de los casos, podemos omitir el "./". Esta implicado. Mecanografía:

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/42cb4eef-dea3-4d64-bbcb-0a3e36e63aa7)

## Looking Around
## A Guided Tour
## Manipulation Files
## Working with Commands
## I/O Redirection
## Expansion
## Permissions
## Job Control
