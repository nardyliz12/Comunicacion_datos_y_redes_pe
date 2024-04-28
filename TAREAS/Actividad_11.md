# ACTIVIDAD 11: Conceptos de introducción a las redes

Aspectos básicos de la actividadSean los siguientes conceptos dados en clase:ARPANET Backbone Bluetooth Broadcast Cache memory Checksum Client Client–servernetwork Computer network CRC DDN Encryption and decryption Encryption key EthernetFirewall Frame Relay Gateway Hub Internet LAN MAC address MODEM Multicast Networkcache Network device NIC Nonce value OSI model Packet switching Peer-to-peer networkPrivate key Protocol Protocol stack Public key Repeater RFC Router Server Switch TCP/IPTopology Unicast WAN,


## PROBLEMA 1: Diseño de red segura

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

##### Código python

#### Preguntas adicionales:

- ¿Cómo implementarias el cifrado de extremo a extremo además de la VNP? Considdera el uso de claves públicas y privadas.

- Proporciona un esquema para implementar un sistema robusto de logs y monitoreo de la red utilizando herramientas modernas de gestión de red. ¿Cómo podría python automatizar la recopilación?

## PROBLEMA 2: Optimización de protocolos y caché

### Escenario:

Una empresa de streaming de video experimenta interrupciones frecuentes en laentrega de contenido a los clientes. La infraestructura actual utiliza multicast para distribuircontenido, pero aún enfrenta problemas de latencia y pérdida de paquetes.

#### Preguntas:

**1. Explica cómo mejorarías el rendimiento utilizando técnicas de caché de red. ¿Dóndecolocarías estos cachés y por qué?**

El caching de datos en la red es una técnica que permite a todas las aplicaciones y los sitios web recuperar información de forma rápida y eficiente, donde los datos se almacenan temporalmente en el lugar donde se necesitan, en lugar de enviarlos de nuevo desde el servidor cada vez que alguien los necesita. Esto reduce significativamente el tiempo que se tarda en servir respuestas, donde mejora la velocidad y la experiencia del usuario. Hagamos un ejemplo, en el caso de la empresa de streaming de video, los cáches se podrian colocar cerca de los puntos de acceso de cada uno de los usuarios para así poder reducir la latencia y mejorar la velocidad de transmisión y esto se debe a que los datos más solicitados por los usuarios se almacenarían temporalmente en estos cáche, lo que nos permitiría un buen acceso, es decir, que sea más rápido a estos datos y así reduciria la carga en los servidores centrales.

**2. ¿Cómo afecta el protocolo de transporte al rendimiento del streaming de video?Considera TCP vs UDP y justifica tu elección.**

El protocolo de transporte juega un papel muy crucial en el rendimiento del streaming de video, donde los dos protocolos de transporte más comunes son TCP (Transmission Control Protocol) y UDP (User Datagram Protocol). Donde TCP es un protocolo orientado a la conexión que garantiza la entrega de los paquetes a través de mecanismos de control de errores y de flujo, sin embargo, estos mecanismos pueden introducir latencia y reducir la velocidad de transmisión, lo que puede ser algo problemático para el streaming de video en tiempo real, mientras que UDP es un protocolo sin conexión que no garantiza la entrega de paquetes y no tiene mecanismos de control de errores o de flujo, lo que significa que UDP puede transmitir datos más rápido que TCP, pero a costa de posibles pérdidas de estos paquetes. Para el streaming de video, UDP suele ser la elección más preferida debido a su baja latencia y alta velocidad de transmisión, pero es importante tener en cuenta que la elección entre TCP y UDP depende mucho de las necesidades específicas de la aplicación que se quiere verificar.

**3. Propone una solución usando Anycast para optimizar la entrega de contenido.¿Cómo funcionaría en este contexto?**

Anycast es una técnica de red que nos permite dirigir las solicitudes de los usuarios al servidor más cercano geográficamente, reduciendo así la latencia y mejorando el rendimiento. En el contexto de la empresa de streaming de video, Anycast puede utilizarse para dirigir las solicitudes de los usuarios al servidor de contenido más cercano, lo que nos permitiría una entrega de contenido más rápida y eficiente para cada usuario.

**4. Desarrolla un modelo simplificado para calcular el efecto de la caché en la reducciónde latencia.**

Un modelo simplificado para calcular el efecto de la caché en la reducción de latencia podría basarse en el tiempo de acceso efectivo (EAT), que es una medida del tiempo promedio que se tarda en acceder a un dato en el caché o en la memoria principal. El EAT se puede calcular utilizando la siguiente fórmula:

*EAT = (Tasa de aciertos de caché * Tiempo de acceso a caché)+(tasa de errores de caché * Tiempo de acceso a memoria*

Donde:

- La tasa de aciertos de caché es la proporción de solicitudes de acceso que se pueden servir directamente desde la caché.
- El tiempo de acceso a caché es el tiempo que se tardaría en recuperar un dato de la caché.
- La tasa de errores de caché es la proporción de solicitudes de acceso que no se pueden servir desde la caché y requieren un acceso a la memoria principal.
- El tiempo de acceso a memoria es el tiempo que se tardaría en recuperar un dato de la memoria principal.

Este modelo nos proporciona una estimación de cómo el caché puede reducir la latencia al servir una mayor proporción de solicitudes de acceso directamente desde la caché, en lugar de tener que acceder a la memoria principal, pero es importante tener en cuenta que este es un modelo simplificado, donde rendimiento real puede variar en función de varios factores, como el comportamiento de acceso de la aplicación y la configuración de la caché que esta queriendo configurar.

- Para tu presentación y código a presentar puedes utilizar:

##### Requisitos:

1. Mejora del rendimiento utilizando técnicas de caché de red.
2. Elección y configuración del protocolo de transporte adecuado para reducir lalatencia y mejorar la confiabilidad.
3. Implementación de Anycast para optimizar la entrega de contenido a los usuarios.
4. Simulación y automatización utilizando Python.

#### Parte 1: Implementación de caché de rd con python

##### Código python:
```
class VideoCache:
    def __init__(self):
        self.cache = {}

    def get_video(self, video_id):
        if video_id in self.cache:
            print(f"Video {video_id} retrieved from cache")
            return self.cache[video_id]
        else:
            print(f"Video {video_id} not in cache, downloading...")
            video_data = self.download_video(video_id)
            self.cache[video_id] = video_data
            return video_data

    def download_video(self, video_id):
        # Simula la descarga del video desde un servidor remoto
        return f"Video data for {video_id}"

# Ejemplo de uso
cache = VideoCache()
video = cache.get_video("video12022004")
print(video)  
video = cache.get_video("video12022004")

```
#### Resultados:
```
Video video12022004 not in cache, downloading...
Video data for video12022004
Video video12022004 retrieved from cache
```
Este código implementa un caché de video utilizando una clase llamada `VideoCache`, donde la caché se implementa como un diccionario, ya que, las claves son los identificadores de los videos y los valores son los datos del video. El método `get_video` verifica si el video solicitado está en el caché, donde si está presente, lo devuelve directamente, pero si no está en la caché, simula la descarga del video desde un servidor remoto, y lo almacena en la caché donde luego lo devuelve. Esta implementación proporciona una forma eficiente de reducir la latencia al momento de almacenar en el caché de videos solicitados frecuentemente, mejorando así el rendimiento del sistema de distribución de video.

#### Parte 2: Selección del protocolo de transporte

- **Discusión:**

  - **Explica las ventajas de usar UDP sobre TCP para streaming de video, considerando las características de ammbos protocolo**

El Protocolo de Datagramas de Usuario (UDP) tiene varias ventajas sobre el Protocolo de Control de Transmisión (TCP) cuando se trata de streaming de video, de los cuales serian las siguientes:

  - Velocidad: UDP es más rápido que TCP, ya que, no requiere establecer una conexión antes de enviar datos.
  - Menor sobrecarga: Al no tener mecanismos de control de flujo, UDP presenta una menor sobrecarga de datos en comparación con TCP.
  - Transmisión en tiempo real: UDP es ideal para aplicaciones que requieren una transmisión más rápida y en tiempo real, pero pueden tolerar cierta pérdida de datos, como transmisiones de audio y video, juegos en línea y aplicaciones de streaming que son muy comunes hoy en dia.

- **Analiza los posibles problemas dde confiabilidad y orden de llegada de los paquetes y cómo mitigarlos**

Aunque UDP tiene varias ventajas, también presenta algunos desafíos, especialmente en términos de confiabilidad y orden de llegada de los paquetes que ciertas veces pueden llegar a ser un problema, donde tiene los siguientes puntos:

  - Falta de fiabilidad: Al no garantizar la entrega de los paquetes ni el orden de estos mismos, UDP puede resultar en una gran pérdida de datos o duplicación de información.
  - No orientado a la conexión: UDP no establece una conexión antes de enviar datos, por lo que puede llevar a la pérdida de los paquetes en entornos con alta congestión de red.

Ahora para poder mitigar estos problemas, podemos utilizar técnicas como:

   - Protocolos de nivel de aplicación: Nos pueden proporcionar mecanismos de control de errores y de flujo en la capa de aplicación, lo que nos puede ayudar a mejorar la confiabilidad de las transmisiones UDP.
  - Reenvío de paquetes: En caso de pérdida de los paquetes, el remitente puede reenviar los paquetes perdidos.
  -Buffering y reordenación de paquetes: Los receptores pueden utilizar buffers para almacenar y reordenar todos los paquetes que llegan fuera de orden.
  - Control de congestión: Podemoa utilizar algoritmos de control de congestión para ajustar la tasa de envío en función de las condiciones de la red, donde esto nos puede ayudar a reducir la pérdida de paquetes en entornos con alta congestión de red.

#### Parte 3: Implementación de anycast con python

##### Código de pyton
```
import random

class AnycastService:
    def __init__(self):
        self.servers = ['192.168.1.1', '192.168.2.1', '192.168.3.1']
    
    def get_nearest_server(self, user_ip):
        # Simula la selección del servidor más cercano (simplificado)
        return random.choice(self.servers)

# Ejemplo de uso
anycast = AnycastService()
nearest_server = anycast.get_nearest_server("192.168.1.44")
print(f"Nearest server for user is {nearest_server}")
```
#### Resultados:
```
Nearest server for user is 192.168.2.1
```
El código es una simulación conceptual de cómo se podría implementar anycast para dirigir las solicitudes de los usuarios al servidor de caché más cercano, donde clase `AnycastService` contiene una lista de direcciones IP de servidores y un método `get_nearest_server()` que simula la selección del servidor más cercano basándose en la dirección IP del usuario. En la simulación, se elige aleatoriamente un servidor de la lista como el servidor más cercano y esta implementación simplificada sirve para ilustrar el concepto de anycast en la distribución de solicitudes a servidores de caché.

#### Parte 4: Monitorización y análisis

- Usa wireshark para caprurar paquetes de red y analiza el tráfico espcífico de video para identificar patrones de uso y posibles cuellos de botella.
```
import pyshark

def analyze_video_traffic(interface='eth0'):
    # Especifica la ubicación de TShark
    tshark_path = '/usr/bin/tshark'  # Reemplaza con la ubicación correcta de TShark en tu sistema

    # Configura la ubicación de TShark para pyshark
    pyshark.tshark.tshark.tshark_path = tshark_path

    # Realiza la captura de paquetes en la interfaz especificada
    capture = pyshark.LiveCapture(interface=interface)

    # Imprime información sobre cada paquete capturado
    for packet in capture.sniff_continuously(packet_count=10):
        print(packet)

# Ejemplo de uso
analyze_video_traffic(interface='eth0')
```
Este código utiliza la biblioteca `pyshark` para realizar un análisis de tráfico de red en tiempo real en una interfaz de red específica, en este caso, 'eth0', primero, configura la ubicación de TShark, una herramienta de captura de paquetes, para que `pyshark` pueda encontrarla, luego, inicia una captura en vivo en la interfaz especificada y, para cada paquete capturado, imprime información detallada sobre el mismo, este enfoque nos proporcionaria una manera más rápida y sencilla de examinar el tráfico de red en busca de patrones específicos o problemas potenciales, pero que en este caso nos bota un error ya que wireshark no se encuentra en el sistema de mi navegador.

## PROBLEMA 3: Simulación de ataque y respuesta

### Escenario:

Eres el administrador de seguridad de una red corporativa y has notado unaumento en el tráfico ARP anómalo. Sospechas que esto podría ser parte de un ataque deARP spoofing, donde un atacante podría estar intentando interceptar la comunicación entredos partes para robar o modificar datos transmitidos.
### preguntas:

**1. Describe cómo identificarías si estas transmisiones ARP son realmente maliciosas.**

**2. ¿Qué medidas tomarías para mitigar el ataque una vez confirmado?**

**3. Explica cómo un switch y un firewall pueden configurarse para prevenir futurosataques de este tipo.**

- **Switch:** Se utiliza la función de ARP spoofing prevention que es una de las funciones que controla el acceso a la red basándose en su dirección Mac o su identificación en la red (Puerto, IP y dirección MAC).

  - **Pasos para configurar la prevención de ARP Spoofing en un switch**:

1. Acceder a la interfaz web del switch utilizando un navegador y colocando la dirección IP donde por defecto suele ser **10.90.90.90**.
2. Ingresar a la configuración del switch y navegar a la sección de **Seguridad**.
3. Buscar la opción de **ARP Spoofing Prevention**.
4. Configurar los siguientes parámetros:
  - **Dirección IP**: La dirección IP de tu **gateway**, **router** o **firewall**.
  - **Dirección MAC**: La dirección MAC LAN de tu **gateway**, **router** o **firewall**.
  - **Puertos**: Indica el puerto donde está conectado tu **gateway**, **router** o **firewall**.
5. Agregar la prevención a la tabla ARP y guardar la configuración.

- **Firewall:** Se utiliza ARP inspection para que verifique los paquetes ARP que los compara con las entradas en la tabla ARP, además, también se puede utilizar Dynamic ARP inspection que es donde interpreta todas las solicitudes y respuestas del ARP para asegurarse que solo ingresen las solicitudes y respuestas validas.

- **Configuración en el Firewall**:
  1. Acceder a la configuración del firewall.
  2. Habilitar **ARP Inspection**.
  3. Verificar que las entradas en la tabla ARP estén actualizadas y sean correctas.
  4. Considerar también de configurar **IP Source Guard** para proteger contra ataques de spoofing que se pueden dar hasta en empresas.
  
**4. Formula un plan para educar a los empleados sobre medidas de seguridad quepueden tomar para reducir el riesgo de ataques futuros.**

- Para tu presentación y código a presentar puedes utilizar:

##### Requisitos:

1. Detección de ARP Spoofing: Implementar un sistema de detección para identificarposibles ataques.
2. Mitigación del Ataque: Desarrollar un método para mitigar o detener el ataque unavez detectado.
3. Automatización y Monitorización: Usar Python para automatizar la detección yrespuesta, y monitorear continuamente la red para futuros ataques.
4. Educación de Empleados: Proporcionar un plan para educar a los empleados sobrecómo pueden ayudar a reducir el riesgo de futuros ataques.

#### Parte 1: Detección de ARP Spoofing con Python

##### Código python:

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

**Diferencias entre red P2P y red cliente-servidor en términos de diseño de red y topología**:

   - **Red P2P (Peer-to-Peer)**: En una red P2P, los nodos actúan tanto como clientes como servidores, lo que significa que cada nodo tiene la capacidad de solicitar y proporcionar recursos. No hay un servidor centralizado, en su lugar, todos los nodos son iguales y se comunican directamente entre sí. La topología de red suele ser más distribuida y descentralizada, lo que permite una mayor resistencia a fallas y una escalabilidad más fácil. La redundancia de datos y la tolerancia a fallos suelen ser más altas en este tipo de red.

   - **Red cliente-servidor**: En una red cliente-servidor, hay un servidor central que actúa como punto focal para el intercambio de recursos. Los clientes solicitan recursos al servidor, que los proporciona. La topología de red es más centralizada, lo que puede resultar en un único punto de fallo y problemas de escalabilidad si el servidor no puede manejar todas las solicitudes de los clientes.

**2. ¿Qué protocolos específicos usarías para gestionar las comunicaciones y elintercambio de archivos en esta red?**

- **Protocolos específicos para gestionar las comunicaciones y el intercambio de archivos en la red P2P**:

   - **Protocolo BitTorrent**: Es un protocolo P2P popular para compartir archivos de forma descentralizada. Permite la distribución eficiente de archivos divididos en fragmentos entre los nodos de la red.
   
   - **Protocolo Kademlia**: Utilizado para construir redes P2P descentralizadas, como en el caso de sistemas de almacenamiento distribuido como IPFS (InterPlanetary File System). Ayuda en la localización eficiente de nodos y recursos en la red.
   
   - **Protocolo de Seguridad SSL/TLS**: Para garantizar la seguridad de las comunicaciones entre nodos, se puede implementar SSL/TLS para cifrar y autenticar las conexiones.
     
**3. Analiza los posibles problemas de seguridad asociados con una red P2P y proponesoluciones para mitigar estos riesgos.**

- **Posibles problemas de seguridad y soluciones para mitigar riesgos en una red P2P**:

   - **Acceso no autorizado**: Implementar un sistema de autenticación robusto para garantizar que solo los usuarios autorizados puedan acceder a los recursos compartidos.
   
   - **Integridad de datos**: Utilizar firmas digitales para verificar la integridad de los archivos compartidos y evitar la manipulación no autorizada de los mismos.
   
   - **Malware y software malicioso**: Implementar medidas de detección y prevención de malware, como escaneo de archivos en busca de virus y limitación de tipos de archivos permitidos en la red.
   
   - **Ataques de denegación de servicio (DDoS)**: Implementar mecanismos de mitigación de DDoS, como limitación de la velocidad de transferencia por nodo o la implementación de listas blancas y negras de direcciones IP.

**4. Evalúa el impacto de incorporar nodos que actúan tanto como clientes comoservidores. ¿Cómo gestionarías el balanceo de carga?**

 - **Impacto de incorporar nodos que actúan tanto como clientes como servidores y gestión del balanceo de carga**:

   - La inclusión de nodos que actúan como clientes y servidores aumenta la eficiencia de la red al distribuir la carga entre los nodos disponibles.
   
   - Se puede implementar un algoritmo de balanceo de carga que distribuya las solicitudes de recursos de manera equitativa entre los nodos disponibles, teniendo en cuenta factores como la capacidad de procesamiento y la carga actual de cada nodo.
   
   - Además, se pueden establecer políticas de prioridad para determinar qué nodos tienen preferencia para actuar como servidores en función de su disponibilidad y recursos disponibles. Esto ayudará a optimizar el rendimiento de la red P2P.

- *Para tu presentación y código a presentar puedes utilizar:*

#### Requisitos:

1. Implementación de la Red P2P: Desarrollar un modelo de red P2P utilizando Pythonque permita a los nodos unirse, compartir recursos y desconectarse de maneradinámica.
2. Gestión de Recursos y Distribución de Carga: Asegurar que los recursos secompartan de manera eficiente y que la carga se distribuya equitativamente entre losnodos.
3. Seguridad: Implementar mecanismos de seguridad para autenticar a los usuarios ycifrar los intercambios de archivos.
4. Automatización y Simulación: Utilizar Python para simular el comportamiento de lared y automatizar tareas comunes de gestión de la red

#### Parte 1: Implementación de la Red P2P con python
##### Codigo de python:
````
 import socket
 import threading
 class Peer:
 def __init__(self, host, port):
   self.host = host
   self.port = port
   self.peers = [] # List to keep track of peers
   self.server = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
   self.server.bind((self.host, self.port))
   self.server.listen(5)
   print(f"Node started on {self.host}:{self.port}")
   threading.Thread(target=self.accept_connections).start()
  def accept_connections(self):
     while True:
       client, address = self.server.accept()
       print(f"Connected with {address[0]}:{address[1]}")
       self.peers.append(client)
       threading.Thread(target=self.handle_client, args=(client,)).start()
   def handle_client(self, client):
     while True:
       try:
           data = client.recv(1024)
           if data:
               print(f"Received: {data.decode()}")
               self.broadcast_data(data, client)
   except Exception as e:
       print(f"Error: {e}")
       client.close()
       break
  def broadcast_data(self, data, sender):
   for peer in self.peers:
       if peer is not sender:
          peer.send(data)
  def connect_to_peer(self, host, port):
 client = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
 client.connect((host, port))
 self.peers.append(client)
 print(f"Connected to peer at {host}:{port}")
 # ejemplos de uso
 node = Peer('127.0.0.1', 5000)
 node.connect_to_peer('127.0.0.1', 6000)
````
#### Resultados:
````
````
#### Parte 2: Gestión de recursos y distribución de carga

- *Estrategias de equilibrio de carga:*

- **Implementar un algoritmo que asigne más carga a los nodos con más recursosdisponibles.**

- **Usar un algoritmo round-robin para asegurar que todos los nodos compartan demanera equitativa la carga de trabajo.**

#### Parte 3: Seguridad en la Red P2P

##### Código python:

````
 import hashlib
 import os
 def generate_key(password):
 salt = os.urandom(16)
 key = hashlib.pbkdf2_hmac('sha256', password.encode('utf-8'), salt, 100000)
 return salt + key
 def verify_key(stored_key, provided_password):
 salt = stored_key[:16]
 key = stored_key[16:]
 new_key =hashlib.pbkdf2_hmac('sha256', provided_password.encode('utf-8'), salt,
 100000)
 return new_key == key
 password = "secure_password"
 key = generate_key(password)
 print("Key generated successfully.")
 print("Verification:", verify_key(key, password)
 import time
 def monitor_peers(peers):
 while True:
 for peer in peers:
 try:
 peer.send(b'ping')
 response = peer.recv(1024)
 if response != b'pong':
 raise Exception("Peer is not responding correctly.")
 except Exception as e:
 print(f"Peer {peer.getpeername()} failed: {e}")
 peers.remove(peer)
 time.sleep(60) # Check every minute
 # In the Peer class, handle 'ping' messages
 def handle_client(self, client):
 while True:
 try:
 data = client.recv(1024)
 if data:
 if data == b'ping':
 client.send(b'pong')
 else:
 print(f"Received: {data.decode()}")
 self.broadcast_data(data, client)
 except Exception as e:
 print(f"Error: {e}")
 client.close()
 break
````
