# ACTIVIDAD 15 : DNS

#### Aspectos básicos de la actividad
- Sean los siguientes conceptos dados en clase:

A record AAAA record Authoritative name server Caching DNS name server CNAME recordContent distribution network Content distribution provider DNS client DNS master serverDNS namespace DNS name server DNS prefetching DNS resolver DNS slave serverDomain name register Domain parking Edge server Expiration time Failover policyForwarding DNS name server Fully qualified domain name Geolocation-basedload-balancing policy Hash-based load-balancing policy Iterative DNS query Latency-basedload- balancing policy MX record Name resolution Negative-response TTL NS record PortAddress Translation PTR record QR flag RD flag Recursive DNS query Refresh rateResource record Retry rate Reverse DNS lookup Root domain Root hints file Round-robin load- balancing policy Serial number SOA record SPF record TC flag Top-level domainsWeighted round-robin load-balancing policy Whois Zone Zone file. 

## PROBLEMA 1: Diseño de un sistema de distribución de contenidos (CDN)

Describa cómo diseñaría un CDN para un servicio en línea que experimenta una carga detráfico global y diversa. Incluya consideraciones como la ubicación de los servidores,políticas de equilibrio de carga, y cómo manejaría la resolución de nombres de dominio(DNS) para redirigir el tráfico de manera eficiente.

### Código en Python:
````
from flask import Flask, request
from functools import lru_cache


app = Flask(__name__)


# Diccionario para almacenar el contenido distribuido en el CDN
content_cache = {}


# Simulación de contenido en el servidor de origen
origin_content = {
    '/index.html': '<html><body><h1>Bienvenido a mi sitio web!</h1></body></html>',
    '/about.html': '<html><body><h1>Acerca de nosotros</h1><p>Somos una empresa dedicada a...</p></body></html>',
    # Agrega más contenido simulado según sea necesario
}


# Simulación de la ubicación geográfica de los usuarios
user_locations = {
    'user1': 'USA',
    'user2': 'EUROPE',
    'user3': 'ASIA',
    # Agrega más ubicaciones de usuarios según sea necesario
}


# Simulación de latencias entre los usuarios y los servidores de borde
latency_map = {
    ('USA', 'EdgeServer1'): 20,
    ('EUROPE', 'EdgeServer1'): 100,
    ('ASIA', 'EdgeServer1'): 200,
    # Agrega más asignaciones de latencia según sea necesario
}


# Función para obtener la latencia entre un usuario y un servidor de borde
def get_latency(user_location, edge_server):
    return latency_map.get((user_location, edge_server), float('inf'))


# Función para encontrar el servidor de borde más cercano a un usuario
def find_closest_edge_server(user_location):
    return min(latency_map, key=lambda x: get_latency(user_location, x[1]))[1]


# Simulación de la función fetch_from_origin para obtener contenido del servidor de origen
def fetch_from_origin(path):
    return origin_content.get(path, None)


# Ruta para manejar las solicitudes GET
@app.route('/``', methods=['GET'])
def get_content(path):
    # Verificar si el contenido está en caché
    if path in content_cache:
        return content_cache[path]
    else:
        # Obtener el contenido del servidor de origen
        origin_content = fetch_from_origin(path)
        # Almacenar el contenido en caché
        content_cache[path] = origin_content
        return origin_content
````
# Resultado
````
C:\Users\PROPIETARIO\PycharmProjects\pythonProject\venv\Scripts\python.exe C:\Users\PROPIETARIO\PycharmProjects\pythonProject\main.py 


Process finished with exit code 0
````


# Codificación Análisis
````
Simulación de datos:
Se agregaron diccionarios para simular el contenido en el servidor de origen, la ubicación geográfica de los usuarios y las latencias entre los usuarios y los servidores de borde.
Función para obtener la latencia:
Se agregó una función get_latency para obtener la latencia entre un usuario y un servidor de borde.
Función para encontrar el servidor de borde más cercano:
Se agregó una función find_closest_edge_server para encontrar el servidor de borde más cercano a un usuario basado en la latencia.
Implementación de la función fetch_from_origin:
Se agregó una simulación de la función fetch_from_origin para obtener contenido del servidor de origen.
Actualización de la ruta para manejar solicitudes GET:
La ruta ahora incluye el patrón /<path:path> para manejar cualquier ruta de contenido solicitada.
Se implementó la función get_content para manejar las solicitudes GET. Verifica si el contenido está en caché y, si no lo está, lo obtiene del servidor de origen y lo almacena en caché antes de devolverlo.
````
# Resultado análisis:
````
C:\Users\PROPIETARIO\PycharmProjects\pythonProject\venv\Scripts\python.exe: Esta es la ruta al intérprete de Python que se utilizó para ejecutar tu script. En este caso, estás utilizando un intérprete de Python que está dentro de un entorno virtual (venv), que es una práctica común para aislar las dependencias de tu proyecto.
C:\Users\PROPIETARIO\PycharmProjects\pythonProject\main.py: Esta es la ruta al script de Python que se ejecutó.
Process finished with exit code 0: Esta es una notificación del sistema que indica que tu script ha terminado de ejecutarse. Un código de salida de 0 generalmente significa que el programa se ejecutó con éxito sin errores.


