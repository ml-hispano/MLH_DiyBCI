# MLH_OpenBCI

![MLHispano OpenBCI](docs/mlh-neuro.png)

Desarrollo del electroencefalógrafo OpenBCI con el mínimo coste.

# Introducción

Este es nuestro cuaderno de bitácora navegando por las profundas aguas de la neurociencia. En él queremos recopilar toda la información relevante para el proyecto y documentar su desarrollo.

Se trata de conseguir un dispositivo [BCI](https://es.wikipedia.org/wiki/Interfaz_cerebro-computadora) a precio asequible, capaz de registrar las ondas cerebrales mediante [EEG](https://es.wikipedia.org/wiki/Electroencefalograf%C3%ADa) de un individuo, que servirá como punto de partida para que cualquiera pueda experimentar y desarrollar sus propias aplicaciones a partir del análisis y tratamiento de las mismas.

Una de las primeras cuestiones que surgió es la posibilidad de hacer una lista de materiales para elaborar un dispositivo de características similares a los ofrecidos por OpenBCI para tratar de contener el precio del experimento. El proyecto se encuentra en fase inicial de desarrollo.


!!! Atención
   Este es un proyecto amateur de aprendizaje, no un proyecto científico riguroso, podría contener errores, contribuye y ayudanos a resolverlos.


## Agradecimientos

- [OpenBCI](https://openbci.com/)
- Todos los colaboradores, extensiones y librerías que hacen posible este proyecto.

## Lista de materiales

- [Octopart (componentes)](https://octopart.com/bom-tool/86yT1jZ5)
- [Descargar lista de materiales](docs/openbci_cyton.csv)
- [Diseño del circuito impreso de OpenBCI Cyton](https://github.com/OpenBCI/V3_Hardware_Design_Files/tree/master/OpenBCI%20Cyton%20Designs)
- [Interfaz gráfica](https://github.com/OpenBCI/OpenBCI_GUI)

## Recursos adicionales

- [Documentación](https://docs.openbci.com/Getting%20Started/00-Welcome)
- La idea surgió, a partir de un hilo del canal [#banco_de_proyectos](https://ml-hispano.slack.com/archives/CF77D1BDH/p1555498224002300) de la comunidad de Slack [Machine Learning Hispano](https://bit.ly/2Oqingj) a partir de los comentarios sobre este artículo de Hackaday [Brain Hacking with Entrainment](https://hackaday.com/2019/04/08/brain-hacking-with-entrainment/)
- Existe una campaña en indiegogo para un dispositivo con características similares a lo que buscamos, creo que el proyecto se encuentra en un punto importante de su desarrollo, en el que se decidirá si progresa o fracasa, a pesar de que resulta bastante caro me parece interesante por las ideas y conclusiones que podemos sacar, se llama [Mindset](https://www.indiegogo.com/projects/mindset-smart-headphones-that-improve-your-focus)
- [Low-intensity ultrasound can change decision-making process in the brain](https://www.sciencedaily.com/releases/2019/04/190415113822.htm)

## Instalación del firmware con Wifi Shield (sin Bluetooth)

![WiFiShield](docs/WiFiShield.jpg)

WiFi Shield permite omitir fácilmente los puertos serie llenos de latencia y las conexiones Bluetooth de bajo rango. Además, Wifi Shield te permite transmitir más rápido y más lejos que con el hardware predeterminado basado en Bluetooth.
Información extraida de este [hilo](https://openbci.com/forum/index.php?p=/discussion/1773/is-cyton-programming-possible-without-using-bluetooth-dongle#latest).

- Utilizar PICKit3 para programar el hex del cargador de arranque en el PIC32 con MPLAB IPE a través de los encabezados.
- Usar un adaptador FTDI (velocidad en baudios: 115,200 b/s) para programar el firmware de Cyton en el PIC32 con Arduino IDE soldando temporalmente los pads 3 (RXD) y 4 (TXD) de donde debería haber estado el RFDuino .
- Utilizar un adaptador FTDI (velocidad en baudios: 115.200 b/s) para programar el firmware "BoardWithWifi" de WiFi Shield en el ESP8266 con el terminal a través de esptool.
- Conectar WiFi Shield a 5V de alimentación externa (SW4: on), encenderlo y cambiar su configuración para conectarse a la red inalámbrica de tu hogar.
- Apagar el WiFi Shield y conectarlo a la placa Cyton.
- Al conectar el WiFi Shield a 5V de alimentación externa (SW4: on), debería encendenderse y transmitir los datos a través de OpenBCI GUI.
- Con el WiFi Shield montado en la placa Cyton y el WiFi Shield conectado a la alimentación externa (SW4: on), ambas placas están encendidas y todos los LED azules (WiFi Shield: D2, D3, D4 y Cyton: D1) permanecen encendidos. Usando una fuente de 5V, las dos tablas están dibujando 120 mA.
