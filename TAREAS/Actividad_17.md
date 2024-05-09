# Actividad 17

## Problema 21: Simulación de resolución de nombres DNS

Conceptos involucrados: DNS client, DNS resolver, Recursive DNS query, Iterative DNS query, A record, AAAA record, MX record, CNAME record, NS record.

- Escribe funciones que simulen el proceso de resolución de nombres DNS. Debes implementar tanto consultas DNS recursivas como iterativas. La función debe poder manejar varios tipos de registros (A, AAAA, MX, CNAME, NS).

  - Implementa una función resolve_name que acepte un nombre de dominio y el tipo de registro y que determine qué tipo de consulta realizar (recursiva o iterativa).
  - Define funciones auxiliares que simulen el comportamiento de diferentes tipos de registros y cómo serían resueltos.
### Codigo de python:


- ## Problema 22: Gestión de caché en un servidor DNS

Conceptos involucrados: Caching DNS name server, TTL, Expiration time, Refresh rate.

- Desarrolla una función que simule un servidor DNS que utiliza caché para almacenar respuestas DNS. La caché debe expirar las entradas basadas en su TTL.

  - Crea una función query_dns que consulte una caché antes de simular una consulta externa.
  - Implementa una función update_cache para añadir o actualizar entradas en la caché, incluyendo manejo del TTL.
  - Añade una función clean_expired_entries que limpie las entradas expiradas de la caché periódicamente.