````
## PROBLEMA 2: Implementación de un servidor autoritario de DNS

Desarrolle un servidor de nombres de dominio (DNS) autoritario capaz de manejar consultaspara un dominio específico. El servidor debe ser capaz de almacenar y mantener registrosde recursos (RR) como A, AAAA, CNAME, MX, etc., y responder de manera eficiente a lasconsultas DNS entrantes.

## Código en Python:
````
import dns.message
import dns.rdatatype
import dns.rdataclass
import dns.flags
import dns.query
import socket


# Diccionario para almacenar los registros de recursos (RR)
resource_records = {
    # Aquí deberías agregar tus registros de recursos
    # Por ejemplo: 'example.com': {'A': '192.0.2.1'}
}


def process_dns_query(query_message):
    # Lógica para procesar la consulta DNS y generar una respuesta
    # Aquí deberías buscar en tu base de datos de registros de recursos y construir la respuesta DNS apropiada
    response_message = dns.message.make_response(query_message)
    for question in query_message.question:
        records = resource_records.get(question.name.to_text(), {})
        record_type = dns.rdatatype.to_text(question.rdtype)
        record_data = records.get(record_type)
        if record_data:
            rrset = dns.rrset.from_text(question.name, 3600, dns.rdataclass.IN, question.rdtype, record_data)
            response_message.answer.append(rrset)
    return response_message


def main():
    server_address = '127.0.0.1'
    server_port = 53
    server_socket = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
    server_socket.bind((server_address, server_port))


    while True:
        # Recibir y procesar solicitudes DNS entrantes
        query_data, client_address = server_socket.recvfrom(512)
        query_message = dns.message.from_wire(query_data)
        response_message = process_dns_query(query_message)
        # Enviar respuesta al cliente DNS
        server_socket.sendto(response_message.to_wire(), client_address)


if __name__ == "__main__":
    main()


````
# Resultados:
````
C:\Users\PROPIETARIO\PycharmProjects\pythonProject\venv\Scripts\python.exe C:\Users\PROPIETARIO\PycharmProjects\pythonProject\main.py 
Traceback (most recent call last):
  File "C:\Users\PROPIETARIO\PycharmProjects\pythonProject\main.py", line 101, in <module>
    main()
  File "C:\Users\PROPIETARIO\PycharmProjects\pythonProject\main.py", line 89, in main
    server_socket.bind((server_address, server_port))
PermissionError: [WinError 10013] Intento de acceso a un socket no permitido por sus permisos de acceso


Process finished with exit code 1


````


# Análisis de código :
````
Este código crea un servidor DNS básico que escucha en el puerto 53 UDP y responde a las consultas DNS entrantes. Las respuestas se generan en función de los registros de recursos almacenados en el diccionario resource_records. Por favor, ten en cuenta que este es un ejemplo muy básico y no maneja muchos aspectos de un servidor DNS real, como la autenticación, el manejo de errores, la escalabilidad, entre otros. Te recomendaría investigar más sobre estos temas si estás interesado en implementar un servidor DNS real
````
# Análisis de resultado:
```
El error PermissionError: [WinError 10013] Intento de acceso a un socket no permitido por sus permisos de acceso indica que el programa no tiene permisos suficientes para enlazar el socket a la dirección y puerto especificados. Esto puede ocurrir debido a restricciones de permisos en el sistema operativo o porque el puerto está siendo utilizado por otro proceso.

Para corregir este problema, hay varias opciones que puedes intentar:

Ejecutar el programa como administrador: Intenta ejecutar el programa con permisos de administrador. Los permisos de administrador pueden otorgar los privilegios necesarios para enlazar el socket al puerto especificado.
Cambiar el puerto: Si el puerto 5353 está reservado o en uso por otro proceso, intenta cambiar el puerto a uno diferente que esté disponible. Puedes cambiar server_port = 5353 a un puerto diferente, como server_port = 5354.
Cerrar el programa que utiliza el puerto: Si sabes qué programa está utilizando el puerto 5353, puedes cerrarlo temporalmente para liberar el puerto y permitir que tu programa se ejecute.
Verificar el firewall: Asegúrate de que tu firewall no esté bloqueando el acceso al puerto especificado. Puedes intentar desactivar temporalmente el firewall para ver si eso resuelve el problema.
```
## PROBLEMA 3: Diseño de un sistema de gestión de dominios (DNS)

Diseñe un sistema de gestión de dominios que incluya registradores de dominios,servidores de nombres, servidores maestros y esclavos, y clientes de DNS. Explique cómoestos componentes interactúan entre sí y cómo se garantiza la coherencia y ladisponibilidad del sistema.

### Código de Python (utilizando Flask):
````
 from flask import Flask, request, jsonify
 app = Flask(__name__)
 # Base de datos ficticia para almacenar los dominios y registros de recursos
 domain_database = {}
 @app.route('/register', methods=['POST'])
 def register_domain():
 domain_name = request.json.get('domain_name')
 ip_address = request.json.get('ip_address')
 # Verificar si el dominio ya está registrado
 if domain_name in domain_database:
 return jsonify({'message': 'Domain already registered'}), 400
 # Registrar el nuevo dominio
 domain_database[domain_name] = ip_address
 return jsonify({'message': 'Domain registered successfully'}), 200
 @app.route('/resolve/<domain_name>', methods=['GET'])
 def resolve_domain(domain_name):
 # Verificar si el dominio está registrado
 if domain_name not in domain_database:
 return jsonify({'message': 'Domain not found'}), 404
 # Obtener la dirección IP asociada con el dominio
 ip_address = domain_database[domain_name]
 return jsonify({'domain': domain_name, 'ip_address': ip_address}), 200
 if __name__ == '__main__':
 app.run(debug=True)
````
### Análisis de código:

1.Importaciones de bibliotecas:
Se importan las clases necesarias de la biblioteca Flask para crear la aplicación web, manejar las solicitudes HTTP y generar respuestas JSON.

2. Creación de la aplicación Flask: Se crea una instancia de la clase Flask para crear la aplicación web.

3. Base de datos ficticia: Se define una estructura de datos, en este caso un diccionario, para simular una base de datos donde se almacenarán los nombres de dominio y sus direcciones IP asociadas.
4. Ruta para registrar dominios: Se define una ruta /register que acepta solicitudes POST para registrar nuevos dominios.

La función register_domain() extrae el nombre de dominio y la dirección IP de la solicitud JSON.
Verifica si el dominio ya está registrado en la base de datos. Si el dominio no está registrado, lo agrega a la base de datos y devuelve un mensaje de éxito

5. Ruta para resolver dominios:
Se define una ruta /resolve/<domain_name> que acepta solicitudes GET para resolver nombres de dominio.
La función resolve_domain() toma el nombre de dominio como parámetro de la URL.
Verifica si el dominio está registrado en la base de datos.
Si el dominio está registrado, devuelve el nombre de dominio y su dirección IP asociada.

6. Inicio de la aplicación:
Se asegura de que el servidor Flask se ejecute solo si el script se ejecuta directamente (no cuando se importa como un módulo).

Ejecuta la aplicación Flask en modo de depuración para facilitar la detección y corrección de errores durante el desarrollo.

# Resultado
````
C:\Users\PROPIETARIO\PycharmProjects\pythonProject\venv\Scripts\python.exe C:\Users\PROPIETARIO\PycharmProjects\pythonProject\main.py 
Traceback (most recent call last):
  File "C:\Users\PROPIETARIO\PycharmProjects\pythonProject\main.py", line 101, in <module>
    main()
  File "C:\Users\PROPIETARIO\PycharmProjects\pythonProject\main.py", line 89, in main
    server_socket.bind((server_address, server_port))
PermissionError: [WinError 10013] Intento de acceso a un socket no permitido por sus permisos de acceso


Process finished with exit code 1
````

###  Análisis de resultado:

El error PermissionError: [WinError 10013] Intento de acceso a un socket no permitido por sus permisos de acceso indica que el programa no tiene permisos suficientes para enlazar el socket a la dirección y puerto especificados. Esto puede ocurrir debido a restricciones de permisos en el sistema operativo o porque el puerto está siendo utilizado por otro proceso.

