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
- ## Problema 22: Gestión de caché en un servidor DNS

Conceptos involucrados: Caching DNS name server, TTL, Expiration time, Refresh rate.

- Desarrolla una función que simule un servidor DNS que utiliza caché para almacenar respuestas DNS. La caché debe expirar las entradas basadas en su TTL.

  - Crea una función query_dns que consulte una caché antes de simular una consulta externa.
  - Implementa una función update_cache para añadir o actualizar entradas en la caché, incluyendo manejo del TTL.
  - Añade una función clean_expired_entries que limpie las entradas expiradas de la caché periódicamente.
