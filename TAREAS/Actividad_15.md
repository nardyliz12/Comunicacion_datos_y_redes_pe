# ACTIVIDAD 15: DNS

#### Aspectos básicos de la actividad

- Sean los siguientes conceptos dados en clase:

A record AAAA record Authoritative name server Caching DNS name server CNAME recordContent distribution network Content distribution provider DNS client DNS master serverDNS namespace DNS name server DNS prefetching DNS resolver DNS slave serverDomain name register Domain parking Edge server Expiration time Failover policyForwarding DNS name server Fully qualified domain name Geolocation-basedload-balancing policy Hash-based load-balancing policy Iterative DNS query Latency-basedload- balancing policy MX record Name resolution Negative-response TTL NS record PortAddress Translation PTR record QR flag RD flag Recursive DNS query Refresh rateResource record Retry rate Reverse DNS lookup Root domain Root hints file Round-robin load- balancing policy Serial number SOA record SPF record TC flag Top-level domainsWeighted round-robin load-balancing policy Whois Zone Zone file.

## PROBLEMA 1: Diseño de un sistema de distribución de contenidos (CDN)

Describa cómo diseñaría un CDN para un servicio en línea que experimenta una carga detráfico global y diversa. Incluya consideraciones como la ubicación de los servidores,políticas de equilibrio de carga, y cómo manejaría la resolución de nombres de dominio(DNS) para redirigir el tráfico de manera eficiente.

- *Para tu presentación y códigp a presentar puedes utilizar:*

### Objetivos de Aprendizaje:
1. Comprender los principios y objetivos de un Sistema de Distribución de Contenidos(CDN).
2. Identificar los componentes clave de un CDN y su función en la entrega decontenido.
3. Diseñar una arquitectura CDN eficiente que pueda manejar la distribución decontenido a nivel mundial.
4. Considerar estrategias de balanceo de carga, almacenamiento en caché ydistribución geográfica para optimizar el rendimiento del CDN.
5. Evaluar los beneficios y desafíos asociados con la implementación de un CDN paraun servicio en línea.

#### Código de Python:

## PROBLEMA 2: Implementación de un sisttema autoritario de DNS

Desarrolle un servidor de nombres de dominio (DNS) autoritario capaz de manejar consultaspara un dominio específico. El servidor debe ser capaz de almacenar y mantener registrosde recursos (RR) como A, AAAA, CNAME, MX, etc., y responder de manera eficiente a lasconsultas DNS entrantes.

- *Para tu presentación y código a presentar puedes utilizar:*

#### Objetivos
1. Comprender los principios básicos del protocolo DNS y la función de un servidorautoritativo.
2. Familiarizarse con los diferentes tipos de registros de recursos (RR) y su uso en laresolución de nombres de dominio.
3. Diseñar e implementar la lógica para procesar consultas DNS entrantes y generarrespuestas autoritativas basadas en los registros de recursos almacenados.
4. Utilizar sockets y protocolo UDP para la comunicación entre el servidor DNS y losclientes.
5. Implementar pruebas para verificar el correcto funcionamiento del servidorautoritativo de DNS

#### Código de Python:

## PROBLEMA 3: Diseño de un sistema de gestión de dominios (DNS)

Diseñe un sistema de gestión de dominios que incluya registradores de dominios,servidores de nombres, servidores maestros y esclavos, y clientes de DNS. Explique cómoestos componentes interactúan entre sí y cómo se garantiza la coherencia y ladisponibilidad del sistema.

- *Para tu presentación y código a presentar puedes utilizar:*

#### Objetivos :
1. Comprender los principios básicos de la gestión de dominios y el funcionamiento delsistema DNS.
2. Identificar los requisitos funcionales y no funcionales para un sistema de gestión dedominios eficaz.
3. Diseñar la arquitectura del sistema DNS, incluyendo la estructura de la base dedatos, la lógica de negocio y la interfaz de usuario.
4. Implementar las funciones básicas del sistema, como el registro de dominios, laactualización de registros de recursos y la resolución de nombres de dominio.
5. Desarrollar pruebas para verificar el correcto funcionamiento del sistema y sucapacidad para gestionar consultas DNS entrantes.

#### Código de Python (utilizando Flask):

## PROBLEMA 4: Optimización de la resolución de nombres de dominio (DNS)

Proponga estrategias para optimizar la resolución de nombres de dominio (DNS) en unentorno de red de alta latencia y alta demanda. Considere técnicas como la prefetchingDNS, la resolución iterativa, el caching DNS y las políticas de equilibrio de carga basadasen la geolocalización y la latencia.

- *Para tu presentación y código a presentar puedes utilizar:*

#### Objetivos:
1. Comprender los factores que afectan el rendimiento de la resolución de nombres dedominio, como la latencia de red, la carga del servidor DNS y el tiempo de caché.
2. Identificar las técnicas de optimización más comunes utilizadas en la resolución denombres de dominio, como el uso de caché DNS, la configuración adecuada delservidor DNS y el uso de servidores DNS de terceros.
3. Aprender a configurar y ajustar un servidor DNS en un entorno de Linux paramejorar el rendimiento y la fiabilidad del sistema.
4. Desarrollar habilidades en el monitoreo y la evaluación del rendimiento del sistemaDNS para identificar posibles cuellos de botella y áreas de mejora.
5. Implementar técnicas avanzadas de optimización, como la configuración de TTL(Tiempo de Vida) adecuado, la implementación de DNSSEC (DNS SecurityExtensions) y el uso de servidores de caché DNS locales

#### Código Python (utilizando dnspython):

## PROBLEMA 5: Implementación de un sistema de registro de dominios

Desarrolle un sistema de registro de dominios que permita a los usuarios registrar ygestionar nombres de dominio de manera eficiente. Incluye funcionalidades como laverificación de disponibilidad de dominios, la renovación automática, y la gestión deregistros de recursos (RR) como SPF y MX.

- *Para tu presentación y código a presentar puedes utilizar:*

#### Objetivos :
1. Comprender los conceptos básicos de registro de dominios y los protocolosinvolucrados, como WHOIS.
2. Identificar los requisitos funcionales y no funcionales para un sistema de registro dedominio eficaz.
3. Diseñar la arquitectura del sistema de registro de dominio, incluyendo la interfaz deusuario, la lógica de negocio y la base de datos.
4. Implementar las funciones principales del sistema, como el registro de nuevosdominios, la verificación de disponibilidad de nombres de dominio y la gestión dedominios existentes.
5. Desarrollar pruebas para verificar el correcto funcionamiento del sistema y sucapacidad para gestionar el registro de dominios en un entorno de producción

#### Código de Python (con Flask):







