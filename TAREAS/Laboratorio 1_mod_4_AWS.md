# Laboratorio 1 Módulo 4: Lanzamiento de una instancia de EC2

El objetivo de este laboratorio es crear una instancia de Amazon Elastic Compute Cloud (Amazon EC2), donde aloja un sitio web sencillo.

## TareA 1: Creación de la instancia y asignación de nombre
- Elegimos:
  
![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/c7dc3748-2c98-4cdf-ab80-cacd6faf9806)

- Lanzamos la instancia:
  
![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/d9effabe-2740-4de6-853c-8c395299edcd)

- Colocamos el nombre a la instancia como *Web Server 2*:

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/65f08870-cf45-4f46-a34e-03e362ec3541)

## Tarea 2: Colocar las imágenes de aplicación y sistemas operativos
- Elegimos una AMI (Imagen de máquina de Amazon) a partir de la cual crear la instancia:
  
![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/91dfa028-01ab-4dc8-b88f-44c9d74e2be0)

## Tarea 3: Elegimos el tipo de instancia
- Especificamos el tipo de instancia que sera el valor predeterminado **t2.micro**:
  
![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/1d0da033-94ef-4e65-83f8-69e5a4ff1450)

## Tarea 4: Selección de un par de claves
- Seleccionamos el par de claves que se asociará con la instancia que es en este caso **vockey**:

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/a2bf5a8b-82dc-4384-9609-af912b2bce98)

## Tarea 5: Configuración de la red
- En la configuración de red, seleccionamos **EDITAR**:

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/9296d558-43f4-412e-a13c-accfca191df6)

- Luego mantenemos la configuración determinada de VPC y *subred*, juntamente con la asignación automática de la IP pública que debe estar **Habilitada**:
  
![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/c6d35d27-0a6c-4801-badd-0f6eaf0eea8a)

- Entonces, en el firewall (Grupos de segurdad), mantenemos seleccionado la opción predeterminada **CREAR GRUPO DE SEGURIDAD**

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/b5d0dc10-82d2-41ac-a889-15ea1be259d7)

- Seguidamente configuramos un nuevo grupo de seguridad, con el nombre de *Web Server* y con la descripción de *Security group for my web server*.

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/681e6608-c2c0-4b54-abe7-f29fb170c413)

- Despues, ponemos **Eliminar** para eliminar la regla de entrada SSH predeterminado.
  
![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/c968583c-9c1c-448d-a0ac-89a1a105bf75)

## Tarea 6: Configuración del almacenamiento
- Mantenemos la configuración predeterminada

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/b8db7b37-3f19-4cb0-83d0-3fd035e8a547)

## Tarea 7: Detalles avanzados
- Configuramos un script de Bash para ejecutarse en la instancia cuando se lance, copiando en el cuadro los **Datos de usuario**.
  
![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/0f8ab882-c0a4-4315-912e-f54b544f67f7)

## Tarea 8: Revisar la instancia y lanzarla
- En la parte inferior del panel **Resumen**, colocamos **Lanzar Instancia**

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/7a4af049-ccdf-42ba-a335-8dbb3fd59287)

- Luego de lanzar la instancia nos tiene que salir la confirmacón de que se realizó el proceso correctamente:

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/59186d99-57da-4496-b774-c51a1dee251e)

## Tarea 9: Acceso a la instancia de EC2

- Una ves de haber verficado el procedimiento, cuando seleccionamos podemos ver los detalles, para copiar el valor de la **dirección IPv4 pública**
 
![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/ac51312b-5838-4aee-bcf6-9fedf608f2ae)

## Tarea 10: Actualización del grupo de seguridad
- Si colocamos la dirección IPv4 en una nueva pestaña de nuestro navegador, este no podrá acceder al servidor web porque el grupo de seguridad no permite el tráfico entrante en el puerto 80, que usualmente se utiliza en para solicitudes web HTTP, por lo cual en esta sección actualizaremos el grupo de seguridad.

- Entramos a la sección de **Security Groups (grupos de seguridad), paraa luego seleccionar el gruppo de segurdad de **Web Server** que se creó cuando lanzamos la instancia.

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/324b19e4-126e-49b2-8972-ce2fbfc6d4a1)

- Luego, seleccionamos la pestaña de **Reglas de entrada**

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/1c1a0e78-054c-41bc-a04e-3902d6bcea07)

## Tarea 11: Crear una regla de entrada
- Seleccionamos **Editar reglas de entrada** y elegimos agregar regla
  
![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/48aacca9-a86a-47f3-ae86-cbbb1e35f544)

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/dd6c7da6-f603-43d6-9c95-5b4cbf69e0ba)

- Realizamos la siguiente configuración: Tipo: HTTP, Origen: Anywhere-IPv4 y Seleccionamos **Guardar reglas**.
  
![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/523e81e2-7907-45a1-8a8a-91e29e311bde)

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/4ff69498-6fd6-4df1-8534-c13c298103c3)

## Tarea 12: Probar la regla
- Finalmente volvemos a la página que utilizamos para intentar conectarnos al servidor web y actualizamos la página donde nos deberia mostrar el mensaje de **"Hello World"** (¡Hola Mundo!).
  
![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/a5ab5008-86e5-4cd8-81a3-55c331291169)

- Resultado final del laboratorio
  
![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/f80380e3-e9b8-49b7-9f09-3e1e6aa78f76)
