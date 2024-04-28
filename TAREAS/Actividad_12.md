# ACTIVIDAD 12: Construyendo una área de red local

##### Aspectos básicos de la actividad

Sean los siguientes conceptos dados en clase: 5-4-3 rule Ad hoc wireless network Association Autonegotiation Band Basic service setBSSID Cellular network Chips Co-channel interference Contention-free period Coveragearea Crossover cable Cross-talk CSMA/CA CSMA/CD Distribution system DSSS Dumbterminal ESSID Ethernet repeater Extended service set EUI-48 EUI-64 Fast Ethernet FHSSFlooding Full-duplex mode Gigabit Ethernet Half-duplex mode Hotspot Independent basicservice set IEEE standards Initialization vector Jam signal LAN edge MAC table MetroEthernet MICHAEL MIMO-OFDM Modulation OFDM Power over Ethernet ProbePseudonoise RJ45 jack Roaming SIM card Simplex mode SSID T-connector TerminatorThickNet Thinnet TKIP Trunk UTP VLAN VPN WAP WEP Wireless ad hoc network WLANWLAN frame WNIC WPA WPA2 XOR.

## PROBLEMA 1: Diseño y Simulación de una red metro Ethernet con QoS

### Contexto: 

Una empresa necesita diseñar una red Metro Ethernet para conectar varias sucursales en una área metropolitana. Se requiere calidad de servicio (QoS) para priorizarel tráfico de voz sobre IP (VoIP) sobre el tráfico regular de datos.

#### Requisitos:

● **Explique cómo utilizaría VLAN y Trunk para segmentar y gestionar el tráfico en la red.**

Los VLANs (Virtual Local Area Networks) se pueden utilizar para segmentar la red en grupos más pequeños, independientes y administrables, por ejemplo: podriamos tener una VLAN para cada sucursal dentro de la empresa, donde esto no solo mejora la seguridad, sino que también ayuda a reducir el tráfico de la red al limitar las transmisiones de broadcast a su propia VLAN. Mientras tanto el Truking es una técnica que se utiliza para llevar el tráfico de varias VLANs a través  de un solo enlace físico (Trunk). Si hacemos referencia a los switches de la red se puede utilizar el protocolo de IEEE 802.1Q es el estándar que define cómo se implementa el trunking de VLAN en una red Ethernet para asi, este pueda etiquetar los paquetes con su correspondiente ID de VLAN antes de enviarlos a través del trunk, donde al llegar al otro extremo, el switch puede leer la etiqueta y dirigir el paquete a la VLAN correcta.

● **Diseñe una política de QoS que utilice Ethernet y VLAN tags para garantizar la prioridad del tráfico de VoIP.**

La Calidad de Servicio (QoS) es muy escencial para garantizar que el tráfico de VoIP tenga una prioridad sobre el tráfico de datos regulares, donde esto se puede lograr utilizando una de las técnicas que esta basado en la "priorización en etiquetas", donde este asigna una alta prioridad a los paquetes de VoIP. En el caso de una red Ethernet se puede utilizar la funcionalidad de "clase de servicio" (CoS) que se encuentra disponible en las etiquetas VLAN (IEEE 802.1Q). EL CoS en la etiqueta de VLAN tiene un valor de 3 bits, lo que significa que puede llegar a tener hasta 8 niveles de prioridad, por lo que, se puede configurar la red para que todos los paquetes de VoIP sean etiquetados con un valor de CoS mas alto, asegurando que se les dé prioridad durante la transmisión.

● **Simule el entorno utilizando software de simulación de redes y describa cómo los conceptos de Fast Ethernet, Gigabit Ethernet, y Full-duplex mode se aplican en este diseño.**

Los conceptos mencionados para describir se refiere na las tecnologías y modos de operación en que se pueden utilizar dentro de una red.