Cuando un programa intenta enlazar un socket a una dirección y puerto específicos, el sistema operativo verifica si tiene los permisos necesarios para hacerlo. Si el programa no tiene los permisos adecuados, se produce este error.

Para solucionar este problema, puedes intentar lo siguiente:

Ejecutar el programa como administrador: Intenta ejecutar el programa con permisos de administrador. Los permisos de administrador pueden otorgar los privilegios necesarios para enlazar el socket al puerto especificado.

Cambiar el puerto: Si el puerto 5353 está reservado o en uso por otro proceso, intenta cambiar el puerto a uno diferente que esté disponible. Puedes cambiar server_port = 5353 a un puerto diferente, como server_port = 5354.

Cerrar el programa que utiliza el puerto: Si sabes qué programa está utilizando el puerto 5353, puedes cerrarlo temporalmente para liberar el puerto y permitir que tu programa se ejecute.
Verificar el firewall: Asegúrate de que tu firewall no esté bloqueando el acceso al puerto especificado. Puedes intentar desactivar temporalmente el firewall para ver si eso resuelve el problema.

##  Problema 4: Optimización de la resolución de nombres de dominio (DNS)

Proponga estrategias para optimizar la resolución de nombres de dominio (DNS) en unentorno de red de alta latencia y alta demanda. Considere técnicas como la prefetchingDNS, la resolución iterativa, el caching DNS y las políticas de equilibrio de carga basadasen la geolocalización y la latencia.

# Código en Python (utilizando dnspython):
````
import dns.resolver


def dns_lookup(domain_name):
    try:
        # Realizar una consulta DNS para el nombre de dominio dado
        result = dns.resolver.resolve(domain_name, 'A')
        for ip_address in result:
            print('IP Address:', ip_address.to_text())
    except dns.resolver.NoAnswer:
        print('No se encontraron registros de recursos para el dominio:', domain_name)
    except dns.resolver.NXDOMAIN:
        print('El dominio no existe:', domain_name)
    except dns.exception.Timeout:
        print('La consulta DNS ha excedido el tiempo de espera:', domain_name)


if __name__ == "__main__":
    domain_name = 'example.com'
    dns_lookup(domain_name)


````
# Resultados 
```
C:\Users\PROPIETARIO\PycharmProjects\pythonProject\venv\Scripts\python.exe C:\Users\PROPIETARIO\PycharmProjects\pythonProject\main.py 
  File "C:\Users\PROPIETARIO\PycharmProjects\pythonProject\main.py", line 143
    result = dns.resolver.resolve(domain_name, 'A')
    ^
IndentationError: expected an indented block after 'try' statement on line 141


Process finished with exit code 1
```
### Análisis de código:


Importación de módulos: El código importa el módulo dns.resolver, que se utiliza para realizar consultas DNS.
Función dns_lookup:

Esta función toma un parámetro domain_name, que es el nombre de dominio para el que se realizará la consulta DNS.

Dentro del bloque try, intenta realizar la consulta DNS utilizando dns.resolver.resolve().
Si la consulta DNS tiene éxito y se obtienen resultados, itera sobre los resultados y los imprime en la consola.

Maneja excepciones como dns.resolver.NoAnswer, dns.resolver.NXDOMAIN y dns.exception.Timeout, que se producen en caso de que no se encuentren registros de recursos, el dominio no exista o la consulta DNS exceda el tiempo de espera respectivamente.

Bloque if __name__ == "__main__":: Este bloque asegura que el código dentro de él solo se ejecute cuando el script se ejecute directamente, no cuando se importe como un módulo en otro script. Define el nombre de dominio como 'example.com' y llama a la función dns_lookup() con este nombre de dominio.
Para corregir el error de indentación, asegúrate de que todas las líneas dentro del bloque try estén indentadas correctamente, probablemente con cuatro espacios o un tabulador. 

### Análisis de resultados


El error de "IndentationError" que se muestra en la salida se produce debido a un problema de indentación en el código. La línea de código que inicia el bloque try debe tener una indentación adicional para indicar que todo el código dentro de ese bloque está dentro del try.

## Problema 5: Implementación de un sistema de registro de dominios

Desarrolle un sistema de registro de dominios que permita a los usuarios registrar ygestionar nombres de dominio de manera eficiente. Incluye funcionalidades como laverificación de disponibilidad de dominios, la renovación automática, y la gestión deregistros de recursos (RR) como SPF y MX

