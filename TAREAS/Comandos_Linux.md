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
La idea de explorar el sistema Linux mediante la navegación por sus directorios, es utilizando comandos básicos de la línea de comandos como `ls`, `less` y `file`. Donde nos invita al lector a familiarizarse con estas herramientas antes de embarcarse en la exploración del sistema. `ls` se utiliza para listar los archivos y directorios en el directorio actual, `less` permite ver el contenido de archivos de texto de manera paginada y `file` se emplea para clasificar el contenido de un archivo en función de su tipo. En resumen, ejercicio prepara al lector para comenzar a explorar el sistema Linux utilizando estos comandos básicos, lo que le permitirá aprender más sobre la estructura y el contenido del sistema operativo a medida que avanza en su viaje.

### es
El ls comando se utiliza para enumerar el contenido de un directorio. Probablemente sea el comando de Linux más utilizado. Se puede utilizar de varias maneras diferentes. Aquí hay unos ejemplos:

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/9b1f777f-6893-496c-8d98-1b67f994d3f6)

### Ejemplos de comandos ls 

- **ls -a**

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/17a665a3-b273-49a2-a7c9-115d3f47b778)

- **ls -l**

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/4307a05d-185e-48c0-8492-39859beb51a7)

- **ls /bin**

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/25ab283c-7b25-48dd-8c68-35a44dce28da)

- **ls -l /etc /bin**

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/8c5c9109-541e-4f95-b284-2dc342d047cb)

- directorio **bin**: hay un total de 92184 archivos
- directorio **etc**:  hay un total de 116 archivos.

  ![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/a1cd03b5-0ff2-4c7f-a569-893b37b974b2)

### Una mirada más cercana al formato largo
- Nombre del archivo: ADVANCE 197121
- Hora de modificación: Nov 20 18:32
- Tamaño: No lo muestra.
- Grupo: No lo muestra
- Dueño: en este caso no lo evidencia.
- Permisos de archivos: tampoco se evidencia.

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/db0a7f46-72bf-4005-b134-5543b89c3741)

### menos
less es un programa que nos permite visualizar archivos de texto. Esto es muy útil ya que muchos de los archivos utilizados para controlar y configurar Linux son legibles por humanos.

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/7fa8f657-0f91-4065-8b26-e246fd33dedc)

### archivo
Mientras deambulamos por nuestro sistema Linux, resulta útil determinar qué tipo de datos contiene un archivo antes de intentar verlo. Aquí es donde fileentra en juego el comando. file Examinará un archivo y nos dirá qué tipo de archivo es.

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/a79fc66a-2753-4a66-be3c-75709523882d)

## A Guided Tour
El texto sugiere hacer un recorrido por diferentes directorios del sistema Linux para explorar su contenido. Para cada directorio mencionado, se recomienda realizar las siguientes acciones:

1. Utilizar el comando `cd` para cambiar al directorio mencionado.
2. Emplear el comando `ls` para listar el contenido del directorio y así explorar qué archivos y subdirectorios contiene.
3. En caso de encontrar archivos interesantes, utilizar el comando `file` para determinar su contenido y tipo.
4. Si los archivos son de texto, se sugiere utilizar el comando `less` para ver su contenido de manera paginada.

- **/**

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/910b7df1-4d5b-4439-a767-a4a74e37d735)

- **/boot**


![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/ab8aca21-fcb0-4524-9f06-d7b179e943f5)


- **/etc**

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/64c9b573-529d-4fa6-bc1e-26b811054b6c)

- **/bin, /usr/bin**

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/4831dd37-a9cf-41f0-a3bd-fa9d8673c1a4)

- **/sbin, /usr/sbin**
  
![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/42e9831b-bb40-422c-a1d9-4e995581884c)

- **/usr**

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/9df2dd0c-c339-4a91-9d53-d0f7470224c9)

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/0258cce3-4d96-49ff-93d1-20fbac8d0b97)

- **/usr/local**

  ![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/b14221fd-2d18-44be-92f4-73346cae869b)
![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/c38c8d04-1361-46cd-b6b6-c211ab1115d1)

- **/var**

 ![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/0fca6915-d341-4663-836d-ba389dc0f837)
![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/477028f8-f755-4e4f-ba5a-04712286e067)

## Manipulation Files
El texto presenta cuatro comandos básicos en Linux: `cp`, `mv`, `rm` y `mkdir`, utilizados para copiar, mover, eliminar y crear archivos y directorios. Aunque las tareas simples pueden ser más fáciles con un administrador de archivos gráfico, estos comandos ofrecen poder y flexibilidad para realizar tareas más complejas de manera eficiente en la línea de comandos.

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/b0ec645c-38e9-4c61-a521-8c1cb81da1d8)

### CP

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/e84fc75c-1621-4196-a3fd-5087f84a323a)

- También se puede utilizar para copiar varios archivos (y/o directorios) a un directorio diferente:
  
![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/f2bf224e-3a61-475d-81e2-a9c148f6f0f4)

### mv

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/434c647f-dc39-4c69-8431-85fc60a33dc1)

- Para mover archivos (y/o directorios) a un directorio diferente:

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/e685dd02-03c6-4690-b3c5-eeca66249b25)

### habitación

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/1cf7bd26-c618-45a3-80a5-932209b893b6)

### mkdir
![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/72bd0a58-aff4-4a65-b52a-f10fe9b15358)

## Working with Commands

El texto introduce cuatro comandos relacionados con la identificación y la información sobre otros comandos en Linux: `type`, `which`, `help` y `man`. Estos comandos ayudan a determinar el tipo de comando que se está utilizando, ya sea un programa ejecutable, un comando interno del shell, una función de shell o un alias. Esto es útil para comprender mejor cómo funcionan los comandos y cómo se pueden utilizar en diferentes contextos en el sistema operativo Linux.
### type

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/87b3d7e1-faf7-4f89-af33-bdced5b80b70)

### wich

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/cea67045-b043-4690-a72c-3a6a01c03d6d)

### Ayuda

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/f94c03ca-ae31-4f8d-bb1f-59af5b2ccae2)

### --ayuda

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/2ae15f37-6f03-45d3-acef-a5dc89be8ad4)

### hombre

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/73b737f8-e613-4409-a147-6ee7b8bbc26f)

## I/O Redirection

Se explica el concepto de redirección de entrada/salida en la línea de comandos, una característica poderosa que permite cambiar dónde se envía la salida de un comando. Se menciona que la mayoría de los programas de línea de comandos envían su salida al estándar de salida por defecto, que por lo general se muestra en la pantalla. Sin embargo, esto puede ser modificado usando la notación especial ">" para redirigir la salida a un archivo en lugar de mostrarla en la pantalla. Esto proporciona flexibilidad al usuario para manejar y almacenar la salida de los comandos de acuerdo a sus necesidades.

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/8bfa3299-a199-429f-9813-3c6124f3e3c5)

- Cada vez que se repite el comando anterior, file_list.txtse sobrescribe desde el principio con la salida del comando ls. Para agregar los nuevos resultados al archivo, usamos ">>" así:

 ![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/96b38fb8-6ea4-4fca-9e63-2e0167b99a6c)
 
### Entrada estándar
![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/150eb5ad-f34d-4185-86c3-65738c5073e1)
![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/aa89d686-edcd-4e98-9864-fd63b01c180a)

### Tuberias
- **ls -l | less**
![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/8a74000f-4919-464e-8625-34e34c52bfa4)

## Expansion
## Permissions
## Job Control
