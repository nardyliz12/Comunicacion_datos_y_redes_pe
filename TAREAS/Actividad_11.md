# ACTIVIDAD 11: Conceptos de introducción a las redes

Aspectos básicos de la actividadSean los siguientes conceptos dados en clase:ARPANET Backbone Bluetooth Broadcast Cache memory Checksum Client Client–servernetwork Computer network CRC DDN Encryption and decryption Encryption key EthernetFirewall Frame Relay Gateway Hub Internet LAN MAC address MODEM Multicast Networkcache Network device NIC Nonce value OSI model Packet switching Peer-to-peer networkPrivate key Protocol Protocol stack Public key Repeater RFC Router Server Switch TCP/IPTopology Unicast WAN,


## PROBLEMA 2: Diseño de red segura

### Escenario:

Una empresa necesita diseñar una red segura que conecte tres sucursalesubicadas en diferentes ciudades utilizando tecnología WAN y LAN. La empresa manejadatos confidenciales y requiere que la comunicación entre sucursales sea cifrada.

### Preguntas:

**1. ¿Qué tipo de tecnología de WAN utilizarías para conectar las sucursales y por qué?(Considera opciones como Frame Relay, MPLS, etc.)**

**2. Describe cómo implementarías el cifrado en la red. ¿Qué tipos de claves yprotocolos utilizarías?**

**3. Dibuja una topología de red que incluya dispositivos como routers, switches, yfirewalls. Explica la función de cada dispositivo en tu diseño. Puedes utilizar PacketTracer**

**4. ¿Cómo garantizarías la integridad y autenticidad de los datos transmitidos entre lassucursales? Detalla el uso de checksums o CRC.**

- Para tu presentación y código a presentar puedes utilizar:

#### Requisitos:

1. Conexión WAN Segura: Utilizar VPNs para asegurar todas las comunicaciones entresucursales.
3. Cifrado: Implementar cifrado de extremo a extremo.
4. Topología de Red: Incluir dispositivos de red como routers, switches y firewalls.4. Automatización: Usar Python para configurar aspectos de la red automáticamente.

#### Parte 1: Diseño de topologia de red

#### Preguntas:

- **Dibuja una topología de red para este esccenario que incluya los dispositivos de red necesarios ca da sucursal.**

- **Explica cómo cada dispositivo contribuye a la seguridad y eficiencia de la red.**

#### Parte 2: Configuración de VNP de red

### Código python

#### Preguntas adicionales:

- ¿Cómo implementarias el cifrado de extremo a extremo además de la VNP? Considdera el uso de claves públicas y privadas.

- Proporciona un esquema para implementar un sistema robusto de logs y monitoreo de la red utilizando herramientas modernas de gestión de red. ¿Cómo podría python automatizar la recopilación?

## PROBLEMA 2: Optimización de protocolos y caché

### Escenario:

Una empresa de streaming de video experimenta interrupciones frecuentes en laentrega de contenido a los clientes. La infraestructura actual utiliza multicast para distribuircontenido, pero aún enfrenta problemas de latencia y pérdida de paquetes.

#### Preguntas:

**1. Explica cómo mejorarías el rendimiento utilizando técnicas de caché de red. ¿Dóndecolocarías estos cachés y por qué?**

**2. ¿Cómo afecta el protocolo de transporte al rendimiento del streaming de video?Considera TCP vs UDP y justifica tu elección.**

**3. Propone una solución usando Anycast para optimizar la entrega de contenido.¿Cómo funcionaría en este contexto?**

**4. Desarrolla un modelo simplificado para calcular el efecto de la caché en la reducciónde latencia.**

- Para tu presentación y código a presentar puedes utilizar:

##### Requisitos:

1. Mejora del rendimiento utilizando técnicas de caché de red.
2. Elección y configuración del protocolo de transporte adecuado para reducir lalatencia y mejorar la confiabilidad.
3. Implementación de Anycast para optimizar la entrega de contenido a los usuarios.
4. Simulación y automatización utilizando Python.

#### Parte 1: Implementación de caché de rd con python

#### Código python:

#### Parte 2: Selección del protocolo de transporte

- **Discusión:**

- Explica las ventajas de usar UDP sobre TCP para streaming de video, considerando las características de ammbos protocolo

- Analiza los posibles problemas dde confiabilidad y orden de llegada de los paquetes y cómo mitigarlos

