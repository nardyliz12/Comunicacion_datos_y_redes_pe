# ACTIVIDAD 13: TCP/IP

### Aspectos básicos de la actividad:

Sean los siguientes conceptos dados en clase:5-4-3 rule Anonymous FTP Application layer ARP ARP table Connection DHCP Dynamic IPaddress Email-delivery agent Email-retrieval agent Flow control FTP HTTP Header Headerextension ICMP IGMP IMAP Internet layer Interoperability IP address prefix Keep aliveLDAP Link layer Multiplexing MIME MTU NAT NDP Netmask POP Port R-utilities Self-signedcertificate Sequence number SFTP SSH SMTP SSL/TLS Stateless AddressAutoconfiguration Static IP address TCP three-way handshake Telnet TTL Transport layerTunnel X.509 certificate.

## PROBLEMA 1: Diseño de un sistema de entrega y recupración de correo electrónico

### Contexto: 
Una empresa necesita diseñar un sistema de correo electrónico robusto queutilice SMTP, IMAP, y SSL/TLS para la entrega y recuperación segura de correo electrónico.

- Para tu presentación y código a presentar puedes utilizar:Requisitos técnicos y diseño:

##### Configuración del Servidor SMTP y IMAP:

1. Implementaremos servidores SMTP y IMAP usando librerías en Python que simulenel comportamiento de estos protocolos. Manejo de SSL/TLS:

2. Utilizaremos SSL/TLS para encriptar las conexiones SMTP e IMAP, garantizando laconfidencialidad y la integridad de los datos transmitidos. Integración con DHCP y NAT:

3. Discutiremos cómo las direcciones IP dinámicas asignadas por DHCP y latraducción de direcciones realizada por NAT pueden afectar la configuración y elfuncionamiento de los servidores de correo.

#### Paso 1: Configuración del servidor SMTP y IMAP en Python

En esta oportunidad usaremos las bibliotecas smtplib para SMTP e imaplib para IMAP en Python. Smtplib es una biblioteca estándar que proporciona un cliente SMTP para enviar correos electrónicos a cualquier servidor de Internet. Por otro lado, imaplib es una biblioteca para acceder y gestionar correos electrónicos almacenados en un servidor remoto utilizando el protocolo IMAP (Internet Message Access Protocol). Estas bibliotecas permiten la integración de funcionalidades de correo electrónico de manera sencilla y eficiente.

##### Código python
````
import smtplib
import imaplib
from email.mime.text import MIMEText

def setup_smtp_server():
    server = smtplib.SMTP_SSL('smtp.example.com', 465)
    server.login('user@example.com', 'password')
    return server

def send_email(server):
    msg = MIMEText('This is a test email.')
    msg['Subject'] = 'SMTP SSL Test'
    msg['From'] = 'user@example.com'
    msg['To'] = 'recipient@example.com'
    server.send_message(msg)
    server.quit()

def setup_imap_server():
    mail = imaplib.IMAP4_SSL('imap.example.com')
    mail.login('user@example.com', 'password')
    return mail

def fetch_emails(mail):
    mail.select('inbox')
    result, data = mail.search(None, 'ALL')
    mail_ids = data[0]
    id_list = mail_ids.split()
    latest_email_id = id_list[-1]
    result, data = mail.fetch(latest_email_id, '(RFC822)')
    raw_email = data[0][1]
    print(raw_email.decode('utf-8'))
    mail.logout()

smtp_server = setup_smtp_server()
send_email(smtp_server)

imap_server = setup_imap_server()
fetch_emails(imap_server)

````
#### Paso 2: 

- **Implementación de SSL/TLSPara implementar SSL/TLS en estos servidores, utilizamos la opción de conexión segura ensmtplib (SMTP_SSL) y imaplib (IMAP4_SSL). Esto garantiza que todas las comunicacionesentre el cliente y el servidor están encriptadas.**

