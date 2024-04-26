# ACTIVIDAD 12: Construyendo una área de red local

##### Aspectos básicos de la actividad

Sean los siguientes conceptos dados en clase: 5-4-3 rule Ad hoc wireless network Association Autonegotiation Band Basic service setBSSID Cellular network Chips Co-channel interference Contention-free period Coveragearea Crossover cable Cross-talk CSMA/CA CSMA/CD Distribution system DSSS Dumbterminal ESSID Ethernet repeater Extended service set EUI-48 EUI-64 Fast Ethernet FHSSFlooding Full-duplex mode Gigabit Ethernet Half-duplex mode Hotspot Independent basicservice set IEEE standards Initialization vector Jam signal LAN edge MAC table MetroEthernet MICHAEL MIMO-OFDM Modulation OFDM Power over Ethernet ProbePseudonoise RJ45 jack Roaming SIM card Simplex mode SSID T-connector TerminatorThickNet Thinnet TKIP Trunk UTP VLAN VPN WAP WEP Wireless ad hoc network WLANWLAN frame WNIC WPA WPA2 XOR

## PROBLEMA 1: Diseño y Simulación de una red metro Ethernet con QoS

### Contexto: 

Una empresa necesita diseñar una red Metro Ethernet para conectar variassucursales en una área metropolitana. Se requiere calidad de servicio (QoS) para priorizarel tráfico de voz sobre IP (VoIP) sobre el tráfico regular de datos.

#### Requisitos:

● Explique cómo utilizaría VLAN y Trunk para segmentar y gestionar el tráfico en lared.

● Diseñe una política de QoS que utilice Ethernet y VLAN tags para garantizar laprioridad del tráfico de VoIP.

● Simule el entorno utilizando software de simulación de redes y describa cómo losconceptos de Fast Ethernet, Gigabit Ethernet, y Full-duplex mode se aplican en estediseño.

- Para tu presentación y código a presentar puedes utilizar:

#### Parte 1: Diseño de red utilizando VLANs y troncales

##### Requisitos:

● Definir diferentes VLANs para VoIP y datos en cada sucursal.

● Configurar troncales para permitir el tráfico de ambas VLANs entre los switches yrouters de la red Metro Ethernet.

##### Código de python

#### Parte 2: Configuración de QoS para priorizar VoIP

##### Requsitos:

● Utilizar políticas de QoS para asegurar que el tráfico de VoIP tenga la máximaprioridad.

##### Código Python:

#### Parte 3: Simulación y análisis
- Utilizar herramientas de simulación o scripts adicionales en Python para simular el tráfico ymedir la efectividad de las políticas de QoS. Aquí, se podría usar scapy para generar tráficode VoIP y de datos, y observar la priorización basada en los DSCP tags asignados a lospaquetes.

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