#### Parte 3: Implementación de anycast con python

##### Código de pyton

#### Parte 4: Monitorización y análisis

- Usa wireshark para caprurar paquetes de red y analiza el tráfico espcífico de video para identificar patrones de uso y posibles cuellos de botella.

## PROBLEMA 3: Simulavión de ataque y respuesta

### Escenario:

Eres el administrador de seguridad de una red corporativa y has notado unaumento en el tráfico ARP anómalo. Sospechas que esto podría ser parte de un ataque deARP spoofing, donde un atacante podría estar intentando interceptar la comunicación entredos partes para robar o modificar datos transmitidos.
### preguntas:

**1. Describe cómo identificarías si estas transmisiones ARP son realmente maliciosas.**

**2. ¿Qué medidas tomarías para mitigar el ataque una vez confirmado?**

**3. Explica cómo un switch y un firewall pueden configurarse para prevenir futurosataques de este tipo.**

**4. Formula un plan para educar a los empleados sobre medidas de seguridad quepueden tomar para reducir el riesgo de ataques futuros.**

- Para tu presentación y código a presentar puedes utilizar:

##### Requisitos:

1. Detección de ARP Spoofing: Implementar un sistema de detección para identificarposibles ataques.
2. Mitigación del Ataque: Desarrollar un método para mitigar o detener el ataque unavez detectado.
3. Automatización y Monitorización: Usar Python para automatizar la detección yrespuesta, y monitorear continuamente la red para futuros ataques.
4. Educación de Empleados: Proporcionar un plan para educar a los empleados sobrecómo pueden ayudar a reducir el riesgo de futuros ataques.

#### Parte 1: Detección de ARP Spoofing con Python

#### Código python:

#### parte 2: Mitigaciónn del Ataque

- *Discusión de Estrategias de Mitigación*

- **Seguridad en el Switch: Habilitar funciones de seguridad como Dynamic ARPInspection (DAI) en los switches.**
  
- **Uso de Seguridad de Puerto: Configurar la seguridad de puerto en los switches paralimitar el número de MACs por puerto y prevenir posibles ataques.**

#### Parte 3: Automatización y monitorización
##### Código de python:
 
## PROBLEMA 4: Análisis y diseño de red Peer-to-Peer (P2P)
### Escenario: 

Una startup tecnológica desea implementar una red P2P robusta para permitir elintercambio eficiente de recursos computacionales entre usuarios distribuidosgeográficamente. Esta red debe ser capaz de manejar intercambios dinámicos de archivos,distribución de carga, y debe incorporar medidas de seguridad para prevenir accesos noautorizados

### Preguntas: 

**1. Describe cómo se diferenciaría esta red P2P de una red cliente-servidor en términosde diseño de red y topología.**

**2. ¿Qué protocolos específicos usarías para gestionar las comunicaciones y elintercambio de archivos en esta red?**

**3. Analiza los posibles problemas de seguridad asociados con una red P2P y proponesoluciones para mitigar estos riesgos.**

**4. Evalúa el impacto de incorporar nodos que actúan tanto como clientes comoservidores. ¿Cómo gestionarías el balanceo de carga?**

- Para tu presentación y código a presentar puedes utilizar:

#### Requisitos:

1. Implementación de la Red P2P: Desarrollar un modelo de red P2P utilizando Pythonque permita a los nodos unirse, compartir recursos y desconectarse de maneradinámica.
2. Gestión de Recursos y Distribución de Carga: Asegurar que los recursos secompartan de manera eficiente y que la carga se distribuya equitativamente entre losnodos.
3. Seguridad: Implementar mecanismos de seguridad para autenticar a los usuarios ycifrar los intercambios de archivos.
4. Automatización y Simulación: Utilizar Python para simular el comportamiento de lared y automatizar tareas comunes de gestión de la red

#### Parte 1: Implementación de la Red P2P con python
##### Codigo de python:

#### Parte 2: Gestión de recursos y distribución de carga

- *Estrategias de equilibrio de carga:*

- **Implementar un algoritmo que asigne más carga a los nodos con más recursosdisponibles.**

- **Usar un algoritmo round-robin para asegurar que todos los nodos compartan demanera equitativa la carga de trabajo.**

#### Parte 3: Seguridad en la Red P2P

##### Código python:

