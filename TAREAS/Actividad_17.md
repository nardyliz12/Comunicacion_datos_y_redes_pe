# Actividad 17

## Problema 21: Simulación de resolución de nombres DNS

Conceptos involucrados: DNS client, DNS resolver, Recursive DNS query, Iterative DNS query, A record, AAAA record, MX record, CNAME record, NS record.

- Escribe funciones que simulen el proceso de resolución de nombres DNS. Debes implementar tanto consultas DNS recursivas como iterativas. La función debe poder manejar varios tipos de registros (A, AAAA, MX, CNAME, NS).

  - Implementa una función resolve_name que acepte un nombre de dominio y el tipo de registro y que determine qué tipo de consulta realizar (recursiva o iterativa).
  - Define funciones auxiliares que simulen el comportamiento de diferentes tipos de registros y cómo serían resueltos.
### Codigo de python:
```
# Base de datos simulada de registros DNS
dns_records = {
    'example.com': {
        'A': '93.184.216.34',
        'AAAA': '2606:2800:220:1:248:1893:25c8:1946',
        'MX': 'mail.example.com',
        'CNAME': None,
        'NS': 'ns.example.com'
    },
    'mail.example.com': {
        'A': '93.184.216.36'
    },
    'ns.example.com': {
        'A': '93.184.216.37'
    }
}

def query_dns(domain, record_type):
    """ Simula la búsqueda de un registro DNS específico. """
    records = dns_records.get(domain, {})
    return records.get(record_type)

def iterative_query(domain, record_type):
    """ Simula una consulta iterativa, buscando registro por registro. """
    result = query_dns(domain, record_type)
    if result:
        return result
    return "No record found"

def recursive_query(domain, record_type):
    """ Simula una consulta recursiva, que podría seguir encadenando búsquedas si se encuentra un CNAME. """
    result = query_dns(domain, record_type)
    if record_type == 'CNAME' and result:
        return recursive_query(result, record_type)
    return result if result else "No record found"

def resolve_name(domain, record_type, query_type='recursive'):
    """ Función principal para resolver nombres usando DNS. Decide entre recursiva e iterativa. """
    if query_type == 'recursive':
        return recursive_query(domain, record_type)
    else:
        return iterative_query(domain, record_type)

# Ejemplo de uso
print(resolve_name('example.com', 'A'))  # Consulta recursiva por defecto
print(resolve_name('example.com', 'MX', 'iterative'))  # Consulta iterativa explícita
```
### Resultados:
```
93.184.216.34
mail.example.com
```
#### Ejercicios adicionales
- Extiende la base de datos con más dominios y registros.
```
dns_records = {
    'example.com': {
        'A': '93.184.216.34',
        'AAAA': '2606:2800:220:1:248:1893:25c8:1946',
        'MX': 'mail.example.com',
        'CNAME': None,
        'NS': 'ns.example.com'
    },
    'mail.example.com': {
        'A': '93.184.216.36'
    },
    'ns.example.com': {
        'A': '93.184.216.37'
    },
    'example2.com': {
        'A': '192.168.1.1',
        'AAAA': '2001:0db8:85a3:0000:0000:8a2e:0370:7334',
        'MX': 'mail.example2.com',
        'CNAME': None,
        'NS': 'ns.example2.com'
    },
    'mail.example2.com': {
        'A': '192.168.1.3'
    },
     'ns.example2.com': {
        'A': '192.168.1.4'
    },
     'google.com': {
        'A': '172.217.7.206',
        'AAAA': '2607:f8b0:4004:809::200e',
        'MX': 'alt4.aspmx.l.google.com',
        'CNAME': None,
        'NS': 'ns1.google.com'
    },   
      'mail.google.com': {
        'A': '172.217.7.208'
    },
    'ns.google.com': {
        'A': '172.217.7.209'
    }
}
```

Se han agregado dos nuevos dominios como `example2.com` y `google.com` con su respectivos registros A, AAAA, MX y NS, ya que nos permetirá que cuando ejecutemos la función `resolve_name` podremos consultar estos nuevos dominios y registros, muy aparte de lo que ya existen.

- Mejora la función iterative_query para simular más fielmente cómo los servidores DNS resolverían una consulta iterativa pasando por varios servidores.
```
def query_dns(domain, record_type):
    """ Simula la búsqueda de un registro DNS específico. """
    records = dns_records.get(domain, {})
    return records.get(record_type)

def iterative_query(domain, record_type):
    original_domain = domain
    while True:
        result = query_dns(original_domain, record_type)
        if result:
            return result
        ns_record = query_dns(original_domain, 'NS')
        if not ns_record:
            return "No record found"
        original_domain = ns_record
```
Esta es la versión mejorada de la función `iterative_query`¨, donde lo primero que intentará encontrar el resgistro deseaddo en el dominio original utilizando la función de `query_dns`, donde nos indica que si el registro no se encuentra, la función buscará el servidor de nombres NS del dominio actual mediante otra llamada a `query_dns` con el tipo de registro NS, pero si se encuentra el registro NS, la función actualizará el dominio acual al servidor de nombres devuelto y volverá a repetir el proceso, basicamente este proceso iterativo simula las consultas DNS en busca de registros deseados.