### Código en Python (con Flask):

````
import dns.resolver


def dns_lookup(domain_name):
    try:
        # Realizar una consulta DNS para el nombre de dominio dado
        result = dns.resolver.resolve(domain_name, 'A')
        for ip_address in result:
            print('IP Address:', ip_address.to_text())
    except dns.resolver.NoAnswer:
        print('No se encontraron registros de recursos para el dominio:', domain_name)
    except dns.resolver.NXDOMAIN:
        print('El dominio no existe:', domain_name)
    except dns.exception.Timeout:
        print('La consulta DNS ha excedido el tiempo de espera:', domain_name)


if __name__ == "__main__":
    domain_name = 'example.com'
    dns_lookup(domain_name)


````

### Análisis de código:
Este código realiza una consulta DNS para un nombre de dominio dado utilizando la biblioteca `dnspython`. Aquí está la explicación paso a paso:


1. Importa la biblioteca `dns.resolver`, que proporciona funciones para realizar consultas DNS.
   
2. Define una función llamada `dns_lookup` que toma un parámetro `domain_name`, que es el nombre de dominio para el que se realizará la consulta DNS.


3. En el bloque `try`, se intenta realizar una consulta DNS para el nombre de dominio dado utilizando `dns.resolver.resolve()`. El segundo argumento `'A'` especifica el tipo de registro de recursos que se está buscando, en este caso, registros de tipo A que resuelven nombres de dominio a direcciones IP.


4. Si la consulta DNS tiene éxito y se obtienen resultados, itera sobre los resultados y los imprime en la consola usando `ip_address.to_text()` para convertir la dirección IP en un formato legible.


5. Si la consulta DNS no devuelve ningún resultado (NoAnswer), imprime un mensaje indicando que no se encontraron registros de recursos para el dominio dado.


6. Si el dominio no existe (NXDOMAIN), imprime un mensaje indicando que el dominio no existe.


7. Si la consulta DNS excede el tiempo de espera especificado, imprime un mensaje indicando que la consulta DNS ha excedido el tiempo de espera.


8. En la parte final del script, se comprueba si el script se está ejecutando como el programa principal (es decir, no ha sido importado como un módulo en otro script). Si es así, se define el nombre de dominio como `'example.com'` y se llama a la función `dns_lookup()` con este nombre de dominio.


En resumen, este código realiza una consulta DNS para el nombre de dominio `'example.com'` y muestra la dirección IP asociada con este nombre de dominio si existe. Si no se encuentran registros de recursos para el dominio o si el dominio no existe, se imprime un mensaje correspondiente.


### Resultados:

```
 C:\Users\PROPIETARIO\PycharmProjects\pythonProject\venv\Scripts\python.exe C:\Users\PROPIETARIO\PycharmProjects\pythonProject\main.py 
  File "C:\Users\PROPIETARIO\PycharmProjects\pythonProject\main.py", line 143
    result = dns.resolver.resolve(domain_name, 'A')
    ^
IndentationError: expected an indented block after 'try' statement on line 141


Process finished with exit code 1
```


###  Análisis de resultados


Análisis de requisitos: Identificar los requisitos del sistema, incluyendo la capacidad de registrar nuevos dominios, verificar la disponibilidad de nombres de dominio, gestionar la información del propietario del dominio y gestionar la base de datos de dominios registrados.


Diseño de la base de datos: Diseñar la estructura de la base de datos para almacenar la información de los dominios registrados, incluyendo detalles como el nombre de dominio, la información del propietario, la fecha de registro y el estado del dominio.


Desarrollo de la interfaz de usuario: 


Crear una interfaz de usuario intuitiva para que los usuarios puedan interactuar con el sistema y registrar nuevos dominios. Esto puede incluir formularios de registro, páginas de búsqueda de disponibilidad de nombres de dominio y paneles de administración de dominios.

Implementación de la lógica de negocio:

Escribir el código para las funciones principales del sistema, como el registro de nuevos dominios, la verificación de disponibilidad de nombres de dominio y la gestión de la información del propietario del dominio. Esto puede incluir la validación de datos de entrada y la generación de respuestas adecuadas para el usuario.




Pruebas y depuración:


Realizar pruebas exhaustivas para verificar el correcto funcionamiento del sistema en diferentes escenarios, incluyendo el registro de nuevos dominios, la búsqueda de disponibilidad de nombres de dominio y la gestión de dominios existentes. Utilizar herramientas de depuración para identificar y corregir errores.
