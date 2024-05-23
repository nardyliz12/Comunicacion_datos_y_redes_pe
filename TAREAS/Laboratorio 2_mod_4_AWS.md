# Laboratorio 2 Módulo 4: Creaciónde un Bucket de S3

El objetivo de este laboratorio es crear un bucket de Amazon Simple Storage Service (Amazon S3) para alojar un sitio web estático.

## Tarea 1. Crear un S3 Bucket
- Primero localizamos los servicios de **Storage**(almacenamiento) y seleccionamos S3.
  
  ![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/bd294022-1f2a-40ac-89c2-6dd46a1f96db)

- Luego seleccionamos **Create bucket** (crear bucket)

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/4a3a02f1-d96e-4077-b377-a2568085effa)

- Luego introducimos el nombre con el cual vamos a crear nuestro nuevo bucket

  ![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/f15c94e9-77e8-4e5b-b43f-119e5906c036)

- En cuanto a la Región, elija la región de AWS en la que desea que resida el bucket.
  
![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/d791c3c7-a6d3-40af-8a1f-df489b404fc3)

- Desmarque la casilla Block all public access (Bloquear todo el acceso público) porque quiere poder probar si el sitio web funciona.
  
![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/456b5dc7-5286-4f10-b73a-a9cd641be8e9)

- Debajo aparece un mensaje de advertencia, en esa casilla vamos a marcarlo para poder continuar

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/2720ed83-47c1-41a7-a426-8e7aeb26561c)

- Vaya al final de la página y seleccione Create bucket (Crear bucket).

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/dbf2d7b0-6357-4527-9a10-3a1eed1b2c8d)

## Tarea 2:  Agregar una política de bucket para que el contenido esté disponible de manera pública
- Elija el enlace del nombre de su bucket y, a continuación, seleccione la pestaña Permissions (Permisos).

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/dfbd4ce8-00f8-42b1-97fa-d3d92e51070a)

- En la sección Bucket policy (Política del bucket), elija Edit (Editar).

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/26bc9c6b-8818-464d-a131-7156dec7b988)

- Para conceder acceso de lectura público al sitio web, copie la siguiente política de bucket y péguela en el editor de políticas.

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/36586270-36a4-4bca-9469-b270befa17e3)

- Y guardamos los cambios

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/dbb1aa75-9f6a-4d6c-b38e-f0efbed79eab)

## Tarea 3: Cargar un documento HTML

- Abra el menú contextual (haga clic con el botón derecho del ratón) en el siguiente enlace y, a continuación, seleccione Save link as (Guardar enlace como): index.html y guardalo en tu navegador, luego En la consola, seleccione la pestaña Objects (Objetos).

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/4759bae1-e574-4b46-90ed-c5ec9704d830)

- Carga el archivo index.html en el bucket y arrastra el archivo.
  
![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/158f4872-6e1b-41a0-bc1f-6e3233d9b471)

- Ahora ve a la sección de **Properties**(propiedades)
 
![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/5a845521-8310-4feb-b514-4f1c2bf95e04)

- Y colocamos cargar

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/0666d5d2-3a67-4984-a974-9d9197ec9b0a)

- Luego elija Close (Cerrar).

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/5875aa88-d740-44e1-9fef-a9bd88b0f659)

## Tarea 4: Probar el sitio web

- Seleccione la pestaña Properties (Propiedades) y baje hasta la sección Static website hosting (Alojamiento de sitios web estáticos) y elija editar.

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/a3c1edf2-f6c5-46d5-acf2-f84e14631ae9)

- Y seleccione **Enable** (Habilitar)
  
![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/667bcb1d-2776-4936-9177-1e3da775f854)

- En el cuadro de texto Index document (Documento de índice), ingrese index.html y seleccione guardar cambios.

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/2edeba8f-1fc6-437f-89c1-694cdc3ce6c7)

- Desplácese hacia abajo a la sección de Static website hosting (Alojamiento de sitios web estáticos) y copie la URL del Bucket website endpoint (punto de enlace del sitio web del bucket) en el portapapeles y pongalo en una nueva pestaña de su navegador.

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/25b23125-8c04-4e20-bd3b-4ac42e720128)

- Resultado final del laboratorio

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/a1c6e5d6-a200-4683-a3a8-174a3cc248d9)

