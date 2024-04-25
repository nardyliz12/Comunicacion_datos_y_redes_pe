# Learning the Shell: https://linuxcommand.org/lc3_learning_the_shell.php 

## Contenido:

## I. What is "the Shell?

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

## II. Navigation

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


## III. Looking Around
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

## IV. A Guided Tour
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

## V. Working with Commands

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

## VI. Expansion
Aqui explica el proceso de expansión que realiza el shell antes de ejecutar un comando. Cuando escribimos una línea de comando y presionamos Enter, el shell lleva a cabo la expansión de ciertos caracteres o secuencias de caracteres antes de procesar el comando. Se menciona que caracteres simples como "*" pueden tener significados especiales para el shell durante este proceso de expansión. Luego, se ilustra este concepto usando el comando "echo", que imprime sus argumentos de texto en la salida estándar.

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/ed6d1292-ac07-4903-a862-c7007bf07ea9)

- Eso es bastante sencillo. Cualquier argumento pasado a echose muestra. Probemos con otro ejemplo:

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/c61327a9-d4fe-476d-9ea7-ab4afc304996)

### Expansión de nombre de ruta

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/a9f0adca-1980-4217-98dc-07379d76dc26)

- podríamos realizar las siguientes ampliaciones:

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/88b5dd60-803b-4ba6-9c15-43d0c775c530)

- Y:

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/c0d70f0c-a3b0-4845-b0b3-8e4e27648ca3)

- o incluso:
  
![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/61cdf470-ac12-4cbc-b81f-0e51b64c654b)

- y mirando más allá de nuestro directorio de inicio:
  
 ![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/b209e01f-9a59-4684-835c-9e419a1d8008)

### Expansión de tilde

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/7df756b9-a49d-420b-b62a-58120002084a)

- Si el usuario "foo" tiene una cuenta, entonces:
  
![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/baa16fc7-d8d0-4e05-9c2b-a6a143ce4683)

### Expansión aritmética

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/847b524c-d67d-411f-a3cd-530b6066dbb8)

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/5190c9e4-3195-4154-bf00-8e11b9a74bdd)

- Otra forma:

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/f82f117a-ca8d-4fec-bd8f-5a946915555e)

- A continuación se muestra un ejemplo que utiliza los operadores de división y resto. Observe el efecto de la división de números enteros:

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/3fe65a32-c4d4-4e8e-9cf6-e9e666188806)

### Expansión de llaves

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/f4c2ab27-7fd1-4cf5-9ef7-2a289f0ac984)

- A continuación se muestra un ejemplo que utiliza un rango de números enteros:

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/cd0380eb-72b7-46a7-b201-e44f747bcb51)

- Una serie de letras en orden inverso:

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/7c01a145-4597-49bc-a212-50846550e63e)

- Las expansiones de llaves pueden estar anidadas:

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/b09b811c-c777-4bc2-b5fa-bba9294d1bfd)

- En lugar de eso, podríamos hacer esto:

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/bb57e885-5f35-43b9-b062-79bfcdf425f1)

### Expansión de parámetros

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/8ecc812f-98db-460c-9355-7e6e9808d385)

- Para ver una lista de variables disponibles, intente esto:
- **printenv | less**
  
![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/3b85fd2b-52a0-4cd0-bf24-b689359aaffa)

- Con la expansión de parámetros, si escribimos mal el nombre de una variable, la expansión seguirá teniendo lugar, pero dará como resultado una cadena vacía:

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/88f3b851-8ad9-4125-9b8e-a9be57fb5cb6)

No muestra ningún resultado.

### Sustitución de comando

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/1e1aa1fa-29b1-4c7d-bc5b-9ff13e3ce62a)

- Uno inteligente dice algo como esto:

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/1a3bb2bc-a93a-4c8c-b841-d9195a20e212)

- Se pueden utilizar tuberías enteras (solo se muestra una salida parcial):

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/5a7758fb-c8a6-4fbb-8f8e-64bea3784a99)

- Utiliza comillas invertidas en lugar del signo de dólar y paréntesis:

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/f63163fa-bce1-4a91-8a67-8c524cef8239)

### Citando

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/8abf0428-1e4a-419e-b498-958ab6fe0d9c)

- o:

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/9edf58b6-633e-4cde-aeef-6ce6fcee3dec)

### Doble comillas

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/8b892df0-c464-4592-97f8-fa033726c393)

- Al utilizar comillas dobles, podemos detener la división de palabras y obtener el resultado deseado; Además, incluso podemos reparar el daño:

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/fce86d57-e610-480b-b05e-bb36a775def4)

- Recuerde, la expansión de parámetros, la expansión aritmética y la sustitución de comandos todavía se realizan entre comillas dobles:

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/db16b8af-cdb0-4ffc-9457-0719eef4f38c)

