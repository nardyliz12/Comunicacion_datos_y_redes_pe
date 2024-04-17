# ACTIVIDAD 3: Identificación de direcciones MAC y direcciones IP

### OJETIVOS:

- Parte 1: Recopilar información de PDU para la comunicación de red local
- Parte 2: Recopilar información de PDU para la comunicación de red remota
  
-  **¿Qué dispositivo tiene el MAC de destino que se muestra?**

 Nos muestra el dispositivo con la dirección MAC de destino 00D0:BA8E:741A es el router.

## Preguntas de reflexión

### Responda las siguientes preguntas con respecto a los datos capturados:

**1. ¿Se utilizaron diferentes tipos de cables / medios para conectar dispositivos?**

Sí, se utilizó 3 medios, 1 medio inalámbrico, otro tipo fue 2 cables de cobre y 3 de fibra óptica.

![image](https://github.com/Fx2048/COMU_TEAM/assets/151795724/5dcbc9c3-f3f0-491c-9190-a85f7dcc01ed)

**2. ¿Los cables cambiaron el manejo de la PDU de alguna manera?**

No, ya que los cables solo trabajan a nivel de capa 1.

**3. ¿El Hub perdió parte de la información que recibió?**

No perdio niguna información.

**4. ¿Qué hace el Hub con las direcciones MAC y las direcciones IP?**

El Hub solo reenvía a todos sus puertos el paquete que se está enviando.

![image](https://github.com/Fx2048/COMU_TEAM/assets/151795724/8426f676-fd63-460f-9ea5-dc53dc880a7b)

**5. ¿El punto de acceso inalámbrico hizo algo con la información que se le proporcionó?**

Sí, el Access point empaqueta la trama para que viaje por el aire, lo empaqueta en una trama inalámbrica a todos sus puertos del estándar 802.11. 

![image](https://github.com/Fx2048/COMU_TEAM/assets/151795724/e87628dc-43cc-473b-b12e-eb5140bc62f8)

**6. ¿Se perdió alguna dirección MAC o IP durante la transferencia inalámbrica?**

No se perdió ninguna dirección MAC y IP.

**7. ¿Cuál fue la capa OSI más alta que utilizaron el Hub y el Punto de acceso ?**

El Access point y el hub  ya que trabaja a nivel de capa 1.  

**8. ¿Hubo alguna vez el Hub o Punto deAcceso una PDU que fue rechazada con una "X" roja?**

Sí, ya que, al reenviar en todos los puertos, solo uno es el destino al que se quiere enviar, y los demás los rechaza porque no son el destino.

![image](https://github.com/Fx2048/COMU_TEAM/assets/151795724/ab2a6927-2107-4457-99db-50abbf6a0827)

**9. Al examinar la pestaña Detalles de PDU, ¿qué dirección MAC apareció primero , la fuente o el destino?**

La primera que aparece es la de destino.

![image](https://github.com/Fx2048/COMU_TEAM/assets/151795724/f13e07c5-fcd7-4cf9-8ccd-e1e8ebe97529)

**10. ¿Por qué aparecerían las direcciones MAC en este orden?**

En simples palabras, es porque si se conoce la trama de destino, el dispositivo enviará la trama más rápido. 

**11. ¿Hubo un patrón para el direccionamiento MAC en la simulación?**

En está ocasión no lo hubo.

**12. ¿Los switches replicaron alguna vez una PDU que fue rechazada con una "X" roja?**

Los switches a diferencia del Hub solo reenvían las tramas al destino que se requiere, y no a todas las PCS.

**13. Cada vez que se envió la PDU entre la red 10 y la red 172, hubo un punto en el que las direcciones MAC cambiaron repentinamente. ¿Dónde ocurrió eso?**

Sí, cuando se envió un paquete desde la red de 172.16.31.5 a 172.16.31.2, la dirección de destino era la de router , y cuando llegó la dirección de destino era la del dispositivo, entonces la modificación repentina ocurre en el router. 

![image](https://github.com/Fx2048/COMU_TEAM/assets/151795724/0172cd14-d735-40b6-8216-82b2aad78c12)

**14. ¿Qué dispositivo usa direcciones MAC que comienzan con 00D0: BA?**

El dispositivo que usa la dirección Mac era la dirección del router. 

![image](https://github.com/Fx2048/COMU_TEAM/assets/151795724/9b64a266-99d1-4bfa-be12-18c39270a763)

**15. ¿A qué dispositivos pertenecían las otras direcciones MAC?**

Pertenecían a emisores y receptores, tales como Access point, laptops ,pcs, computadores, switchers. 

**16. ¿Las direcciones IPv4 de envío y recepción cambiaron los campos en alguna de las PDU?**

No cambiaron en ningún campo de las PDU.

**17. Cuando sigue la respuesta a un ping, a veces llamado estanque, ¿ve el cambio de envío y recepción de direcciones IPv4?**

Si se visualiza el cambio que existe entre el envió y la recepción de las direcciones IPv4.

**18. ¿Cuál es el patrón para el direccionamiento IPv4 utilizado en esta simulación?**

El patrón es cada puerto o interfaz del router debe manejar una ip diferente y cada dispositivo dentro de esta red que se dirigen en direcciones diferentes no deben solaparse, pero, deben estar dentro de esta red, aunque sean diferentes.

![image](https://github.com/Fx2048/COMU_TEAM/assets/151795724/8da39a41-9aa8-4247-91c1-1733cea31764)

**19. ¿Por qué se deben asignar diferentes redes IP a diferentes puertos en el router?**

Específicamente un router sirve para conectar redes, por lo que asignarlas sirve para interconectarlas, posteriormente. 

**20. Si esta simulación se configuró con IPv6 en lugar de IPv4, ¿qué sería diferente?**

Todo sería exactamente igual, lo único diferente es el formato, en cómo se maneja las direcciones de IP, ya que se manejan en versión IPv6 ya que manejan una dirección sexagesimal. 