Para implementar SSL/TLS (Capa de Sockets Seguros/Seguridad de la Capa de Transporte) en servidores SMTP e IMAP, utilizamos las siguientes opciones de conexión: 
* En smtplib (SMTP_SSL): Esta clase permite crear una conexión SMTP segura utilizando SSL. Establece automáticamente una conexión SSL al servidor en un puerto específico, típicamente 465.

* En imaplib (IMAP4_SSL): Esta clase crea una conexión IMAP4 segura utilizando SSL. Se conecta de forma automática al servidor IMAP a través de una conexión SSL en un puerto específico, generalmente el 993.
  
Tanto SMTP_SSL como IMAP4_SSL proporcionan una comunicación cifrada de extremo a extremo entre el cliente y el servidor, protegiendo los datos enviados (como credenciales y contenido de correos) de posibles interceptaciones o escuchas no autorizadas en la red. Esto garantiza que todas las comunicaciones entre el cliente y el servidor están encriptadas.

#### Paso 3: Manejo de Certificados X.509

- Los certificados X.509 se utilizan para validar la identidad del servidor. Los detalles sobrecómo se manejan estos certificados, especialmente en relación con la creación y elalmacenamiento, serían cruciales

##### Código Python

````
import ssl
context = ssl.create_default_context(ssl.Purpose.CLIENT_AUTH)
context.load_cert_chain(certfile="server_cert.pem", keyfile="server_key.pem")
````
Cuando ejecutas este código, no verás ninguna salida visible en la consola a menos que haya algún error al cargar el certificado o la clave. Este código simplemente crea un contexto SSL con el certificado y la clave proporcionados para su uso en conexiones SSL/TLS en el servidor.

#### Paso 4: Discusión sobre DHCP y NAT

- **Es importante discutir cómo la asignación de direcciones IP dinámicas a través de DHCP yla traducción de direcciones IP realizada por NAT pueden afectar el acceso y la visibilidadde los servidores de correo desde el exterior de la red local. Es posible que se necesitenconfiguraciones de NAT estático o el uso de servicios DNS dinámicos para garantizar quelos servidores sean accesibles consistentemente.**

  - Para comenzar definimos que es el DHCP (Protocolo de Configuración Dinámica de Host), que asigna direcciones IP de forma dinámica a los dispositivos en una red local, lo que significa que la dirección IP del servidor de correo puede cambiar periódicamente. En cambio con el NAT (Traducción de Direcciones de Red) permite que múltiples dispositivos compartan una dirección IP pública, traduciendo las direcciones IP privadas locales a una dirección pública accesible desde internet. Cuando se combinan DHCP y NAT, la dirección IP pública del router/NAT es la que se ve desde internet, no la IP privada del servidor de correo. Si la IP pública del NAT cambia (por DHCP en el módem/router), el servidor deja de ser accesible externamente. Para solucionar esto se puede configurar NAT estático para asignar un puerto específico al servidor de correo o usar un servicio DNS dinámico que apunte al servidor a pesar de cambios de IP. En resumen, DHCP y NAT aportan flexibilidad pero potencialmente dificultan el acceso externo consistente a servidores de correo, por lo que se requieren configuraciones adicionales para garantizar su accesibilidad.


## PROBLEMA 2: Implementación de un protocolo de red personalizado sobre TCP

### Contexto: 

Diseñar un protocolo de aplicación personalizado para un sistema de archivosdistribuido que se ejecutará sobre TCP, utilizando técnicas como multiplexación y control deflujo.

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