- En nuestro ejemplo anterior, vimos cómo la división de palabras parece eliminar espacios adicionales en nuestro texto:

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/fd24dfa2-9992-423c-9985-5d8a9551a876)

-  Si agregamos comillas dobles:

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/5a6ceb51-e374-4674-9e81-588bd8234e2f)

- Considera lo siguiente:

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/3e7339b6-c76a-4e2d-b8a9-a75257d78ab5)

### Comillas simples

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/a42b7a06-9c21-459b-9bb3-c14f1fa90453)

### Personajes que escapan

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/2914b4af-f722-4bb6-8060-695bc6495738)

- Para incluir un carácter especial en un nombre de archivo podemos hacer esto:

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/c5d2a31a-049a-44ab-98e3-0e1ccfdd1c79)

### Más trucos de barra invertida

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/6e50e983-f376-4fef-b181-e7ed747bbb50)

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/283483e8-8f7b-44d2-b179-2b27c0571e2b)

- Usar el echocomando con la opción -e nos permitirá demostrar:

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/2225cd73-977f-4c70-93dc-44598948dd8e)

## VII. Permissions

Explica que los sistemas tipo Unix, como Linux, permiten la operación simultánea de múltiples usuarios. Esto se originó en entornos donde las computadoras eran centrales y compartidas por muchos usuarios. Para evitar conflictos, se implementaron comandos como chmod, su, sudo, chown y chgrp, que permiten controlar los permisos de acceso a archivos y la administración de usuarios y grupos.

### Permisos de archivos

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/278e6da8-8c9b-4238-8cb3-79d6bc889130)

### chmod

- Por ejemplo, si quisiéramos configurar some_filepermisos de lectura y escritura para el propietario, pero quisiéramos mantener el archivo privado de otros, haríamos lo siguiente:

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/cf0510b9-8c3c-4182-8acd-26d24d749ece)

### Convertirse en superusuario por un corto tiempo

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/85aad13f-754d-4fea-a652-76e31d0b1e99)

- Después de ingresar el comando, se le solicita al usuario su propia contraseña en lugar de la del superusuario:

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/f2fc2fa6-b214-49a1-8777-14d46bce956a)

No identifica el comando.

- Todavía es posible un shell raíz sudousando la opción "-i":

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/5a4f1b06-5542-49f8-acc4-9415a3c458f3)

### Cambiar la propiedad del archivo

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/fa5be534-1105-4902-b9cf-fa08a2d648ba)

### Cambiar la propiedad del grupo

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/0a93287a-b44b-4249-a974-3969a361764d)

## Job Control

Aqui explora la naturaleza de multitarea de Linux y cómo se controla a través de la interfaz de línea de comandos. Aunque Linux ejecuta múltiples procesos aparentemente simultáneos, en realidad, un solo núcleo de procesador solo puede ejecutar un proceso a la vez. El kernel de Linux administra estos procesos para darles a cada uno un turno en el procesador. Se presentan varios comandos para controlar los procesos, como ps para listar los procesos, kill para enviar señales a los procesos (a menudo para "matar" un proceso), jobs para listar los procesos propios, y bg y fg para poner un proceso en segundo plano o primer plano, respectivamente.

### Un ejemplo práctico

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/b069fd8e-8e17-4109-8292-104c5cb3aed3)

Nos indica que no reconoce el comando.

### Poner un programa en segundo plano

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/2a3114e6-cbe7-41ae-8e9d-718850e328b2)

- El proceso todavía existe, pero está inactivo. Para reanudar el proceso en segundo plano, escriba el bgcomando (abreviatura de fondo). Aquí hay un ejemplo:

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/c5b55623-173b-411d-a5c0-8c68db8ee8fd)

No reconoce el comando.

### Listado de procesos en ejecución

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/643196c3-a07d-40fc-9b72-53ead056646d)

### Matar un proceso

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/cb46a503-ba29-4a5f-9432-73029259ee05)

### Un poco más sobre matar

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/6b74c168-6066-4dfe-96e6-39327da01137)

- Utilice el pscomando para obtener la identificación del proceso (PID) del proceso que queremos finalizar.
- Emita un killcomando para ese PID.
- Si el proceso se niega a terminar (es decir, ignora la señal), envíe señales cada vez más duras hasta que termine.

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/c77f6f3f-0c21-4155-b5ad-1157f001dbf3)

El comanddo no realiza el procesamiento.

- En la práctica real, es más común hacerlo de la siguiente manera ya que la señal enviada por defecto killes SIGTERM y killtambién puede usar el número de señal en lugar del nombre de la señal:

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/e5d7ab49-13bd-4aeb-a775-a9b938a0bd8a)

- Luego, si el proceso no termina, fuercelo con la señal SIGKILL:

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/f17ae7d8-6696-49ce-9816-f7ab317e01a7)

El comando no logra procesar los archivos.
