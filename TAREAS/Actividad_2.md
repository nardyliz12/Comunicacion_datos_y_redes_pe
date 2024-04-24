# ACTIVIDAD 2: IMPLEMENTACIÓN DE UNA CONECTIVIDAD BÁSICA 

### Tabla de asignación de direcciones

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/17408c87-5075-4b0f-903e-eb5eb900682c)

#### Objetivos
- Parte 1: Realizar una configuración básica en S1 y S2
- Paso 2: Configurar las PC
- Parte 3: Configurar la interfaz de administración de switches
- 
### 1.- Realiza una configuración básica en el S1 y el S2.
![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/d03c7b8a-2f83-4935-af31-38fd7ed0345d)

#### Configura un nombre de host en el S1.
![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/4fc684de-4d21-446c-82ed-e86b85e3a3fa)
#### Configura la consola y las contraseñas cifradas de modo EXEC privilegiado.

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/64cf4848-cff6-4890-b751-6bbe49e6ac2b)

#### Verifica la configuración de contraseñas para el S1.

- **¿Cómo puedes verificar que ambas contraseñas se hayan configurado correctamente?**
Se puede realizar de dos maneras:

- **PRIMERO:
  ![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/a0f02f68-2840-4c9f-8360-9a17ba1db7b4)

- **SEGUNDO:**
Es salir de toda la configuración poniendo un *exit*, y una ves de haber salido hacemos un *enter*, y nos saldra un *User Access Verification* para poder ingresar la contraseña y nuevamente ingresar a la configuación.

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/710fcaa1-bade-444c-bf8e-947682f503ed)

#### Configura un aviso de MOTD.
*"Acceso autorizado únicamente. Los infractores se procesarán en la medida en que lopermita la ley."*

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/6ce9e35e-696b-4c0d-a88c-55bc67733b8b)

#### Guarda el archivo de configuración en la NVRAM

- **¿Qué comando emite para realizar este paso?**
 
Nosotros paraa guardar de lo que hemos hecho de la RAM a la NVRAM tenemos que hacer lo siguiente:

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/4f801584-9bcd-4024-91c8-09a8d09a0f54)

### 2.- repita los pasos  1 a 5 para el S2:

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/8604aac8-9d55-4d49-8572-ab5162212ded)

#### configurar las PC

- **PC1:**
![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/4c52d9e1-890b-403f-b131-12ac3a4f814c)

- **PC2:**
  
![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/04c8adc5-4a0a-464f-8fbf-c58a3ed94721)

#### Prueba la conectividad a los switches.

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/9ff62e05-8ac7-4868-91ac-96f1b7c9eef3)

- **¿Tuviste existo? Explica.**
No tuvo exito, porque no hemos configurado todavia una dirección IP al switches, donde es una dirección de administración, y ello no tuvo exito.

### 3.- Configura la interfaz de administración de switches
#### Configura el S1 con una dirección IP.

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/9923798d-e1e3-48dc-bcfd-9538cec24b2b)

- **¿Por qué debe introducir el comando no shutdown?**

Ingresamos *no shutdown* basicamente para que se habilite la dirección en esta interfaz de vlan 1.

#### Configura el S2 con una dirección IP.

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/b7e53c55-adbc-4c85-b2cd-8a424d075c5e)

#### Verifica la configuración de direcciones IP en el S1 y el S2

- **Para S2:**
  
![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/9d1475bc-2d07-4c6f-b024-0d5c2ff9fe4d)

- **Para S1:**
  
![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/7f1fd4ae-d8b5-4ece-a6f2-c662a337f33d)

#### Guarda la configuración para el S1 y el S2 en la NVRAM
- **S1:**
![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/a50eb047-e502-4264-bcc2-4a4b23eee4bb)

- **S2**
  
![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/c56ca43f-aabb-4591-ac61-db5362d086f7)

- **¿Qué comando se utiliza para guardar en la NVRAM el archivo de configuración que se encuentra enla RAM?**
  
Se tiene que poner *copy running-config st* para que se guarde de la RAM a la NVRAM, tanto paraa ese S1 y S2.

#### Verifica la conectividad de la red.

- **PC1 con direccción IP de PC2, muestra tener exito.**

![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/4c6ae587-0cd1-4f85-a336-b368d99a237b)


- **PC1 con direccción de S1, muestra tener exito.**
  
![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/471ccc2f-d285-45c7-8fa6-8d0d640f9bb5)

- **PC1 con direccción de S2, muestra tener exito.**
  
![image](https://github.com/nardyliz12/Comunicacion_datos_y_redes_pe/assets/151795724/eb750141-22a4-4462-bb47-64d1e71adbf1)

  