- Implementa un manejo más complejo de registros CNAME en recursive_query
```
def recursive_query(domain, record_type, visited=None):

    visited = visited or set()  # Inicializa el conjunto de registros visitados si no está presente
    if domain in visited:
        return "CNAME loop detected"  # Manejo de bucles de CNAME para evitar ciclos infinitos
    
    results = query_dns(domain, record_type)
    if record_type == 'CNAME' and results:
        visited.add(domain)  # Agrega el dominio actual a los visitados
        return recursive_query(results, record_type, visited)  # Realiza una nueva consulta con el dominio apuntado por el CNAME
    return results if results else "No record found"

def resolve_name(domain, record_type, query_type='recursive'):
    """ Función principal para resolver nombres usando DNS. Decide entre recursiva e iterativa. """
    if query_type == 'recursive':
        return recursive_query(domain, record_type)
    else:
        return iterative_query(domain, record_type)

# Ejemplo de uso
print(resolve_name('google.com', 'A'))  # Consulta recursiva por defecto
print(resolve_name('google.com', 'MX', 'iterative'))  # Consulta iterativa explícita
```
En esta versión comparado al codigo base, es que se le agregó un parametro adiconal llamado `visited` que basicamente nos servirá para rastrear los dominios visitados durante la busqueda recursiva, ya que esto nos ayuda a detectar y evitar bucles de CNAME, donde también verifica si el dominio acctual ya ha sido visitado para evitar bucles infinitos.

#### Resultados:
```
172.217.7.206
mail.google.com
``` 
- ## Problema 22: Gestión de caché en un servidor DNS

Conceptos involucrados: Caching DNS name server, TTL, Expiration time, Refresh rate.

- Desarrolla una función que simule un servidor DNS que utiliza caché para almacenar respuestas DNS. La caché debe expirar las entradas basadas en su TTL.

  - Crea una función query_dns que consulte una caché antes de simular una consulta externa.
  - Implementa una función update_cache para añadir o actualizar entradas en la caché, incluyendo manejo del TTL.
  - Añade una función clean_expired_entries que limpie las entradas expiradas de la caché periódicamente.

### Código original:
```
import time

# Caché simulada para registros DNS con TTL
dns_cache = {}

def update_cache(domain, record_type, value, ttl):
    """Añade o actualiza una entrada en la caché con su TTL."""
    expiration = time.time() + ttl
    if domain not in dns_cache:
        dns_cache[domain] = {}
    dns_cache[domain][record_type] = (value, expiration)
    print(f"Cache updated: {domain} [{record_type}] -> {value} (TTL: {ttl}s)")

def query_dns(domain, record_type):
    """Consulta la caché para obtener el registro; si no está o ha expirado, simula una consulta externa."""
    if domain in dns_cache and record_type in dns_cache[domain]:
        value, expiration = dns_cache[domain][record_type]
        if expiration > time.time():
            print(f"Cache hit: {domain} [{record_type}] -> {value}")
            return value
        else:
            print(f"Cache expired for: {domain} [{record_type}]")
    # Simulación de una consulta externa (podrías mejorar esto con lógica de red real)
    external_value = "192.168.1.1"  # Valor ficticio
    update_cache(domain, record_type, external_value, 30)  # TTL de 30 segundos
    return external_value

def clean_expired_entries():
    """Limpia las entradas expiradas en la caché."""
    current_time = time.time()
    for domain in list(dns_cache.keys()):
        for record_type in list(dns_cache[domain].keys()):
            _, expiration = dns_cache[domain][record_type]
            if expiration <= current_time:
                del dns_cache[domain][record_type]
                if not dns_cache[domain]:
                    del dns_cache[domain]
                print(f"Expired cache entry removed: {domain} [{record_type}]")

# Uso de la simulación de caché DNS
update_cache('example.com', 'A', '93.184.216.34', 10)  # TTL de 10 segundos
query_dns('example.com', 'A')
time.sleep(5)
query_dns('example.com', 'A')
time.sleep(6)
query_dns('example.com', 'A')
clean_expired_entries()
```
### Resultados:
```
Cache updated: example.com [A] -> 93.184.216.34 (TTL: 10s)
Cache hit: example.com [A] -> 93.184.216.34
Cache hit: example.com [A] -> 93.184.216.34
Cache expired for: example.com [A]
Cache updated: example.com [A] -> 192.168.1.1 (TTL: 30s)
```
### Ejercicios adicionales
```
!pip install nest_asyncio
```
```
import asyncio
import time
import nest_asyncio
```
- Modifica las funciones update_cache y query_dns para soportar diferentes tipos de registros DNS. Asegúrate de que tu caché pueda almacenar múltiples tipos de registros para un mismo dominio y que la función query_dns busque correctamente según el tipo de registro solicitado.
```
def update_cache(domain, record_type, value, ttl):
    """Añade o actualiza una entrada en la caché con su TTL."""
    expiration = time.time() + ttl
    cache_key = (domain, record_type)
    if cache_key not in dns_cache:
        dns_cache[cache_key] = (value, expiration)
    else:
        _, current_expiration = dns_cache[cache_key]
        if expiration > current_expiration:
            dns_cache[cache_key] = (value, expiration)
    print(f"Cache updated: {domain} [{record_type}] -> {value} (TTL: {ttl}s)")

def query_dns(domain, record_type):
    """Consulta la caché para obtener el registro; si no está o ha expirado, realiza una consulta externa."""
    cache_key = (domain, record_type)
    if cache_key in dns_cache:
        value, expiration = dns_cache[cache_key]
        if expiration > time.time():
            print(f"Cache hit: {domain} [{record_type}] -> {value}")
            return value
        else:
            print(f"Cache expired for: {domain} [{record_type}]")
            del dns_cache[cache_key]  # Elimina la entrada expirada de la caché
    # Consulta externa simulada
    external_value = external_dns_query(domain, record_type)
    if external_value != "No record found":
        update_cache(domain, record_type, external_value, 30)  # TTL de 30 segundos
    return external_value
```
Las modificaciones empleadas frente al código base en la función de `update_cache` es que ahora acepta un nuevo parámetro `record_type` que nos especificará el tipo de registro DNS que es, además, la función de `query_dns` ahora utiliza una clave compuesta `(domain, record_type)` es que para buscar y almacenar registros en el caché, lo que nos permite que la caché almacene y recuepere múltiples tipos de registros para un mismo dominio.

- Implementa una función external_dns_query que simule de manera más realista una consulta DNS externa. Por ejemplo, podría seleccionar de un conjunto predefinido de respuestas basadas en el dominio y el tipo de registro.
```
def external_dns_query(domain, record_type):
    """Simula una consulta DNS externa y devuelve una respuesta predefinida."""
    predefined_responses = {
        ('example.com', 'A'): '93.184.216.34',
        ('example.com', 'AAAA'): '2606:2800:220:1:248:1893:25c8:1946',
        ('example.com', 'MX'): 'mail.example.com',
        ('example.com', 'CNAME'): None,
        ('example.com', 'NS'): 'ns.example.com',
        ('mail.example.com', 'A'): '93.184.216.36',
        ('ns.example.com', 'A'): '93.184.216.37',
    }
    return predefined_responses.get((domain, record_type), "No record found")
```
Esta función `external_dns_query` toma un domio y un tipo de registro como entrada donde devuelve una respuesta predefinida basada en el conjunto de respuestas predefinidas `predefined_responses`, donde si no hay una respuesta predefinida para la combinación específica de dominio y el tipo de registro, donnde la función nos devolverá "No record found".

- Implementa una manera de que esta función se ejecute automáticamente en intervalos regulares. Considera el uso de threading o programación asíncrona para manejar esta tarea en el fondo sin bloquear las consultas principales.
```
async def clean_expired_entries(interval, max_iterations):
    """Limpia las entradas expiradas en la caché en intervalos regulares."""
    for _ in range(max_iterations):
        await asyncio.sleep(interval)
        current_time = time.time()
        expired_entries = [(domain, record_type) for (domain, record_type), (_, expiration) in dns_cache.items() if expiration <= current_time]
        for cache_key in expired_entries:
            del dns_cache[cache_key]
            print(f"Expired cache entry removed: {cache_key[0]} [{cache_key[1]}]")

async def main():
    update_cache('example.com', 'A', '93.184.216.34', 10)  # TTL de 10 segundos
    query_dns('example.com', 'A')
    query_dns('example.com', 'A')
    query_dns('example.com', 'A')
    await clean_expired_entries(5, 10)  # Limpia las entradas expiradas cada 5 segundos, se detiene después de 10 iteraciones

if __name__ == "__main__":
    nest_asyncio.apply()
    asyncio.run(main())
```
El código incluye la función `clean_expired_entries` que toma dos parámetros que son el `interval` que especifica el intervalo de tiempo entre cada limpieza en la caché, y `max_iterations` que determina cuántas veces la función debe ejecutarse antes de detenerse, ya que dentro del bucle `for` la función espera el intervalo especificado usando `await asyncio.sleep(interval)` y luego limpia las entradas expiradas en la caché, para después completar las `max_iterations` iteraciones, donde la función se detiene, proporcionando así un mecanismo controlado para limpiar la caché de manera periódica y limitada.

### Resultados:
```
Cache updated: example.com [A] -> 93.184.216.34 (TTL: 10s)
Cache hit: example.com [A] -> 93.184.216.34
Cache hit: example.com [A] -> 93.184.216.34
Cache hit: example.com [A] -> 93.184.216.34
Expired cache entry removed: example.com [A]
```
