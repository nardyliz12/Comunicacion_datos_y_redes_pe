# ACTIVIDAD 14: Herramientas para TCP/IP

#### Aspectos básicos de la actividad

Sean los siguientes conceptos dados en clase: Address resolution aureport ausearchBase64 encoding Canonical name cURL Denial of service attack dig Event Viewer Filter Hophost ifconfig ip ipconfig IP lookup Log file Netcat netstat Network (service) nslookup Packetcapture ping Probe Reconnaissance attack Reverse IP lookup Route Smurf attacktraceroute/tracert tcpdump wget whois Wireshark

## PROBLEMA 1: Simulación de un ataque de reconocimiento y mitigación
### Contexto:
Una empresa observa actividad sospechosa en sus servidores y sospecha de unataque de reconocimiento. Los estudiantes deben utilizar herramientas como dig,traceroute, y whois para identificar la fuente y naturaleza del ataque, seguido por laimplementación de estrategias para mitigar y prevenir futuros ataques.
#### Requisitos:
● Utilizar dig para analizar las consultas DNS sospechosas dirigidas a los servidoresde la empresa.

● Emplear traceroute para determinar la ruta que siguen los paquetes desde la fuentesospechosa hasta el servidor.

● Aplicar whois para obtener información sobre los propietarios de las direcciones IPidentificadas en el ataque.

● Configurar reglas de filtrado y rastrear paquetes con tcpdump para capturar tráficomalicioso y analizarlo con Wireshark.

- *Para tu presentación y código a presentar puedes utilizar:*

#### Objetivos:

1. Identificación del Ataque: Usar herramientas de DNS y trazado de rutas para identificar la fuente del ataque.
2. Análisis de Tráfico: Automatizar la captura y análisis de tráfico de red para detectar patrones anormales.
3. Mitigación y Prevención: Implementar reglas de filtrado y monitorear la red para prevenir futuros ataques.

#### Paso 1: Identificación del ataque utilizando Python
##### Código de Python:

#### Paso 2: Análisis de tráfico
##### Código de Python:

#### Paso 3: Mitigación y prevención

-	Finalmente, vamos a implementar reglas de filtrado para bloquear tráfico sospechoso y ajustar la configuración del firewall.

#### Código de Python:

## PROBLEMA 2: Análisis forense de un ataque de denegación de servicio (DoS)
### Contexto: 

Un servicio en línea de la empresa ha sido interrumpido debido a un ataque DoS. Se requiere que los estudiantes realicen un análisis forense utilizando registros de eventos y herramientas de captura de paquetes para identificar la fuente del ataque y proponer medidas correctivas
#### Requisitos:

● Analizar archivos de registro del servidor con ausearch y aureport para identificar patrones anormales.

● Utilizar tcpdump para capturar paquetes durante el ataque y usar Wireshark para filtrar y analizar estos paquetes.

● Desarrollar una estrategia de mitigación usando técnicas como la limitación de tasade conexiones y el bloqueo de IPs específicas.

● Discutir el uso de cURL y wget para simular y testear la resistencia del servidor después de aplicar las medidas de mitigación.

- *Para tu presentación y código a presentar puedes utilizar:*

##### Objetivos:

1. Diseño del protocolo: Definir el formato de los mensajes, incluyendo cabeceras y extensiones de cabecera para control de flujo, manejo de errores, y otras funciones críticas.
2. Implementación de control de flujo: Desarrollar un esquema de control de flujobasado en ventana deslizante para asegurar una transferencia de datos eficiente yfiable.
3. Simulación con python: Utilizar Python para crear un prototipo del protocolo, simularsu funcionamiento y evaluar su rendimiento en diversas condiciones de red.
4. Evaluación y optimización: Analizar los resultados de las simulaciones para identificar problemas y optimizar el protocolo.

#### Paso 1: Diseño del protocolo

Definiremos un formato básico para los mensajes del protocolo, incluyendo tipos deoperaciones como PUT, GET, y DELETE. Cada mensaje tendrá una cabecera que incluye eltipo de operación, el tamaño del mensaje, un número de secuencia, y un número de acusede recibo

##### Estructura de la cabecera del protocolo protocolo:
#### Paso 2: Implementación de control de flujo
##### Código de Python:
#### Paso 3: Evaluación y Optimización
##### Código Python para simulación de condiciones de red:

## PROBLEMA 3: Implementación y análisis de una red ssegura utilizando varias herramientas

Diseña una red para una pequeña empresa que incluya servidores web, de correoelectrónico y bases de datos. Utiliza ifconfig o ipconfig para configurar las interfaces de red,dig y whois para configurar los registros DNS, y cURL o wget para probar la accesibilidad delos servicios. Además, implementa estrategias de defensa en profundidad como zonasdesmilitarizadas (DMZ) y subredes internas.

##### Objetivos: 

Configurar y verificar configuraciones de red, usar herramientas de DNS para resolver nombres de host, y establecer y verificar medidas de seguridad.

-	**Para tu presentación y código a presentar puedes utilizar:**

#### 1.	Configuración de la red

Supongamos que estamos configurando una red que incluye un servidor web, un servidor de correo electrónico y un servidor de base de datos. Utilizaremos ifconfig o el moderno ip para configurar las interfaces de red.

##### Configuración de IP estática en Linux

#### 2.	Configuración de DNS con dig y whois

##### Para configurar y verificar registros DNS, así como para obtener información de dominio:

#### 3.	Scripting para automatización y monitoreo

- Aquí podemos escribir un script en Python para monitorear la disponibilidad de los servicios y verificar la conectividad usando ping y traceroute.

##### Script de monitoreo en Python

#### 4.	Uso de cURL o wget para pruebas

- Podemos usar cURL o wget para verificar la accesibilidad de los servidores web:

#### 5.	Implementar seguridad

- Podríamos configurar firewalls utilizando iptables para limitar el acceso no autorizado a los servicios:

## PROBLEMA 4: Desarrollo de un script para monitoreo y alerta de red
### Problema:

Escribe un script utilizando bash o python que utilice herramientas como ping,traceroute, y nslookup para monitorear la disponibilidad de varios servidores críticos. El script debe registrar cualquier anomalía y enviar alertas automáticas si detecta problemas como tiempos de respuesta elevados o pérdida de paquetes.
#### Objetivos: 

- Automatizar el monitoreo de la red, interpretar la salida de herramientas de red, y desarrollar mecanismos de alerta en tiempo real.

#### Requisitos para el script de monitoreo de red

1. Ping a los servidores para verificar la conectividad.
2. Traceroute para diagnosticar la ruta de la red.
3. Envío de alertas por correo electrónico cuando se detecte un problema.
4. Registro de actividades para análisis posterior.

##### Script de monitoreo de red en Python

##### Consideraciones adicionales

● Seguridad: Asegúrate de que las credenciales del servidor SMTP estén seguras y considera el uso de variables de entorno o configuraciones seguras para almacenarlas.

● Extensibilidad: Puedes expandir este script para incluir más comprobaciones, como verificar puertos específicos con nmap o comprobar la carga de los servidores con ssh y comandos como top.

● Resiliencia: Considera implementar mecanismos de reintento o backoff en caso de fallas temporales de re

