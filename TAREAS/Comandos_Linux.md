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

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/9157fa25-6d07-42f2-876d-dd1dfa87fe2a)

- Para enumerar los archivos en el directorio de trabajo, usamos el ls comando.

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/affd64ca-2117-4cc5-9367-c874697f2f7b)

### cd

- probemos esto:

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/68e128e5-a8f8-4650-b98a-283d286389db)

- El "." La notación se refiere al directorio de trabajo en sí y la notación ".." se refiere al directorio principal del directorio de trabajo. Así es como funciona. Cambiemos nuevamente el directorio de trabajo a /usr/bin:


![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/14ff31c0-fc35-413d-96ab-b17565580613)


- Bien, ahora digamos que queremos cambiar el directorio de trabajo a /usr/bincuyo padre es /usr. Podríamos hacerlo de dos maneras diferentes. Primero, con una ruta absoluta:


![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/316a2a44-d053-437b-8b18-31e3a470ef28)


- O, con una ruta de acceso relativa:


![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/369f55f3-6105-48ab-9f4b-d614c556e43e)


- Asimismo, podemos cambiar el directorio de trabajo de /usra /usr/binde dos formas diferentes. Primero usando una ruta de acceso absoluta, o con una ruta de acceso relativa:


![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/0f0a0821-5551-4a25-a973-e83f3a700cc8)


- Ahora bien, hay algo importante que debemos señalar aquí. En la mayoría de los casos, podemos omitir el "./". Esta implicado. Mecanografía:

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/70a94a38-4ede-4be8-aaa1-69139146ec3f)


## Looking Around


## A Guided Tour
## Manipulation Files
## Working with Commands
## I/O Redirection
## Expansion
## Permissions
## Job Control
