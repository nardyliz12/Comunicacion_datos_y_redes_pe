# ACTIVIDAD 13: TCP/IP

### Aspectos básicos de la actividad:

Sean los siguientes conceptos dados en clase:5-4-3 rule Anonymous FTP Application layer ARP ARP table Connection DHCP Dynamic IPaddress Email-delivery agent Email-retrieval agent Flow control FTP HTTP Header Headerextension ICMP IGMP IMAP Internet layer Interoperability IP address prefix Keep aliveLDAP Link layer Multiplexing MIME MTU NAT NDP Netmask POP Port R-utilities Self-signedcertificate Sequence number SFTP SSH SMTP SSL/TLS Stateless AddressAutoconfiguration Static IP address TCP three-way handshake Telnet TTL Transport layerTunnel X.509 certificate.

## PROBLEMA 1: Diseño de un sistema de entrega y recupración de correo electrónico

### Contexto: na empresa necesita diseñar un sistema de correo electrónico robusto queutilice SMTP, IMAP, y SSL/TLS para la entrega y recuperación segura de correo electrónico.

#### Requisitos:
● Desarrollar un diagrama de red que muestre cómo se integrarían SMTP, IMAP, ySSL/TLS en la infraestructura existente.

● Escribir un pseudocódigo para la configuración del servidor SMTP y IMAP quetambién maneje conexiones SSL/TLS.● Explicar cómo se gestionarán los certificados X.509 en este sistema y la importanciade estos para SSL/TLS.

● Discutir cómo se manejarán las direcciones IP dinámicas y estáticas dentro de estared, especialmente en relación con DHCP y NAT.

- Para tu presentación y código a presentar puedes utilizar:Requisitos técnicos y diseño:

##### Configuración del Servidor SMTP y IMAP:

1. Implementaremos servidores SMTP y IMAP usando librerías en Python que simulenel comportamiento de estos protocolos. Manejo de SSL/TLS:

2. Utilizaremos SSL/TLS para encriptar las conexiones SMTP e IMAP, garantizando laconfidencialidad y la integridad de los datos transmitidos. Integración con DHCP y NAT:

3. Discutiremos cómo las direcciones IP dinámicas asignadas por DHCP y latraducción de direcciones realizada por NAT pueden afectar la configuración y elfuncionamiento de los servidores de correo.

#### Paso 1: Configuración del servidor SMTP y IMAP en Python

##### Código python

#### Paso 2: 

- Implementación de SSL/TLSPara implementar SSL/TLS en estos servidores, utilizamos la opción de conexión segura ensmtplib (SMTP_SSL) y imaplib (IMAP4_SSL). Esto garantiza que todas las comunicacionesentre el cliente y el servidor están encriptadas.

#### Paso 3: Manejo de Certificados X.509

- Los certificados X.509 se utilizan para validar la identidad del servidor. Los detalles sobrecómo se manejan estos certificados, especialmente en relación con la creación y elalmacenamiento, serían cruciales

##### Código Python

#### Paso 4: Discusión sobre DHCP y NAT

- Es importante discutir cómo la asignación de direcciones IP dinámicas a través de DHCP yla traducción de direcciones IP realizada por NAT pueden afectar el acceso y la visibilidadde los servidores de correo desde el exterior de la red local. Es posible que se necesitenconfiguraciones de NAT estático o el uso de servicios DNS dinámicos para garantizar quelos servidores sean accesibles consistentemente.

## PROBLEMA 2: Implementación de un protocolo de redd personalizado sobre TCP

### Contexto: 

Diseñar un protocolo de aplicación personalizado para un sistema de archivosdistribuido que se ejecutará sobre TCP, utilizando técnicas como multiplexación y control deflujo.

##### Requisitos:

● Definir el formato del mensaje, incluyendo cabeceras y extensiones de cabecera.

● Desarrollar un esquema de control de flujo que gestione eficazmente la transferenciade archivos grandes a través de redes con alta latencia.

● Escribir un pseudocódigo para las funciones de conexión, como el handshake detres vías de TCP, y cómo se manejará la retransmisión.

● Evaluar el uso de NAT y su impacto en las conexiones de red en este protocolo,particularmente cuando se utilizan direcciones IP dinámicas.

- *Para tu presentación y código a presentar puedes utilizar:*

##### Objetivos:

1. Diseño del protocolo: Definir el formato del mensaje, incluidas las cabeceras y lasextensiones de cabecera para manejar funcionalidades específicas como control deflujo y recuperación de errores.
2. Implementación de control de flujo: Desarrollar un esquema de control de flujo paramanejar eficazmente la transferencia de datos sobre TCP.
3. Simulación con Python: Simular el protocolo utilizando Python para evaluar surendimiento y robustez en escenarios de red simulados.

#### Paso 1: Diseño del protocolo
Vamos a definir un protocolo simple que incluya operaciones básicas como PUT, GET, yDELETE para interactuar con archivos en el sistema distribuido.

- Ejemplo de Especificación del Protocolo:

● PUT: Enviar un archivo al sistema.

● GET: Recuperar un archivo del sistema.

● DELETE: Eliminar un archivo del sistema.

Cada mensaje tendrá una cabecera que incluye el tipo de operación, el tamaño delmensaje, y un número de secuencia para el control de flujo y la recuperación de errores

#### Paso 2: Implementación de control de flujo

##### Código Python para simulación del protocolo:

#### Paso 3: Evaluación del protocolo
- Después de implementar el protocolo, usaríamos herramientas como Wireshark paramonitorear la eficacia del control de flujo y el manejo de errores durante la transferencia dearchivos. Esto podría involucrar la simulación de condiciones de red adversas, como altalatencia y pérdida de paquetes, para ver cómo el protocolo se comporta y se recupera deestos problemas.

## PROBLEMA 3: Creaciónn de un sistema de autenticación segura con LDAP y  SSH

### Contexto: 
Una organización requiere un sistema de autenticación segura que utilice LDAPpara la gestión de identidades y SSH para el acceso remoto.

#### Requisitos:

● Diagramar cómo LDAP y SSH pueden integrarse para proporcionar un sistema deautenticación y autorización.

● Discutir la implementación de un túnel SSH que pueda encapsular la comunicaciónLDAP, incluyendo detalles sobre la configuración de port forwarding.

● Escribir un pseudocódigo que ilustre cómo se puede implementar un certificadoautofirmado y cómo LDAP maneja la autenticación.

● Analizar el papel de la capa de transporte en este sistema, con énfasis en losdetalles de SSL/TLS para la protección de datos.

- *Para tu presentación y código a presentar puedes utilizar:*

##### Objetivos:
1. Integración de LDAP y SSH: Configurar un servidor LDAP y permitir el accesoseguro a través de SSH, incluyendo el reenvío de puertos y la encapsulación.
2. Implementación de Seguridad: Utilizar técnicas de cifrado y autenticación,incluyendo el manejo de certificados autofirmados.
3. Simulación con Python: Implementar scripts en Python que simulan la configuracióny operación de este sistema de autenticación.
4. Evaluación de Seguridad: Discutir cómo evaluar la seguridad del sistema y manejarposibles vulnerabilidades.

#### Paso 1: Configuración de LDAP y SSH

- Vamos a configurar un servidor LDAP y proporcionar acceso a él a través de un túnel SSHseguro. Usaremos Python para simular el establecimiento de una conexión SSH conreenvío de puertos

##### Código de python

#### Paso 2: Implementación de seguridad

- Usaremos SSL/TLS para cifrar la comunicación LDAP. Además, configuraremos certificadosautofirmados para asegurar la comunicación entre el cliente y el servidor LDAP a través deltúnel SSH.

##### Código Python para la generación de certificados autofirmados:

#### Paso 3: 
- Evaluación de seguridadDiscutir cómo evaluar la seguridad del sistema implementado, abordando potencialesvulnerabilidades como ataques de intermediario y configuraciones erróneas de certificados.La evaluación incluirá pruebas de penetración y revisión de configuraciones

## PROBLEMA 4: Simulación de interpolaridad de red con múltiples protocolos

### Contexto: 

Simular un entorno de red que utilice múltiples protocolos de la pila TCP/IP,asegurando la interoperabilidad entre dispositivos que utilizan diferentes configuraciones dered.

#### Requisitos:

● Crear un escenario que implique IP, ICMP, IGMP, y ARP, describiendo cómo cadauno afecta la operación y gestión de la red.

● Desarrollar un plan para la simulación de esta red, incluyendo la configuración de latabla ARP, el manejo de ICMP para la detección de errores, y la utilización de IGMPpara la gestión del tráfico multicast.

● Proponer métodos para probar y validar la interoperabilidad de estos protocolos endiferentes segmentos de la red.

● Discutir cómo se podrían usar las utilidades de red (R-utilities) para monitorear yresolver problemas en esta red.

- *Para tu presentación y código a presentar puedes utilizar:*

##### Objetivos:
1. Simulación de protocolos de Red: Crear un entorno simulado que incluya IP, ICMP,IGMP, y ARP para observar y gestionar la comunicación entre dispositivos.
2. Implementación de la simulación en Python: Utilizar Python para crear scripts quesimulen el envío y recepción de paquetes utilizando estos protocolos.
3. Evaluación de interoperabilidad: Analizar cómo estos protocolos interactúan ygestionan la conectividad, especialmente en escenarios de alta densidad de red ytráfico multicast.
4. Uso de R-utilities para monitoreo y resolución de problemas: Implementar y discutircómo herramientas como traceroute, ping y otras utilidades pueden ayudar adiagnosticar y resolver problemas en la red.

#### Paso 1: 
- Simulación de protocolos de red en PythonUsaremos Python para simular la generación y el manejo de paquetes de red para IP, ICMP,IGMP y ARP. Utilizaremos la biblioteca scapy, que es muy potente para manipular y enviarpaquetes de red.

##### Código Python para la simulación de protocolos:

#### Paso 2: Evaluación de interoperabilidad
- Después de simular cada protocolo, observaremos cómo los paquetes son gestionados ydirigidos a través de la red. Esto ayudará a identificar problemas de interoperabilidad yeficiencia en la comunicación entre dispositivos.

#### Paso 3: Uso de R-utilities para diagnóstico
- Implementaremos scripts para utilizar R-utilities como traceroute y ping, y simular cómo sepueden usar para monitorear y diagnosticar problemas en la red.Código Python para Utilizar R-utilities:






