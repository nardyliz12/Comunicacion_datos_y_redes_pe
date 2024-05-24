# Laboratorio de Módulo 5: Uso de CloudFront como CDN para un sitio web

El objetivo de este laboratorio es utilizar Amazon CloudFront como red de entrega de contenido (CDN) para un sitio web que se almacena en Amazon Simple Storage Service (Amazon S3). 

## Tarea 1: Crear un bucket de S3 mediante la utilización de AWS CLI
- Seleccione los Servicios y las Herramientas para desarrolladores y elija CloudShell, donde son aparece una ventana de bienvenida que pondremos cerrar.

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/ff4cd9fa-c15e-421a-9c59-01919eebf35a)

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/4ae43e8e-bc26-4233-b131-ed212aa758ec)

- Luego copiw el siguiente código en un editor de texto y colo colocamos el nombre del bucket que queramos y luego seleccione la opción de **Paste** (Pegar)

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/e99bd8de-3b79-4b84-a6a8-e2318bcf69cf)

- El resultado debe salir de la siguiente manera

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/d2b5f57d-de73-4ae2-a12d-292189b0c468)

## Tarea 2: Agregar una política de bucket
- n la consola, elija el menú Services (Servicios), localice la sección Storage (Almacenamiento) y elija S3.

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/0ffcb224-c54e-4ed3-bb09-61b3b9c97bf4)

- Luego eliga el bucket que acaba de crear 

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/41a7d5a5-4773-4a4c-b0b9-7c29d29c4088)

- Luego seleccione la pestaña Permissions (Permisos). 

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/1d492a30-a871-4c75-b3b9-dfe028b3873b)

- En Block public access (bucket settings) (Bloquear acceso público [configuración del bucket]), seleccione Edit (Editar). Desactive la marca de verificación de Block all public access (Bloquear todo el acceso público). Seleccione Guardar cambios. Confirme los cambios.

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/ca3051bf-a927-4447-8796-1926f5ddd487)

- Luego desactive la marca de verificación de Block all public access (Bloquear todo el acceso público). Seleccione Guardar cambios. Confirme los cambios.

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/a1f69ae3-dde7-4d70-9630-e29bf11402b0)
![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/86fd4759-2835-46ae-86f0-0180ae2d3dd4)

- En Object Ownership (Propiedad del objeto), elija Edit (Editar).  

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/f414b3bc-2145-4040-9263-bfb5d631bfe8)

- Luego seleccione ACLs enabled (ACL habilitadas).

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/13750f63-3b0f-4696-9ff7-e5d2b73e3718)

- Compruebe la confirmación y seleccione Save changes (Guardar cambios).

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/6b0e84f7-0b06-4dd8-b815-8b6c40936851)

- En la sección Bucket policy (Política de bucket), elija Edit (Editar).

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/c3a0a137-1eee-4112-bbb3-2d1891ff4747)

- Para conceder acceso público de lectura al sitio web, copie la siguiente política de bucket en el editor de políticas con el noombre respectivo del bucket creado anteriormente.

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/e949797b-a5f2-48f8-b93c-47db961f6d38)

## Tarea 3: Cargar un documento HTML
- Abra el menú contextual (haga clic con el botón derecho) del siguiente enlace y, a continuación, elija Save link as: (Guardar enlace como:) index.html y guardelo en su navegador

- Luego en la consola seleccione la pestaña de objetos y cargue el archivo anteriormente guardada.

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/678959f5-ab64-4ff5-9159-5e0e75fc92cf)

- En permisos, en la sección de Predefined ACL (ACL predefinidas), seleccione Grant public-read access (Conceder acceso público de lectura).
  
![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/6c41efe1-98ce-4c81-9424-f14aea83c7ca)

- Te va aparece un mensaje de advertencia, de ello marca la casilla junto con entiendo y coloca cargar, despues cerrar.

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/5b630a98-7141-49f2-926f-399305c8c44c)

## Tarea 4: Probar el sitio web
- Seleccione la pestaña Properties (Propiedades)

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/89b6ffc1-1f70-41c6-bc10-66409188107b)

- baje hasta la sección Static website hosting (Alojamiento de sitios web estáticos) y seleccione Edit (Editar). 

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/da533ac2-a842-48fb-b172-67fcb5becc56)

- Seleccione Enable (Habilitar).

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/2304a9b1-b8d3-45dc-bd42-969199a33554)

- En el cuadro de texto Index document (Documento de índice), ingrese index.html y pon guardar cambios

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/5f89369f-ebc7-40aa-a31f-7752b81dc1fd)

- Desplácese hacia abajo a la sección de Static website hosting (Alojamiento de sitios web estáticos) y copie la URL del Bucket website endpoint (punto de enlace del sitio web del bucket) en el portapapeles y abra el enlace en una ventana nueva, donde debe aparecer un mensaje

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/a366d2d5-592f-4a59-a471-1b01dafbabe8)

- Resultado del laboratorio

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/167c097b-aeba-4d5d-addd-1b75dc347596)

## Tarea 5: Crear una distribución de CloudFront para servir el sitio web
- Seleccione el menú Services (Servicios), localice la sección Networking & Content Delivery (Redes y entrega de contenido) y elija CloudFront.

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/c0411d60-e32d-4129-9a72-f0872bdc4e12)

- Elija Create a CloudFront distribution (Crear una distribución de CloudFront).

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/22f64c39-5b23-4401-bd84-bfa5510b1a32)

- En Origin (Origen), elija el cuadro de texto junto a Origin Domain (Dominio de origen) y seleccione el punto de enlace de su bucket de S3.

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/c6236397-eb1e-4975-bf61-902fd04d1fdb)

- Para la Viewer Protocol Policy (Política de protocolo del lector), asegúrese de que HTTP y HTTPS estén seleccionados.

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/8a936cfd-cf27-4074-8a1b-9a66e6e01e55)

- En Web Application Firewall (WAF) (Firewall para aplicaciones web [WAF]), seleccione Do not enable security protections (No habilitar protecciones de seguridad).

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/134352dd-6d76-467f-8c6e-35aa9c5bdfc5)

- Vaya a la parte inferior de la página y seleccione Create Distribution (Crear distribución).

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/6794eac7-cc39-42bd-bec8-dcc429f284e8)

- Copie el valor del Domain Name (Nombre de dominio) de su distribución y guárdelo en un editor de texto para utilizarlo más adelante.

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/9e392c95-bc0a-45d7-9fc0-277a0e6fa691)

- Vaya al bucket de S3 y suba el archivo de imagen a él, asegúrese de conceder acceso público como hizo al subir el archivo HTML anteriormente en este laboratorio.

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/47e0c9e1-5c2b-42a4-98e1-424cbedd9cf2)

- Cree un nuevo archivo de texto con el Bloc de notas y copie el siguiente texto en él y sustituye el nombre de dominio que se copio antes y la imagen subida anteriormente:
```
<html>
    <head>My CloudFront Test</head>
    <body>
        <p>My test content goes here.</p>
        <p><img src="https://d2w4986nbbs2xt.cloudfront.net/jhope.jpeg" alt="my test image">
    </body>
</html>
```
- Resultado final del laboratorio

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/d33cb696-6422-4e8d-9561-0c63ef38cbc5)
