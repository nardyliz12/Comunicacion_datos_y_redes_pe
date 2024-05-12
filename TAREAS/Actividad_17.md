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