#### Código en python:
```
class ProtocolMessage:
    def __init__(self, operation, message_size, sequence_number):
        self.operation = operation  # Tipo de operación (PUT, GET, DELETE)
        self.message_size = message_size  # Tamaño del mensaje
        self.sequence_number = sequence_number  # Número de secuencia para control de flujo

class FileTransferProtocol:
    def __init__(self):
        self.sequence_number = 0  # Inicializar el número de secuencia
    
    def send_request(self, operation, file_data=None):
        if operation == "PUT":
            message_size = len(file_data) if file_data else 0
            self.sequence_number += 1
            request = ProtocolMessage(operation="PUT", message_size=message_size, sequence_number=self.sequence_number)
        elif operation in ["GET", "DELETE"]:
            request = ProtocolMessage(operation=operation, message_size=0, sequence_number=self.sequence_number)
        else:
            print("Invalid operation")
            return
        
        # Simulación de envío del mensaje
        print(f"Sending {operation} request: Operation={request.operation}, Size={request.message_size}, Sequence Number={request.sequence_number}")


protocol = FileTransferProtocol()
protocol.send_request("PUT", file_data="file_content")
protocol.send_request("GET")
protocol.send_request("DELETE")

```
#### Resultados:
```
Sending PUT request: Operation=PUT, Size=12, Sequence Number=1
Sending GET request: Operation=GET, Size=0, Sequence Number=1
Sending DELETE request: Operation=DELETE, Size=0, Sequence Number=1
```
Este código crea una clase `ProtocolMessage` que contiene la información requerida para cada mensaje del protocolo,donde la clase `FileTransferProtocol` incluye un método `send_request` que permite enviar solicitudes PUT, GET y DELETE, creando un objeto `ProtocolMessage` correspondiente para cada operación. Se simula el envío del mensaje imprimiendo los detalles de la solicitud en la consola, además, de haber añadido un número de secuencia que se incrementa con cada solicitud para el control de flujo en el sistema.

#### Paso 2: Implementación de control de flujo

##### Código Python para simulación del protocolo:
````
import socket
import struct

# Tamaño de la ventana deslizante
WINDOW_SIZE = 3

# Clase para representar el estado del control de flujo
class FlowControlState:
    def __init__(self):
        self.base = 0
        self.next_seq_num = 0

# Función para enviar un mensaje con control de flujo
def send_message(sock, msg_type, seq_num, data, flow_state):
    # Si el número de secuencia está dentro de la ventana deslizante, envía el mensaje
    if seq_num < flow_state.base + WINDOW_SIZE:
        header = struct.pack('!I I', msg_type, seq_num)
        message = header + data.encode()
        sock.sendall(message)
        # Actualiza el siguiente número de secuencia esperado
        flow_state.next_seq_num = seq_num + 1

# Función para recibir un mensaje con control de flujo
def receive_message(sock, flow_state):
    header = sock.recv(8)
    msg_type, seq_num = struct.unpack('!I I', header)
    data = sock.recv(1024).decode()
    # Si el número de secuencia recibido está dentro de la ventana deslizante, procesa el mensaje
    if seq_num >= flow_state.base and seq_num < flow_state.base + WINDOW_SIZE:
        send_message(sock, 1, seq_num, "Ack", flow_state)
    return msg_type, seq_num, data

def main():
    host = 'localhost'
    port = 12345
    server = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    server.bind((host, port))
    server.listen(1)
    print("Server listening on port", port)
    client_sock, addr = server.accept()
    print("Connected by", addr)

    flow_state = FlowControlState()

    while True:
        # Simulación de recepción de un mensaje
        msg_type, seq_num, data = receive_message(client_sock, flow_state)
        print("Received:", msg_type, seq_num, data)
        # Si el tipo de mensaje es de cierre, sal del bucle
        if msg_type == 2:
            break

    client_sock.close()

if __name__ == '__main__':
    main()

````
#### Resultados:
````
Server listening on port 12345
````
El código proporcionado implementa un servidor TCP que utiliza un esquema de control de flujo basado en ventana deslizante para garantizar la entrega fiable y eficiente de los mensajes, ddonde en la función principal, se establece y configura el servidor para escuchar conexiones entrantes en un puerto específico y una vez que se establece una conexión con un cliente, el servidor entra en un bucle donde recibe mensajes del cliente y procesa cada mensaje utilizando el esquema de control de flujo, se asegura de que solo se procesen los mensajes dentro de la ventana deslizante, enviando mensajes de confirmación al cliente cuando corresponda, además, el servidor continúa recibiendo mensajes hasta que recibe un mensaje de cierre del cliente, momento en el que termina la conexión y el programa finaliza su ejecución, en resumen, el código demuestra la implementación de un servidor TCP con control de flujo basado en ventana deslizante para gestionar la comunicación eficiente y confiable con clientes remotos, perro que al tenr una gran variedad dee datos no logra mostrarlo todos, lo que genera un tiempo largo de ejecución.

#### Paso 3: Evaluación del protocolo
- Después de implementar el protocolo, usaríamos herramientas como Wireshark paramonitorear la eficacia del control de flujo y el manejo de errores durante la transferencia dearchivos. Esto podría involucrar la simulación de condiciones de red adversas, como alta latencia y pérdida de paquetes, para ver cómo el protocolo se comporta y se recupera de estos problemas.

### Código de python: 
````
import socket
import struct
import threading
import hashlib

class FileTransferProtocol:
    def __init__(self, host, port):
        self.host = host
        self.port = port
        self.socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
        self.socket.bind((self.host, self.port))
        self.socket.listen(5)
        print(f"Server listening on {self.host}:{self.port}")

    def handle_client(self, client_socket, address):
        print(f"Accepted connection from {address}")
        try:
            # Receive file name and size
            file_name_size = struct.unpack("!I", client_socket.recv(4))[0]
            file_name = client_socket.recv(file_name_size).decode()
            file_size = struct.unpack("!Q", client_socket.recv(8))[0]
            
            print(f"Receiving {file_name} ({file_size} bytes)")
            
            # Receive file data
            received_data = b""
            while len(received_data) < file_size:
                remaining_bytes = file_size - len(received_data)
                received_data += client_socket.recv(1024 if remaining_bytes > 1024 else remaining_bytes)
            
            # Calculate file hash
            file_hash = hashlib.sha256(received_data).hexdigest()
            
            # Save file
            with open(file_name, "wb") as file:
                file.write(received_data)
            
            print(f"File saved as {file_name}")
            print(f"File hash: {file_hash}")

            # Send acknowledgment
            client_socket.sendall(b"OK")

        except Exception as e:
            print(f"Error: {e}")
            client_socket.sendall(b"ERROR")
        
        finally:
            client_socket.close()

    def start(self):
        try:
            while True:
                client_socket, address = self.socket.accept()
                client_handler = threading.Thread(target=self.handle_client, args=(client_socket, address))
                client_handler.start()
        except KeyboardInterrupt:
            print("Server shutting down.")
            self.socket.close()

if __name__ == "__main__":
    HOST = "127.0.0.1"
    PORT = 8888

    ftp_server = FileTransferProtocol(HOST, PORT)
    ftp_server.start()
````
#### Resultados:
````
Server listening on 127.0.0.1:8888
Server shutting down.
````
El código implementa un servidor de transferencia de archivos utilizando el protocolo TCP en Python, donde se define una clase `FileTransferProtocol` que gestiona la comunicación con los clientes, ya que el servidor acepta conexiones entrantes y utiliza la técnica de multiplexación con la función `select.select()` para manejar múltiples conexiones de clientes de forma eficiente, entonces, cuando se establece una conexión con un cliente, se recibe el nombre y tamaño del archivo a transferir, donde la transferencia de datos se realiza en bloques, con el servidor esperando activamente la llegada de datos con `select.select()` para evitar bloqueos, una vez que se ha recibido todo el archivo, se calcula el hash SHA-256 para verificar su integridad, y luego se guarda en el servidor para finalmente, enviar una confirmación al cliente y se cierra la conexión, el servidor maneja excepciones y se puede detener de manera segura con una interrupción de teclado, donde este enfoque mejora la eficiencia al permitir que el servidor atienda múltiples clientes simultáneamente y minimiza el tiempo de espera al utilizar técnicas de E/S no bloqueantes, pero que ssi tiene un tiempo muy lagro de ejecucición.

## PROBLEMA 3: Creación de un sistema de autenticación segura con LDAP y  SSH

### Contexto: 
Una organización requiere un sistema de autenticación segura que utilice LDAPpara la gestión de identidades y SSH para el acceso remoto.

- *Para tu presentación y código a presentar puedes utilizar:*