- **Fast Ethernet (100BASE-T):** Es una versión de Ethernet que soporta velocidasdes de datos hasta 100 Mbps.
- **Gigabit Ethernet (1000BASE-T):** Es una versión más rápida de Ethernet  que soporta grandes velocidades de datos de hasta 1000 Mbps (1 Gbps), donde es recomendable para el enlace troncal de la red que necesita aveces una alta capacidad de transmisión de datos.
- **Full-duplex mode:** Es un modo de comunicación donde los datos pueden ser enviados y recibidos al mismo tiempo, lo que efectivamente duplica la capacidad de transmisión de los datos del enlace, además, es especialmente útil para el tráfico de VoIP que requiere una comunicación bidirrecional constante.

- *Para tu presentación y código a presentar puedes utilizar:*

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/fa705d70-d0e0-49fe-a803-0466cae1c510)

#### Parte 1: Diseño de red utilizando VLANs y troncales

##### Requisitos:

● Definir diferentes VLANs para VoIP y datos en cada sucursal.

● Configurar troncales para permitir el tráfico de ambas VLANs entre los switches y routers de la red Metro Ethernet.

##### Código de python

- Instalamos netmiko para importar la libreria correspondiente:

```
pip install netmiko
```
```
from netmiko import ConnectHandler

def configure_switch(ip_address, username, password):
    # Definir VLANs para VoIP y datos
    commands = [
        'vlan 10',
        'name DATA',
        'exit',
        'vlan 20',
        'name VOIP',
        'exit',
    ]
    
    # Configurar troncales
    trunk_commands = [
        'interface range gig0/1-2',
        'switchport trunk encapsulation dot1q',
        'switchport mode trunk',
        'switchport trunk allowed vlan 10,20',
    ]
    
    try:
        # Conexión al switch
        switch = {
            'device_type': 'cisco_ios',
            'ip': ip_address,
            'username': username,
            'password': password,
        }
        
        # Establecer conexión y enviar comandos de VLANs
        with ConnectHandler(**switch) as conn:
            vlan_output = conn.send_config_set(commands)
            print("VLANs configuradas:")
            print(vlan_output)
            
            # Enviar comandos de troncales
            trunk_output = conn.send_config_set(trunk_commands)
            print("\nTroncales configuradas:")
            print(trunk_output)
            
            # Desconectar
            conn.disconnect()
    except Exception as e:
        print(f"Error de conexión: {e}")

# Ejemplo de uso
configure_switch('192.168.1.100', 'admin', 'password')
```
#### Resultados:

```
Error de conexión: TCP connection to device failed.

Common causes of this problem are:
1. Incorrect hostname or IP address.
2. Wrong TCP port.
3. Intermediate firewall blocking access.

Device settings: cisco_ios 192.168.1.100:22
```
Este código proporciona una forma modular y organizada de configurar un switch utilizando Netmiko, una biblioteca de Python para automatizar tareas de redes, además, permite configurar los VLANs y troncales en el switch de manera que sea eficiente y poder manejar posibles errores de conexión de manera adecuada, Donde en el código nos dio que existe un error de conexión.


#### Parte 2: Configuración de QoS para priorizar VoIP

##### Requsitos:

● Utilizar políticas de QoS para asegurar que el tráfico de VoIP tenga la máximaprioridad.

##### Código Python:
```
from netmiko import ConnectHandler

def configure_qos(ip_address, username, password):
    switch = {
        'device_type': 'cisco_ios',
        'ip': ip_address,
        'username': username,
        'password': password,
    }
    
    qos_commands = [
        'access-list 101 permit ip any any',
        'class-map match-any VOIP',
        'match access-group 101',
        'exit',
        'policy-map VOIP-Policy',
        'class VOIP',
        'set ip dscp ef',
        'exit',
        'interface gig0/1',
        'service-policy output VOIP-Policy',
    ]
    
    try:
        with ConnectHandler(**switch) as conn:
            output = conn.send_config_set(qos_commands)
            print(output)
            conn.disconnect()
    except Exception as e:
        print(f"Error de conexión: {e}")

# Ejemplo de uso
configure_qos('192.168.1.44', 'admin', 'password')

```
#### Resultados:
```
Error de conexión: TCP connection to device failed.

Common causes of this problem are:
1. Incorrect hostname or IP address.
2. Wrong TCP port.
3. Intermediate firewall blocking access.

Device settings: cisco_ios 192.168.1.44:22

```
El código utiliza la biblioteca Netmiko para establecer conexiones SSH con dispositivos Cisco IOS y configurar políticas de QoS que prioricen el tráfico de VoIP sobre otros tipos de tráfico en la red. Para lograr esto, se definio una función llamada `configure_qos` que toma la dirección IP del dispositivo, el nombre de usuario y la contraseña como parámetros. Esta función envía una serie de comandos de configuración de QoS al dispositivo, incluyendo la creación de listas de acceso, clases de tráfico y políticas de QoS. Luego, establece la conexión SSH con el dispositivo utilizando la función `ConnectHandler` de Netmiko, envía los comandos de configuración donde maneja cualquier error que pueda ocurrir durante el proceso. Finalmente, muestra un ejemplo de uso de la función `configure_qos`, donde nos dio como resultado que existio un error.

#### Parte 3: Simulación y análisis
- Utilizar herramientas de simulación o scripts adicionales en Python para simular el tráfico y medir la efectividad de las políticas de QoS. Aquí, se podría usar scapy para generar tráficode VoIP y de datos, y observar la priorización basada en los DSCP tags asignados a los paquetes.

```
pip install scapy
```
```
from scapy.all import *

def generate_traffic():
   # Definir las direcciones IP de origen y destino.
    src_ip = "192.168.1.1"
    dst_ip = "192.168.1.2"

    # Generar tráfico VoIP
    for i in range(10):
       # Cree un paquete VoIP con un valor DSCP alto (EF = 46)
        voip_packet = IP(src=src_ip, dst=dst_ip, tos=184) / UDP(dport=5060)
        # Enviar el paquete
        send(voip_packet)

    # Generar tráfico de datos
    for i in range(10):
        # Crea un paquete de datos con un valor DSCP bajo (BE = 0)
        data_packet = IP(src=src_ip, dst=dst_ip, tos=0) / TCP(dport=80)
        # Send the packet
        send(data_packet)

# Ejecutar la función para generar tráfico.
generate_traffic()

```
#### Resultados:
```
Sent 1 packets.

Sent 1 packets.
```

Este código utiliza la biblioteca Scapy en Python para generar tráfico simulado tanto de VoIP como de datos, donde crea paquetes con direcciones IP de origen y destino predefinidos y los envía a través de la red. La diferencia entre los paquetes de VoIP y datos radica en los valores DSCP (Differentiated Services Code Point) que se les asigno, lo que permite simular diferentes niveles de priorización de tráfico. Luego de generar los paquetes, los envía utilizando la función `send` de Scapy. Este código es útil para probar y analizar políticas de QoS (Quality of Service) en una red simulada.


## PROBLEMA 2: Implementación de seguridad en WLAN con tecnología MIMO-OFDN

### Contexto:

Una universidad desea actualizar su red WLAN para mejorar la cobertura, elrendimiento y la seguridad. Se decide implementar tecnología MIMO-OFDM y actualizar losprotocolos de seguridad a WPA 3.

#### Requisitos:
● Describa el proceso de configuración de una WLAN utilizando MIMO-OFDM paramaximizar la cobertura y el rendimiento.

● Explique cómo WPA 3 mejora la seguridad en comparación con WPA y WPA2,particularmente en relación con la gestión de claves y la protección contra ataquescomunes.

● Proponga un esquema para el uso efectivo de ESSID y BSSID en el contexto de unservicio distribuido y un servicio extendido en la red.

- *Para tu presentación y código a presentar puedes utilizar:*

##### Objetivos:
1. Configuración de MIMO-OFDM: Establecer configuraciones que optimicen el uso deMIMO-OFDM para mejorar la capacidad de la red y la cobertura.
2. Seguridad con WPA3: Implementar y configurar WPA 3 para mejorar la seguridad enla red WLAN.
3. Simulación con Python: Usar Python para simular la configuración de la red y testearla seguridad

#### Parte 1: Configuración de MIMO-OFDM
##### Código python:

#### Parte 2: Configuración y simulación de WPA3
##### Implementación de WPA3

Configurar WPA3 requiere soporte de hardware y software, pero podemos simular elproceso de configuración utilizando scripts que podrían ser ejecutados en puntos de accesocompatibles con WPA3.

###### Código python

#### Parte 3: Evaluación de la seguridad

- Finalmente, para evaluar la seguridad de la implementación de WPA3, podríamos utilizarherramientas como Scapy para simular intentos de ataques y verificar la robustez del cifradoy autenticación en la red.

## PROBLEMA 3: Estrategias de mitigaión para interferencia en redes Ad Hoc Inalambricas
### Contexto:

En un entorno de red ad hoc inalámbrico, los dispositivos sufren de interferenciaco-canal y de problemas de acceso al medio debido a la naturaleza descentralizada de la red.

#### Requisitos:

● Explique cómo los protocolos CSMA/CA y CSMA/CD difieren y por qué uno es másadecuado que el otro para redes ad hoc inalámbricas.

● Discuta el impacto de la interferencia co-canal y proponga métodos de modulacióncomo FHSS o DSSS para mitigar este problema.

● Desarrolle un algoritmo o protocolo para mejorar el período libre de contención eneste tipo de redes, incluyendo el uso de vectores de inicialización para la seguridadde las transmisiones.

- *Para tu presentación y código a presentar puedes utilizar:*

##### Objetivos:
1. Implementar CSMA/CA para manejo de acceso al medio.
2. Mitigar la interferencia co-canal utilizando técnicas de modulación como FHSS oDSSS.
3. Mejorar el período libre de contención utilizando un algoritmo personalizado.
4. Simulación con Python de las estrategias propuestas.

#### Parte 1: Implementación de CSMA/CA en Python

##### Simulación de CSMA/CA:
#### Parte2: Mitigación de interferenca Co-canal
##### Simulación básica de DSSS:
#### Parte 3: Mejora del Período Libre de Contención
##### Algoritmo de ajuste dinámico:

## PROBLEMA 4: Análisis y Resolución de Problemas de conectvidad en una rede compleja

### Contexto:

Una red empresarial compuesta por diferentes segmentos de red, incluyendoEthernet, WLAN y VPN, experimenta problemas de conectividad y rendimientointermitentes.

#### Requisitos:
● Utilice técnicas de diagnóstico para identificar y resolver problemas de crosstalk yjam signal en la red Ethernet.

● Explique cómo el roaming y la utilización de SIM card pueden afectar la experienciade los usuarios en la WLAN y proponga soluciones para optimizar la transición entrepuntos de acceso.

● Evalúe cómo diferentes configuraciones de VPN podrían influir en la latencia y elancho de banda de la red, y proponga ajustes para mejorar la conectividad yseguridad.

- *Para tu presentación y código a presentar puedes utilizar:*

#### Objetivos:
1. Diagnóstico de Problemas de Ethernet: Identificar y resolver problemas de crosstalky señales de jam en la red Ethernet.
2. Optimización de WLAN: Examinar el impacto del roaming y la utilización de tarjetasSIM en la experiencia del usuario y la conectividad.
3. Configuración y Optimización de VPN: Evaluar y ajustar la configuración de VPNpara mejorar la latencia y el ancho de banda.
4. Simulación con Python de las estrategias propuestas.

#### Parte 1: Diagnóstico de problemas de Ethernet
##### Código de Python para simular y diagnósticar problemas de Ethernet:
#### Parte 2: Optimización de WLAN
##### Código de python para simular roaming en WLAN:
#### Parte 3: Configuración y Optimización de VPN
##### Código de python paraa simular y optimizar VPN:





