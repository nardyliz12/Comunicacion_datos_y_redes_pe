# ACTIVIDAD 10: Aprendiendo DNS

### Objetivos
-  Observar la conversión de una URL en una dirección IP.
-  Observar la búsqueda del DNS utilizando el comando nslookup
  
## Observa la conversión DNS.

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/260c398b-5152-4b6c-bc2a-f3d278fc59fc)

- **¿Qué dirección IP aparece en la pantalla?**
  
La dirección IP que aparece en pantalla es 72.163.4.185.

- **¿Es la misma que aparece en la imagen?**
  
No son las mismas direcciones, ya que, lo que se muestra en la imagen tiene una dirección IP de 72.163.4.161, mientras que el otro que se nos muestra en pantalla es 72.163.4.185.

- **¿Cisco.com siempre debe resolver la misma dirección IP? Explica**

Tras realizar los pasos correspondiente podemos concluir que no siempre va ser la misma dirección IP, ya que, en este caso depende mucho del donde esta abriendo esta configuración de dirección IP, dado que si hacemos el mismo procedimiento en otra computadora lo mas probable es que nos brinde otra dirección IP.

## Verifica el funcionamiento de DNS con el comando nslookup.

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/ebfe11bf-0085-4b09-b32a-ac0616ea0e27)

- **¿Cómo figura su servidor predeterminado?**
  
En este caso lo que fígura en mi servidor es muy diferente a lo que muestra en la imágen proporcionada, dado que lo que nos muestra en el *Defauld Server* es *Unknow*, mientras que en la dirección nos da lo siguiente: 192.168.18.1, lo que significaria una configuracción distinta que quiza sea por parte del sistema de cada operador.

- **Menciona los tres comandos que puede usar con nslookup:**
  
- **root=NOMBRE** - Establece un servidor raíz en NOMBRE.
- **all **        - Opciones de impresión, servidor actual y host.
- **set OPCIÓN**  - Establecer una opción

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/c902b7d3-94d1-46ce-9539-55bbc4072518)

- **¿Cuál es la dirección IP traducida?**

A lo que se muestra en el servidor es 2001:420:1101:1::185

- **¿La dirección IP es una dirección IPv4 o una dirección IPv6?**

Es una dirección IPv6, ya que nos muestra la siguiente dirección: 2001:420:1101:1::185.

- **¿Es la misma que la dirección IP que se muestra con el comando ping?**

Si es la misma dirección IP que se muestra al inicio con el comando ping de 72.163.4.185.

- **En el símbolo del sistema, escribe la dirección IP del servidor Web de Cisco que acabas deencontrar. ¿Cuál es el resultado del nombre?**

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/56d9f64f-99e4-40d5-a99a-84caf0eccd1c)

El nombre que nos da como resultado es **redirect-ns.cisco.com.**

##  Identifica servidores de correo utilizando el comando nslookup

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/e610b60b-1a0f-4318-b79d-685e363b3852)

- **¿Cuáles son los nombres de los servidores de correo de Cisco identificados en el campo mailexchanger?**

Son los siguientes:
- rcdn-mx-01.cisco.com
- alln-mx-01-cisco.com
- aer-mx-01.cisco.com

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/8428aaf8-f09b-46a8-9021-12a9b7b9cff6)


### Preguntas

- **Si la universidad no tuviera un servidor DNS, ¿qué efectos tendría esto en el uso de Internet?**

Tendria muchos efectos tales como tener dificultad para acceder a sitios web por nombres de dominio, tener dependencia de direcciones IP conocidas lo que seria poco práctico y dificil de gestiona a medida que aumenta la cantidad de sitios web en Internet, tambien llegaria a tener problemas de conectividad con servicos en la nube.

- **Algunas empresas no dedican un solo servidor para el DNS. Por el contrario, el servidor DNS también proporciona otras funciones. ¿Qué funciones crees que se pueden incluir en un servidor DNS? Usa el comando ipconfig /all para ayudarte con esto**

**Puede incluir funciones como:**

- Configuración IP de windows
- Adaptador de Ethernet Ethernet
- Adaptador de LAN inalámbrica Conexión de área local* 12
- Adaptador de LAN inalámbrica Conexión de área local* 14
- Adaptador de lan inalámbrica Wi-Fi
- Adaptador de Ethernet Conexión de red Bluetooth