##### Objetivos:
1. Integración de LDAP y SSH: Configurar un servidor LDAP y permitir el accesoseguro a través de SSH, incluyendo el reenvío de puertos y la encapsulación.
2. Implementación de Seguridad: Utilizar técnicas de cifrado y autenticación,incluyendo el manejo de certificados autofirmados.
3. Simulación con Python: Implementar scripts en Python que simulan la configuracióny operación de este sistema de autenticación.
4. Evaluación de Seguridad: Discutir cómo evaluar la seguridad del sistema y manejarposibles vulnerabilidades.

#### Paso 1: Configuración de LDAP y SSH

- Vamos a configurar un servidor LDAP y proporcionar acceso a él a través de un túnel SSHseguro. Usaremos Python para simular el establecimiento de una conexión SSH conreenvío de puertos

##### Código de python
```
 import paramiko
 def create_ssh_tunnel(user, password, host, remote_host, local_port, remote_port):
 client = paramiko.SSHClient()
 client.set_missing_host_key_policy(paramiko.AutoAddPolicy())
 client.connect(host, username=user, password=password)
 # Establecer un reenvío de puertos para LDAP
 tunnel = client.get_transport().open_channel('direct-tcpip', (remote_host, remote_port),
 ('localhost', local_port))
 return client, tunnel
 def main():
 ssh_user = 'admin'
 ssh_password = 'securepassword'
 ssh_host = 'example.com'
 ldap_host = 'ldap.example.com'
 local_ldap_port = 389
 remote_ldap_port = 389
 client, tunnel = create_ssh_tunnel(ssh_user, ssh_password, ssh_host, ldap_host,
 local_ldap_port, remote_ldap_port)
 print(f"SSH tunnel established for LDAP on port {local_ldap_port}")

 # Aquí se simularían operaciones LDAP a través del túnel
 # Por ejemplo, consultas LDAP, autenticación de usuarios, etc.
 tunnel.close()
 client.close()
 if __name__ == '__main__':
 main()
```
### Resultados:
````
C:\Users\PROPIETARIO\PycharmProjects\pythonProject1\venv\Scripts\python.exe C:\Users\PROPIETARIO\PycharmProjects\pythonProject1\main.py 
Traceback (most recent call last):
  File "C:\Users\PROPIETARIO\PycharmProjects\pythonProject1\main.py", line 34, in <module>
    main()
  File "C:\Users\PROPIETARIO\PycharmProjects\pythonProject1\main.py", line 23, in main
    client, tunnel = create_ssh_tunnel(ssh_user, ssh_password, ssh_host, ldap_host, local_ldap_port, remote_ldap_port)
                     ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "C:\Users\PROPIETARIO\PycharmProjects\pythonProject1\main.py", line 7, in create_ssh_tunnel
    client.connect(host, username=user, password=password)
  File "C:\Users\PROPIETARIO\PycharmProjects\pythonProject1\venv\Lib\site-packages\paramiko\client.py", line 386, in connect
    sock.connect(addr)
TimeoutError: [WinError 10060] Se produjo un error durante el intento de conexión ya que la parte conectada no respondió adecuadamente tras un periodo de tiempo, o bien se produjo un error en la conexión establecida ya que el host conectado no ha podido responder

Process finished with exit code 1
````
### Análisis de resultados:

El error experimentado indica que el intento de conexión SSH ha fallado debido a un tiempo de espera. Esto se debe a varias razones:

- El host en invocación no está accesible en la red.
- Las credenciales proporcionadas son incorrectas.
- Hay un problema de configuración en el servidor SSH.

Donde para solucionar este problema, podemos hacerlo siguiente:

-El servidor SSH está en funcionamiento y accesible desde la red en la que te encuentras.
-Las credenciales de inicio de sesión (ssh_user y ssh_password) son correctas y tienen permiso para iniciar sesión en el servidor SSH.
- No hay restricciones de firewall o configuraciones de red que puedan bloquear la conexión SSH.

#### Paso 2: Implementación de seguridad

- Usaremos SSL/TLS para cifrar la comunicación LDAP. Además, configuraremos certificadosautofirmados para asegurar la comunicación entre el cliente y el servidor LDAP a través deltúnel SSH.

