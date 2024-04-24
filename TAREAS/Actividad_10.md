# ACTIVIDAD 9: Uso de Wireshark para ver el tráfico de la topología de red.

### Objetivos
- Parte 1: Capturar y analizar datos ICMP locales en Wireshark
- Parte 2: Capturar y analizar datos ICMP remotos en Wireshark
  
![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/45cf4ea7-5381-4485-bd2d-d0b5d68d0861)

## 1. Captura y análisis de datos ICMP locales en Wireshark

### Recupera las direcciones de interfaz de la PC

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/c2c82400-3f2f-44fb-b0fb-35e63d3b8744)

### Inicia Wireshark y comienza a capturar datos

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/4cf59972-ca8c-4c37-a02b-d24061d851eb)

### Examina los datos capturados

- **¿La dirección MAC de origen coincide con la interfaz de su PC?**
  
  Si coincide la interfaz tanto en mi PC y el ejemplo brindado.
  
- **¿La dirección MAC de destino en Wireshark coincide con la dirección MAC del compañero de equipo?**

Si coincide al momento de hacer la comparaación.

- **¿De qué manera su PC obtiene la dirección MAC de la PC a la que hizo ping?**

Dentro de una lan, los paquetes van con direccion de origen y de destino, por lo que, se conoce la dirección MAC, porque está dentro de la misma red de área local, que es como un switch. 

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/630eef04-4251-43dd-be7b-d9225eb8501c)

## 2. Captura y analiza datos ICMP remotos en Wireshark

### Inspecciona y analiza los datos de los hosts remotos

- **¿Qué es importante sobre esta información?**

Que en todas las direcciones MAC tendremos la misma dirccion MAC, porque es la direccion del router.
  
- **¿En qué se diferencia esta información de la información de ping local que recibió?**

Se diferencia en la parte de direcciones MAC, porque no tenemos dicho acceso.

- **¿Por qué Wireshark muestra la dirección MAC vigente de los hosts locales, pero no la dirección MACvigente de los hosts remotos?**

Porque no tenemos acceso, es decir, si no corresponde a una red local, no tenemos dicho acceso, un switch no une redes, sino dispositivos, sino los routers. 
