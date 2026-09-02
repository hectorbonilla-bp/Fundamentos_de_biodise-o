# INGENIERÍA BIOMÉDICA
## CICLO: 2026 - II
### ENTREGABLE 2

**Nombre de la Institución:** Universidad Peruana Cayetano Heredia - Pontificia Universidad Católica Del Perú  
**Facultad o Escuela:** Facultad Ciencias E Ingeniería | Estudios Generales Ciencias  
**Curso:** FUNDAMENTOS DE BIODISEÑO (4to ciclo - 2026)  
**Docentes:** Miguel Hoyos  

---

## TRABAJO DE INVESTIGACIÓN
### Placas de ordenador reducido (SBC) y tarjetas de desarrollo: comparación, pines, protocolos de comunicación y aplicaciones biomédicas

#### Integrantes
* Bonilla Pantoja, Héctor Guillermo
* Castro Huarsocca, Jahaira Q'uorianka
* Céspedes Huasacca Oscar Danilo
* Cuadros Huarcaya, Alonso Martín
* Custodio Gonzales, Diego Joel
* Guerra Egoavil, Marcela Lindaflor

---

## Índice
1. [Ventajas y desventajas de las placas de ordenador reducido (tipo Raspberry Pi)](#1-ventajas-y-desventajas-de-las-placas-de-ordenador-reducido-tipo-raspberry-pi)
2. [Ventajas y desventajas de las tarjetas de desarrollo (tipo Arduino)](#2-ventajas-y-desventajas-de-las-tarjetas-de-desarrollo-tipo-arduino)
3. [Tipos de pines](#3-tipos-de-pines)
4. [Protocolo de comunicación de las placas de ordenador reducido (tipo Raspberry Pi)](#4-protocolo-de-comunicación-de-las-placas-de-ordenador-reducido-tipo-raspberry-pi)
5. [Protocolo de comunicación de las tarjetas de desarrollo (tipo Arduino)](#5-protocolo-de-comunicación-de-las-tarjetas-de-desarrollo-tipo-arduino)
6. [Proyectos biomédicos con ambas plataformas](#6-proyectos-biomédicos-con-ambas-plataformas)
7. [Referencias bibliográficas](#referencias-bibliográficas)

---

## Introducción
En el ámbito de la electrónica embebida y el diseño de sistemas para la Internet de las Cosas (IoT), la robótica y la ingeniería biomédica, dos familias de placas se han vuelto referentes: las placas de ordenador reducido o SBC (Single Board Computer), representadas principalmente por la Raspberry Pi, y las tarjetas de desarrollo basadas en microcontrolador, cuyo máximo exponente es Arduino. Aunque ambas suelen usarse en proyectos similares, responden a arquitecturas y propósitos distintos: la primera es un ordenador completo en una sola placa capaz de ejecutar un sistema operativo, mientras que la segunda es un sistema mínimo orientado al control de entradas y salidas en tiempo real. El presente trabajo expone las ventajas y desventajas de cada plataforma, describe los tipos de pines disponibles, explica sus principales protocolos de comunicación y presenta ejemplos de aplicación en el campo biomédico.

---

## 1. Ventajas y desventajas de las placas de ordenador reducido (tipo Raspberry Pi)
Una placa de ordenador reducido o SBC es, según su definición general, una computadora completa construida sobre una única placa de circuito impreso, que integra procesador, memoria, controladores de entrada/salida y demás componentes que normalmente estarían distribuidos en varias tarjetas de una computadora convencional ([\\[1\\]](#ref-1), [\\[2\\]](#ref-2)).

### Tabla Comparativa: SBC (Raspberry Pi)

| Ventajas | Desventajas |
| :--- | :--- |
| • Es un ordenador completo: puede ejecutar sistemas operativos como Raspberry Pi OS, Ubuntu, DietPi o RetroPie, entre otros basados en Linux. | • No tiene entradas analógicas nativas, por lo que requiere módulos ADC externos para leer sensores analógicos. |
| • Bajo consumo energético: una Raspberry Pi 4 consume entre 3,8 y 5,5 W según la carga, frente a los 65-250 W de un ordenador de escritorio. | • Depende de un sistema operativo y de una tarjeta microSD, lo que la hace menos robusta ante cortes de energía repentinos (riesgo de corrupción de datos). |
| • Tamaño reducido y portabilidad, ideal para proyectos con espacio limitado. | • Tiempos de arranque más largos que un microcontrolador, que ejecuta su programa de forma casi inmediata. |
| • Amplia documentación oficial y una comunidad de usuarios muy grande, lo que facilita el aprendizaje. | • No es un sistema de tiempo real: al correr un sistema operativo, no garantiza tiempos de respuesta exactos, algo crítico en control industrial o médico. |
| • Conectividad completa: puertos USB, HDMI, Ethernet, Wi-Fi, Bluetooth y ranura para tarjeta microSD. | • Mayor consumo eléctrico y complejidad que una tarjeta de desarrollo simple como Arduino. |
| • Permite ejecutar múltiples procesos y aplicaciones a la vez (multitarea real) y correr lenguajes de alto nivel como Python. | • El hardware de los modelos más recientes puede quedar rápidamente desactualizado frente a la competencia. |
| • Cuenta con pines GPIO que permiten interactuar con sensores y actuadores igual que una tarjeta de desarrollo. | |

> *Fuentes de soporte de la sección:* [\\[3\\]](#ref-3), [\\[4\\]](#ref-4), [\\[5\\]](#ref-5).

---

## 2. Ventajas y desventajas de las tarjetas de desarrollo (tipo Arduino)
Arduino es una plataforma de electrónica de código abierto basada en hardware y software libres, construida alrededor de un microcontrolador (típicamente de la familia Atmel/AVR o ARM). A diferencia de un SBC, no ejecuta un sistema operativo: el programa (denominado "sketch") se graba directamente en la memoria del microcontrolador y se ejecuta de manera continua y determinista ([\\[6\\]](#ref-6), [\\[7\\]](#ref-7)).

### Tabla Comparativa: Tarjetas de Desarrollo (Arduino)

| Ventajas | Desventajas |
| :--- | :--- |
| • Bajo costo y accesibilidad: las placas y módulos son económicos frente a otras plataformas de microcontroladores. | • Memoria RAM y capacidad de procesamiento limitadas, lo que restringe proyectos complejos (imagen, redes, cálculo intensivo). |
| • Facilidad de uso: entorno de programación (IDE) simple, basado en un lenguaje similar a C/C++, adecuado para principiantes. | • No permite ejecutar un sistema operativo ni tareas multihilo reales. |
| • Multiplataforma: el software funciona en Windows, macOS y Linux. | • Carece de salida de vídeo, red o interfaces de alto nivel sin módulos adicionales. |
| • Gran cantidad de bibliotecas y proyectos de código abierto disponibles, lo que acelera el desarrollo. | • Al ser una plataforma ya ensamblada, ofrece menos flexibilidad de diseño de PCB que trabajar con un microcontrolador "a medida". |
| • Estandarización de pines ("shields"): existe un enorme ecosistema de módulos de expansión compatibles. | • Para proyectos avanzados de conectividad (Wi-Fi, Ethernet, Bluetooth) requiere módulos o shields extra, incrementando costo y complejidad de cableado. |
| • Comportamiento predecible y en tiempo real, ya que no depende de un sistema operativo ni de procesos en segundo plano. | • El aprendizaje con Arduino simplifica tanto el proceso que puede limitar la comprensión profunda de la electrónica y programación de bajo nivel de un microcontrolador. |
| • Arranque inmediato y bajo consumo, apto para proyectos que funcionan con baterías. | |

> *Fuentes de soporte de la sección:* [\\[8\\]](#ref-8), [\\[9\\]](#ref-9), [\\[10\\]](#ref-10).

---

## 3. Tipos de pines
Tanto las placas SBC como las tarjetas de desarrollo exponen distintos tipos de pines o terminales para alimentar, controlar y comunicar la placa con el mundo exterior. Los principales tipos son:

| Tipo de pin | Función principal | Presencia típica |
| :--- | :--- | :--- |
| **Alimentación (5V, 3.3V, GND)** | Suministran energía a la placa y a los módulos externos, y proporcionan la referencia de tierra (0V) común. | Raspberry Pi y Arduino |
| **Digitales (GPIO)** | Entrada/Salida de propósito general; leen o generan señales binarias (alto/bajo, 0 o 1) para botones, LEDs, relés, etc. | Raspberry Pi y Arduino |
| **Analógicos (entrada ADC)** | Leen voltajes variables y los convierten en un valor digital proporcional (sensores de temperatura, luz, potenciómetros). | Arduino (nativo); Raspberry Pi requiere un ADC externo, pues sus GPIO son solo digitales |
| **PWM (Pulse Width Modulation)** | Generan una señal digital que simula una salida analógica variando el ancho de pulso; se usan para controlar brillo de LEDs, velocidad de motores o servos. | Ambas (en Arduino son pines específicos marcados con `~`; en Raspberry Pi, PWM por hardware o software) |
| **Comunicación serie (UART: TX/RX)** | Transmiten y reciben datos en serie, un bit tras otro, entre la placa y otros dispositivos. | Raspberry Pi y Arduino |
| **I2C (SDA/SCL)** | Bus serie de dos hilos (datos y reloj) para comunicar varios dispositivos esclavos con un maestro. | Raspberry Pi y Arduino |
| **SPI (MOSI, MISO, SCLK, CS)** | Bus serie síncrono de alta velocidad, con líneas separadas de datos de entrada y salida más una línea de selección de dispositivo. | Raspberry Pi y Arduino |
| **Reset** | Reinicia la ejecución del programa o del sistema. | Ambas |
| **Pines especiales (interrupciones externas, cristal, ICSP)** | Permiten funciones avanzadas como interrupciones por hardware o programación directa del microcontrolador. | Principalmente Arduino |

> *Fuentes de soporte de la sección:* [\\[11\\]](#ref-11), [\\[12\\]](#ref-12), [\\[13\\]](#ref-13).

---

## 4. Protocolo de comunicación de las placas de ordenador reducido (tipo Raspberry Pi)
La Raspberry Pi cuenta con un conector de 40 pines (denominado J8) del cual 26 son pines GPIO de propósito general. Además de funcionar como entradas o salidas digitales simples, algunos de estos pines pueden configurarse en "modo alternativo" para operar como interfaces de comunicación estandarizadas. Es importante señalar que la lógica de los GPIO de la Raspberry Pi trabaja a 3,3 V y no es tolerante a 5 V, por lo que conectar dispositivos de 5 V sin un adaptador de nivel puede dañar la placa ([\\[14\\]](#ref-14)).

### Principales protocolos
* **I2C (Inter-Integrated Circuit):** bus serie de dos hilos (`SDA` para datos y `SCL` para reloj) que sigue una relación maestro-esclavo. La Raspberry Pi puede administrar varios dispositivos I2C simultáneamente identificándolos por una dirección única; es adecuado para sensores y módulos de baja velocidad como relojes en tiempo real (RTC).
* **SPI (Serial Peripheral Interface):** protocolo síncrono de mayor velocidad que I2C, que utiliza líneas separadas para el reloj (`SCLK`), datos de salida (`MOSI`), datos de entrada (`MISO`) y selección de dispositivo (`Chip Select`). Es común en pantallas pequeñas y módulos que requieren alta velocidad de transferencia.
* **UART (Universal Asynchronous Receiver-Transmitter):** comunicación serie asíncrona (líneas `TX` y `RX`) usada tradicionalmente para conectar la Raspberry Pi con microcontroladores u otros dispositivos serie.
* **GPIO como E/S general:** cuando no se usan como bus, muchos de estos mismos pines pueden emplearse como entradas o salidas digitales simples.

> *Fuentes de soporte:* [\[15\]](#ref-15), [\[16\]](#ref-16), [\[17\]](#ref-17)

Además de estos buses de bajo nivel, la Raspberry Pi —al ser un ordenador completo— también soporta de forma nativa protocolos de red de alto nivel como **Ethernet, Wi-Fi y Bluetooth**, lo que la hace especialmente apta para aplicaciones de IoT y monitoreo remoto en tiempo real.

---

## 5. Protocolo de comunicación de las tarjetas de desarrollo (tipo Arduino)
Las placas Arduino, al estar basadas en microcontroladores AVR o ARM, integran de fábrica los mismos tres buses de comunicación estándar que se emplean en la mayoría de sistemas embebidos, aunque implementados directamente por el hardware del microcontrolador (UART, SPI e I2C/TWI):

* **UART/Serie:** Arduino se comunica de forma nativa por puerto serie con la computadora (por USB, a través de un chip conversor USB-serie) y también puede comunicarse con otros dispositivos a través de los pines `TX`/`RX`. Es el protocolo más simple, sin verificación de errores, salvo el bit de paridad opcional.
* **I2C** (llamado *"TWI"*, Two Wire Interface, en el hardware Atmel): bus de dos hilos (`SDA`/`SCL`) gestionado normalmente mediante la biblioteca estándar `Wire.h`; permite conectar múltiples sensores o módulos (pantallas OLED, sensores de movimiento, RTC) usando solo dos líneas más alimentación y tierra.
* **SPI:** bus síncrono de cuatro líneas (`MOSI`, `MISO`, `SCK` y `SS`/`CS`) gestionado mediante la biblioteca `SPI.h`, utilizado para módulos que requieren mayor velocidad, como tarjetas SD, pantallas o módulos de red Ethernet.

> *Fuentes de soporte:* [\[16\]](#ref-16), [\[6\]](#ref-6)

A diferencia de la Raspberry Pi, Arduino no incluye de fábrica Wi-Fi, Ethernet o Bluetooth (salvo en variantes específicas como el Arduino Uno WiFi o el ESP32, compatible con el mismo entorno); para añadir estas capacidades se recurre a módulos o *shields* adicionales que a su vez suelen comunicarse con la placa principal mediante alguno de los tres buses mencionados (por ejemplo, un módulo ESP8266 vía UART, o un módulo Ethernet vía SPI).

---

## 6. Proyectos biomédicos con ambas plataformas
Gracias a su bajo costo y a la disponibilidad de sensores comerciales, tanto Arduino como Raspberry Pi se emplean ampliamente en el desarrollo de prototipos y sistemas de monitoreo biomédico, especialmente en investigación académica y en soluciones de salud electrónica (e-Health) de código abierto. Cabe resaltar que, en general, **estos prototipos no cuentan con certificación médica** y se orientan a fines educativos, de investigación o de prueba de concepto.

### Ejemplos de aplicación
* **Plataforma e-Health Sensor Shield (Cooking Hacks / Libelium):** un módulo compatible tanto con Arduino como con Raspberry Pi que integra hasta diez sensores biomédicos: pulso, oxigenación en sangre (SpO2), electrocardiograma (ECG), electromiografía (EMG), flujo de aire/respiración, temperatura corporal, glucosa, respuesta galvánica de la piel (GSR), presión arterial y posición corporal (acelerómetro). Los datos pueden transmitirse de forma inalámbrica por Wi-Fi, Bluetooth, ZigBee, 3G o GPRS.
* **Monitores de frecuencia cardíaca y oximetía:** usando sensores como el pulsioxímetro `MAX30100`/`MAX30102` conectados por I2C, tanto a Arduino como a Raspberry Pi, para registrar la frecuencia cardíaca y la saturación de oxígeno en tiempo real.
* **Monitores del sueño:** dispositivos basados en Arduino con sensores de electroencefalografía (EEG) y pantallas OLED que registran patrones de sueño y actividad cerebral.
* **Calculadoras de composición corporal:** dispositivos con sensores de bioimpedancia conectados a Arduino para estimar el porcentaje de grasa corporal.
* **Sistemas de historia clínica electrónica (EMR) e imágenes médicas (PACS/DICOM) sobre Raspberry Pi:** al ser un ordenador completo, la Raspberry Pi puede alojar pequeños servidores de registros médicos electrónicos o visores de imágenes DICOM de bajo costo para clínicas con recursos limitados.
* **Monitores de frecuencia cardíaca por Bluetooth de bajo costo:** reciben datos de bandas de pulso comerciales y los visualizan en una Raspberry Pi.

> *Fuentes de soporte:* [\[18\]](#ref-18), [\[19\]](#ref-19), [\[20\]](#ref-20)

### Rol complementario de ambas plataformas
En muchos proyectos biomédicos reales, Arduino y Raspberry Pi se combinan: el microcontrolador Arduino se encarga de la **adquisición de señales en tiempo real** desde los sensores (ECG, pulso, temperatura), tarea en la que su comportamiento determinista es una ventaja, mientras que la Raspberry Pi recibe esos datos —típicamente por UART, I2C o USB serie— y se encarga del **procesamiento más pesado**, el almacenamiento, la visualización gráfica y el envío de la información a la nube o a una red hospitalaria.

---

## Referencias bibliográficas

* <a id="ref-1"></a> **[1]** Raspberry Pi Ltd, "Raspberry Pi computer hardware," *Raspberry Pi Documentation*. [Disponible en línea](https://www.raspberrypi.com/documentation/computers/raspberry-pi.html).
* <a id="ref-2"></a> **[2]** J. Cruz-Benito, F. J. García-Peñalvo, and R. Therón, "Understanding the role of single-board computers in engineering and computer science education: A systematic literature review," *arXiv:2203.16604*, 2022. [Disponible en línea](https://arxiv.org/pdf/2203.16604).
* <a id="ref-3"></a> **[3]** Opensource.com, "What is a Raspberry Pi?" *Red Hat, Inc.* [Disponible en línea](https://opensource.com/resources/raspberry-pi).
* <a id="ref-4"></a> **[4]** Raspberry Pi Ltd, "Raspberry Pi OS," *Raspberry Pi Documentation*. [Disponible en línea](https://www.raspberrypi.com/documentation/computers/os.html).
* <a id="ref-5"></a> **[5]** "Comparative Study of Microcontroller: ESP32, Arduino Uno & Raspberry Pi 4," *International Journal for Research in Applied Science and Engineering Technology (IJRASET)*, 2023. [Disponible en línea](https://www.ijraset.com/best-journal/comparative-study-of-microcontroller-esp32-arduino-uno-raspberry-pi-4).
* <a id="ref-6"></a> **[6]** Arduino Documentation, "What is Arduino?" *Arduino S.r.l.* [Disponible en línea](https://docs.arduino.cc/learn/starting-guide/whats-arduino/).
* <a id="ref-7"></a> **[7]** Arduino Documentation, "Getting Started with Arduino." [Disponible en línea](https://docs.arduino.cc/learn/starting-guide/getting-started-arduino/).
* <a id="ref-8"></a> **[8]** Arduino Documentation, "Language Reference." [Disponible en línea](https://docs.arduino.cc/language-reference/).
* <a id="ref-9"></a> **[9]** Arduino Documentation home page. [Disponible en línea](https://docs.arduino.cc/).
* <a id="ref-10"></a> **[10]** "Comparative Study of Microcontroller: ESP32, Arduino Uno & Raspberry Pi 4," *International Journal for Research in Applied Science and Engineering Technology (IJRASET)*, 2023. [Disponible en línea](https://www.ijraset.com/best-journal/comparative-study-of-microcontroller-esp32-arduino-uno-raspberry-pi-4).
* <a id="ref-11"></a> **[11]** Raspberry Pi Ltd, "Raspberry Pi computer hardware" (GPIO section), *Raspberry Pi Documentation*. [Disponible en línea](https://www.raspberrypi.com/documentation/computers/raspberry-pi.html#gpio).
* <a id="ref-12"></a> **[12]** Arduino Documentation, "Language Reference" (analogRead, analogWrite, digitalRead/Write). [Disponible en línea](https://docs.arduino.cc/language-reference/).
* <a id="ref-13"></a> **[13]** pinout.xyz, "Raspberry Pi GPIO Pinout" (interactive pin reference maintained with Raspberry Pi Ltd data). [Disponible en línea](https://pinout.xyz/).
* <a id="ref-14"></a> **[14]** Raspberry Pi Ltd, "Raspberry Pi computer hardware" (GPIO voltage specifications), *Raspberry Pi Documentation*. [Disponible en línea](https://www.raspberrypi.com/documentation/computers/raspberry-pi.html#gpio).
* <a id="ref-15"></a> **[15]** Raspberry Pi Ltd, "Raspberry Pi OS" (hardware communication: I2C, SPI, UART), *Raspberry Pi Documentation*. [Disponible en línea](https://www.raspberrypi.com/documentation/computers/os.html).
* <a id="ref-16"></a> **[16]** Arduino Documentation, "Language Reference" (Wire and SPI communication libraries). [Disponible en línea](https://docs.arduino.cc/language-reference/).
* <a id="ref-17"></a> **[17]** Raspberry Pi Ltd, "Raspberry Pi computer hardware" (GPIO alternate functions), *Raspberry Pi Documentation*. [Disponible en línea](https://www.raspberrypi.com/documentation/computers/raspberry-pi.html#gpio).
* <a id="ref-18"></a> **[18]** "Healthcare Monitoring System and transforming Monitored data into Real time Clinical Feedback based on IoT using Raspberry Pi," in *Proc. IEEE Conf.*, 2019. [Disponible en línea](https://ieeexplore.ieee.org/document/8673393/).
* <a id="ref-19"></a> **[19]** K. Ain, R. A. Wibowo, and S. Soelistiono, "Design and development of a low-cost Arduino-based electrical bioimpedance spectrometer," *Journal of Medical Signals and Sensors*, vol. 10, no. 2, pp. 125-133, 2020. [Disponible en línea](https://pmc.ncbi.nlm.nih.gov/articles/PMC7359956/).
* <a id="ref-20"></a> **[20]** O. A. Paiva et al., "Raspberry Pi: a 35-dollar device for viewing DICOM images," *Radiologia Brasileira*, vol. 47, no. 2, pp. 129-130, 2014. [Disponible en línea](https://pmc.ncbi.nlm.nih.gov/articles/PMC4337158/).