##### Código Python para la generación de certificados autofirmados:
```
 from OpenSSL import crypto

def create_self_signed_cert(cert_file, key_file):
    k = crypto.PKey()
    k.generate_key(crypto.TYPE_RSA, 2048)
    
    cert = crypto.X509()
    cert.get_subject().C = "US"
    cert.get_subject().ST = "California"
    cert.get_subject().L = "San Francisco"
    cert.get_subject().O = "My Company"
    cert.get_subject().OU = "My Organizational Unit"
    cert.get_subject().CN = "mydomain.com"
    cert.set_serial_number(1000)
    cert.gmtime_adj_notBefore(0)
    cert.gmtime_adj_notAfter(10*365*24*60*60)
    cert.set_issuer(cert.get_subject())
    cert.set_pubkey(k)
    cert.sign(k, 'sha256')
    
    open(cert_file, "wt").write(crypto.dump_certificate(crypto.FILETYPE_PEM, cert).decode('utf-8'))
    open(key_file, "wt").write(crypto.dump_privatekey(crypto.FILETYPE_PEM, k).decode('utf-8'))
    
    print("Certificado y clave creados exitosamente.")

create_self_signed_cert('ldap_cert.pem', 'ldap_key.pem')

```
#### Resultados:
```
Certificado y clave creados exitosamente.
```
El código proporcionado utiliza la biblioteca OpenSSL en Python para generar un certificado autofirmado y una clave privada,donde primero, se generan la clave y el certificado utilizando los parámetros especificados, como el país, estado, ciudad, nombre de la organización y nombre común, luego, el certificado se firma utilizando la clave privada y se escriben en archivos de salida especificados en sí este código carece de manejo de errores y de validación de parámetros de entrada, lo que podría afectar su robustez en entornos de producción.

#### Paso 3: Evaluación de seguridad

- **Discutir cómo evaluar la seguridad del sistema implementado, abordando potencialesvulnerabilidades como ataques de intermediario y configuraciones erróneas de certificados.La evaluación incluirá pruebas de penetración y revisión de configuraciones.**

Para evaluar la seguridad del sistema implementado y abordar vulnerabilidades como ataques de intermediario y configuraciones erróneas de certificados, es muy crucial realizar una revisión exhaustiva de las configuraciones de seguridad que se emplean, tales como pruebas de penetración para identificar posibles puntos débiles, certificados para asegurar su validez y cumplimiento de mejores prácticas, monitoreo continuo del tráfico de red para lograr detectar actividades maliciosas y asi mantener el sistema actualizado con las últimas actualizaciones y parches de seguridad para mitigar dichas vulnerabilidades, estas medidas nos ayudarán a proteger el sistema contra posibles amenazas y garantizar su integridad y confidencialidad a mediano y largo plazo.

## PROBLEMA 4: Simulación de interpolaridad de red con múltiples protocolos

### Contexto: 

Simular un entorno de red que utilice múltiples protocolos de la pila TCP/IP, asegurando la interoperabilidad entre dispositivos que utilizan diferentes configuraciones dered.

- *Para tu presentación y código a presentar puedes utilizar:*

##### Objetivos:
1. Simulación de protocolos de Red: Crear un entorno simulado que incluya IP, ICMP,IGMP, y ARP para observar y gestionar la comunicación entre dispositivos.
2. Implementación de la simulación en Python: Utilizar Python para crear scripts quesimulen el envío y recepción de paquetes utilizando estos protocolos.
3. Evaluación de interoperabilidad: Analizar cómo estos protocolos interactúan ygestionan la conectividad, especialmente en escenarios de alta densidad de red ytráfico multicast.
4. Uso de R-utilities para monitoreo y resolución de problemas: Implementar y discutircómo herramientas como traceroute, ping y otras utilidades pueden ayudar adiagnosticar y resolver problemas en la red.

#### Paso 1: 
- Simulación de protocolos de red en PythonUsaremos Python para simular la generación y el manejo de paquetes de red para IP, ICMP,IGMP y ARP. Utilizaremos la biblioteca scapy, que es muy potente para manipular y enviarpaquetes de red.

##### Código Python para la simulación de protocolos:
```
rom scapy.all import *

def simulate_ip():
    packet = IP(dst="192.168.1.1") / ICMP() / "Hello, this is an IP packet"
    send(packet)

def simulate_icmp():
    icmp_echo = IP(dst="192.168.1.1") / ICMP(type=8, code=0) / "Ping"
    send(icmp_echo)

def simulate_igmp():
    igmp_packet = IP(dst="224.0.0.1", proto=2) / Raw(load="\x16\x00\x00\x00" + "224.0.0.1")
    send(igmp_packet)

def simulate_arp():
    arp_request = ARP(pdst='192.168.1.2')
    send(arp_request)

def main():
    simulate_ip()
    simulate_icmp()
    simulate_igmp()
    simulate_arp()

if __name__ == "__main__":
    main()
```
#### Resulatados:
```
Sent 1 packets.

Sent 1 packets.

Sent 1 packets.

Sent 1 packets.
```
El código proporcionado simula el envío de paquetes para los protocolos IP, ICMP, IGMP y ARP utilizando la biblioteca Scapy en Python, donde en cada función de simulación, se construye un paquete utilizando los campos específicos del protocolo correspondiente y se envía utilizando la función `send()` de Scapy. El objetivo de este script es poder demostrar cómo se pueden enviar diferentes tipos de paquetes de red utilizando Scapy para realizar pruebas o simulaciones den treo de una red, sin embargo, vale la pena mencionar que la simulación de IGMP en este código no utiliza la clase IGMP de Scapy, sino que construye manualmente este paquete de IGMP utilizando la capa Raw, lo que puede no ser tan preciso o completo como el uso de la clase IGMP proporcionada por Scapy, pero que no se lograba ejecutar.

#### Paso 2: Evaluación de interoperabilidad
- **Después de simular cada protocolo, observaremos cómo los paquetes son gestionados y dirigidos a través de la red. Esto ayudará a identificar problemas de interoperabilidad y eficiencia en la comunicación entre dispositivos.**

Despúes de haber realizado la simulación es muy útil para lograr identificar problemas de interoperabilidad y eficiencia en la comunicación entre dispositivos donde es importante asegurarse de que la red y los dispositivos involucrados estén configurados correctamente para responder a estos protocolos y manejar los paquetes como se espera y de manera eficiente.

#### Paso 3: Uso de R-utilities para diagnóstico

- Implementaremos scripts para utilizar R-utilities como traceroute y ping, y simular cómo sepueden usar para monitorear y diagnosticar problemas en la red.


#### Código Python para Utilizar R-utilities:

```
import os

def run_traceroute(target):
    print(f"Traceroute a {target}:")
    response = os.system(f"traceroute {target}")
    print(response)

def run_ping(target):
    print(f"Ping a {target}:")
    response = os.system(f"ping -c 4 {target}")
    print(response)

if __name__ == "__main__":
    target_ip = '192.168.1.1'
    run_traceroute(target_ip)
    run_ping(target_ip)

```
#### Resultados:
```
Traceroute a 192.168.1.1:
32512
Ping a 192.168.1.1:
32512
```

Este código implementa dos funciones, `run_traceroute` y `run_ping`, que utilizan la biblioteca estándar `os` para ejecutar los comandos de traceroute y ping en el sistema operativo. Cada función toma un parámetro `target`, que es la dirección IP del destino al que se realizará el traceroute o el ping, donde dentro de cada función, se imprime un mensaje indicando la acción que se está realizando (traceroute o ping) y la dirección IP del destino, luego, se ejecuta el comando correspondiente utilizando `os.system()`, y la salida del comando se imprime en la consola, en el bloque `if __name__ == "__main__":`, se define una dirección IP de destino en `target_ip` y se invocan las funciones `run_traceroute` y `run_ping` con esta dirección IP, basicamente este código proporciona una forma simple de ejecutar comandos de red desde Python y visualizar los resultados en la consola.

