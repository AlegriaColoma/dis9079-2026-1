# sesion-02

lunes 16 marzo 2026
Grupo de 2 con Agustina Aceituno


##  GitHub y Markdown


Hablamos del github y markdown para registrar nuestros apuntes 


## Open Source y OSHWA


El concepto Open Source (código abierto) se refiere a proyectos cuyo diseño o código puede ser accedido, modificado y distribuido libremente.


En el caso del hardware existe la organización Open Source Hardware Association (OSHWA), que promueve el desarrollo de hardware abierto. Esta organización certifica proyectos que cumplen con los principios de transparencia, acceso y libertad de uso para los usuarios.


## Arduino


Arduino es una plataforma que combina hardware (placas electrónicas) y software (IDE para programarlas).


Se programa principalmente usando C++.


Un programa básico de Arduino siempre tiene dos partes principales:
```cpp
setup()
```
Se ejecuta una sola vez al iniciar el programa. Se usa para configurar el sistema.
```cpp
loop()
```
Se ejecuta repetidamente en un ciclo infinito.


Ejemplo:
```cpp
void setup() {
  // configuraciones iniciales
}


void loop() {
  // instrucciones que se repiten
}
```
### Arduino UNO R4 WiFi


En el curso se trabaja con la Arduino UNO R4 WiFi, una placa reciente que incluye conexión inalámbrica.


En el Arduino IDE es necesario instalar:


- Boards Manager


   - Arduino UNO R4 Boards


- Bibliotecas


   - Arduino MQTTClient
   - Arduino Graphics


Estas bibliotecas permiten agregar funciones extra, como manejar pantallas o comunicarse por red.


## Versionamiento Semántico (SemVer)


Muchos proyectos utilizan un sistema de versiones llamado Semantic Versioning, que sigue la estructura:
```cpp
mayor.menor.parche
ej: 0.1.8
```
Cada número indica el tipo de cambio realizado:


- Mayor
Cambios grandes que ya no son compatibles con versiones anteriores.
- Menor
Nuevas funciones que siguen siendo compatibles.
- Parche
Correcciones de errores o mejoras pequeñas.


## MQTT


MQTT (Message Queuing Telemetry Transport) es un protocolo de comunicación ligero pensado para el Internet de las Cosas (IoT).


Sus características principales:


- Funciona sobre TCP/IP
- Utiliza un modelo de publicación y suscripción
- Está diseñado para dispositivos con pocos recursos o redes inestables


Los dispositivos no se comunican directamente entre sí, sino a través de un broker.


### Broker


El broker actúa como intermediario que recibe y distribuye los mensajes.


Un broker muy utilizado es Mosquitto.


Proyecto:
https://github.com/eclipse-mosquitto/mosquitto


Configuración típica:


- IP del broker
- Puerto: 1883
- Topic: canal donde se envían o reciben mensajes


Ejemplo:
```cpp
broker: 10.174.124.28
port: 1883
topic: asistencia/20260316
```


## Mosquitto


Mosquitto es un programa que permite crear un broker MQTT.
Su función es manejar el intercambio de mensajes entre distintos dispositivos conectados.


En una red con MQTT pueden existir muchos dispositivos:


- Algunos publican mensajes
- Otros se suscriben a un topic


El broker se encarga de distribuir los mensajes a quienes estén suscritos.


## Ejemplo


Se revisó un ejemplo en el que el Arduino UNO R4 WiFi muestra texto desplazándose en su pantalla LED.


Para ello se utilizan las bibliotecas:


- ArduinoGraphics
- Arduino_LED_Matrix


El código crea una instancia de la pantalla, inicializa la comunicación serial y luego escribe un texto que se mueve hacia la izquierda en la matriz LED.


## Conexión WiFi y MQTT


Para conectarse a la red se usa un archivo separado con las credenciales:


arduino_secrets.h
```cpp
#define SECRET_SSID "nombre_wifi"
#define SECRET_PASS "clave_wifi"
```
Luego el Arduino:

1. Se conecta a la red WiFi
2. Se conecta al broker MQTT
3. Se suscribe a un topic
4. Espera mensajes
Cuando llega un mensaje, el Arduino lo lee y lo imprime en el monitor serial.

## Solemne 1

La primera evaluación consiste en conectar dos placas Arduino distintas y lograr que se comuniquen entre sí mediante MQTT.

Esto implica:

- Configurar la conexión WiFi
- Conectarse al broker Mosquitto
- Usar el mismo topic
- Enviar y recibir mensajes entre placas

## Herramientas mencionadas

Algunas herramientas o conceptos que también aparecieron en la clase:

- Homebrew

Sistema para instalar programas desde la terminal.

- Bash

Lenguaje de comandos que permite automatizar acciones en la terminal.

- OSC (Open Sound Control)

Otro protocolo de comunicación usado en sistemas interactivos.


