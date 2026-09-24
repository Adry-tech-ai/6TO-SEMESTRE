## QUE ES SOHO
En el ámbito de la red y el entorno laboral, SOHO es un acrónimo en inglés que significa Small Office / Home Office ("Pequeña oficina / Oficina en casa

Se refiere al segmento de mercado, equipos de red (como routers Wi-Fi domésticos/profesionales) o soluciones de software diseñadas para autónomos, teletrabajadores o microempresas de pocos empleados

---

## 1. STP (Spanning Tree Protocol)

El **Spanning Tree Protocol** (Protocolo de Árbol de Expansión) es un protocolo de red de capa 2 (enlace de datos) cuyo objetivo principal es **prevenir bucles (loops) en redes de área local (LAN)** que cuentan con enlaces redundantes.

### ¿Por qué es necesario?
Para garantizar alta disponibilidad y tolerancia a fallos, las redes suelen diseñarse con caminos alternativos (enlaces redundantes). Sin embargo, en las redes de nivel 2, si existen múltiples caminos sin control, las tramas de difusión (*broadcasts*) pueden circular indefinidamente en un bucle infinito, colapsando los switches y saturando la red (tormenta de *broadcasts*).

### ¿Cómo funciona?
STP utiliza el algoritmo **STA (Spanning Tree Algorithm)** para calcular un árbol de expansión lógico dentro de la topología física de la red. 
1. **Elección del Puente Raíz (*Root Bridge*):** Todos los switches de la red se comunican mediante tramas especiales llamadas **BPDU** (*Bridge Protocol Data Units*) para elegir al switch con la prioridad más baja (o dirección MAC más antigua) como el centro o "cerebro" de la red.
2. **Cálculo de Costes:** Los demás switches calculan el camino más corto (en función del ancho de banda del enlace) para llegar al *Root Bridge*.
3. **Bloqueo de Puertos:** Los puertos redundantes que crearían un bucle se colocan en estado de **bloqueo** (*blocking*), de modo que no retransmiten tráfico de datos normal, pero siguen escuchando BPDUs. Si el enlace principal falla, STP recalcula la topología y habilita el puerto alternativo de forma automática.

### Estados de los puertos en STP clásico (IEEE 802.1D):
* **Disabled (Deshabilitado):** El puerto está apagado administrativamente.
* **Blocking (Bloqueo):** No reenvía tráfico, solo escucha BPDUs (evita bucles). Pasa a este estado al iniciar.
* **Listening (Escucha):** Procesa BPDUs para determinar la topología y asegura que no hay bucles antes de enviar datos.
* **Learning (Aprendizaje):** Empieza a aprender direcciones MAC de los dispositivos conectados, pero aún no reenvía tráfico de usuario.
* **Forwarding (Reenvío):** El puerto opera con normalidad, envía y recibe tráfico de datos y BPDUs.

> *Nota moderna:* Variantes como **RSTP (Rapid Spanning Tree Protocol - 802.1w)** reducen drásticamente los tiempos de convergencia de segundos a milisegundos.

---

## 2. FTP (File Transfer Protocol)

El **File Transfer Protocol** (Protocolo de Transferencia de Archivos) es un protocolo de red estándar perteneciente a la capa de aplicación del modelo OSI / TCP/IP, diseñado específicamente para **transferir archivos entre un cliente y un servidor** a través de una red TCP/IP.

### Características Principales:
* **Orientado a conexión:** Utiliza el protocolo **TCP** para garantizar que los datos se entreguen de manera confiable y sin errores.
* **Arquitectura Cliente-Servidor:** Un equipo actúa como servidor FTP (almacenando los archivos) y el otro como cliente (software o terminal que solicita o envía archivos).
* **Autenticación:** Por lo general, requiere un nombre de usuario y una contraseña (aunque existe el modo *Anonymous FTP* para descargas públicas).

### Arquitectura de Puertos (Conexión Dual):
Una de las particularidades más distintivas de FTP es que utiliza **dos canales independientes** para funcionar:
1. **Puerto de Control (Puerto 21):** Se utiliza para enviar los comandos del cliente (como iniciar sesión, cambiar de directorio, solicitar un archivo) y recibir las respuestas del servidor. Permanece abierto durante toda la sesión.
2. **Puerto de Datos (Puerto 20 por defecto en modo activo):** Se abre temporalmente cada vez que se necesita transferir el contenido real de un archivo (subir o bajar documentos, imágenes, etc.).

### Modos de Operación:
* **Modo Activo (Active Mode):** El cliente abre un puerto aleatorio y le indica al servidor a qué puerto conectarse para la transferencia de datos. *(Problema común: los firewalls del lado del cliente suelen bloquear esta conexión entrante).*
* **Modo Pasivo (Passive Mode - PASV):** Es el más utilizado hoy en día. Es el cliente quien inicia ambas conexiones (tanto la de control como la de datos). El servidor le indica al cliente un puerto aleatorio en el que se quedará escuchando para recibir la conexión de datos, evitando bloqueos de firewalls en el cliente.

### Limitación de Seguridad:
El FTP tradicional transmite las credenciales (usuario y contraseña) y los datos en **texto plano**, lo que lo hace vulnerable a ataques de interceptación (*sniffing*). Por esta razón, en entornos modernos se prefieren alternativas seguras como **SFTP** (Secure File Transfer Protocol, sobre SSH) o **FTPS** (FTP over SSL/TLS).

---

# Resumen: UPS (Uninterruptible Power Supply)

## ¿Qué es un UPS?
Un **UPS** (por sus siglas en inglés, *Uninterruptible Power Supply*, o **SAI** - *Sistema de Alimentación Ininterrumpida* en español) es un dispositivo eléctrico que proporciona energía de emergencia a una carga cuando la fuente de energía de entrada (la red eléctrica principal) falla o cae a niveles inaceptables.

A diferencia de un supresor de picos o un regulador simple, un UPS incluye baterías que garantizan **continuidad operativa inmediata** ante un corte de energía, evitando la pérdida de datos, daños en equipos sensibles y caídas de sistemas críticos.

---

## Funciones Principales
1. **Suministro de energía ininterrumpida:** Mantiene encendidos dispositivos críticos (servidores, equipos de red, computadoras) durante un apagón para permitir un apagado seguro o mantener la operación.
2. **Protección contra fluctuaciones eléctricas:** Filtra y estabiliza la corriente, protegiendo contra:
   * Sobretensiones y picos de voltaje.
   * Bajadas de tensión (*sags* o *brownouts*).
   * Ruido eléctrico e interferencias de frecuencia.
   * Distorsiones en la onda de corriente alterna.

---

## Topologías de UPS (Tipos principales)

Existen diferentes tecnologías según el nivel de protección y el costo:

### 1. UPS Offline / Standby (En espera)
* **Cómo funciona:** El equipo opera directamente con la energía de la red eléctrica comercial. Solo cuando detecta un fallo o corte en la red, un circuito inversor conmuta y comienza a alimentar los equipos usando la energía de la batería.
* **Tiempo de conmutación:** Tiene un pequeño retardo (de 2 a 10 milisegundos) al cambiar a batería.
* **Uso ideal:** Equipos de oficina básicos, computadoras personales y periféricos de bajo costo.

### 2. UPS Line-Interactive (Interactivo)
* **Cómo funciona:** Similar al Offline, pero incorpora un regulador automático de voltaje (**AVR** - *Automatic Voltage Regulation*). Puede corregir variaciones leves de voltaje (subidas o bajadas de tensión) **sin necesidad de descargar la batería**, prolongando la vida útil de esta.
* **Tiempo de conmutación:** Entre 2 y 4 milisegundos al pasar a batería por un apagón total.
* **Uso ideal:** Servidores pequeños, estaciones de trabajo de gama media, consolas de videojuegos y equipos de red departamentales (switches, routers). Es la opción más equilibrada para el hogar y oficinas.

### 3. UPS Online de Doble Conversión (En línea / Online)
* **Cómo funciona:** Es el estándar de mayor gama y protección. La energía de la red eléctrica de entrada se convierte continuamente: de **CA (Corriente Alterna) a CC (Corriente Continua)** para cargar la batería y alimentar el inversor, y luego de **CC a CA** limpia y perfecta para entregar a los equipos.
* **Tiempo de conmutación:** **Cero milisegundos (0 ms)**. Como los equipos conectados se alimentan permanentemente del inversor (y no directamente de la red), no hay interrupción ni parpadeo si la red eléctrica principal colapsa.
* **Uso ideal:** Centros de datos (*Data Centers*), servidores críticos de misión crítica, equipos médicos y sistemas industriales de alta sensibilidad.

---

## Componentes Clave de un UPS
* **Baterías:** Generalmente de plomo-ácido selladas (VRLA) o de ión-litio en modelos modernos, encargadas de almacenar la energía química.
* **Rectificador / Cargador:** Convierte la corriente alterna de la red en corriente continua para mantener las baterías cargadas.
* **Inversor:** Convierte la corriente continua de la batería en corriente alterna pura para alimentar los dispositivos conectados.
* **Filtros y Supresores:** Protegen contra picos y ruido eléctrico.
* **Interfaz de Control / SNMP:** Permite la comunicación con servidores para un apagado automatizado (*graceful shutdown*) o monitoreo remoto de la salud del UPS.
# Resumen: BTU (British Thermal Unit)

---

## ¿Qué es un BTU?
El **BTU** (por sus siglas en inglés, *British Thermal Unit* o *Unidad Térmica Británica*) es una unidad de medida de **energía térmica** (calor). 

Específicamente, un BTU se define como la cantidad de calor necesaria para elevar la temperatura de **una libra masa de agua en un grado Fahrenheit** (físicamente, de 59 °F a 60 °F) a una presión constante de una atmósfera.

---

## Aplicación Principal: Climatización y Aire Acondicionado
Aunque es una unidad de energía, su uso más extendido a nivel mundial es en los sistemas de **aire acondicionado y calefacción (HVAC)** para indicar la **capacidad de enfriamiento** o extracción de calor de un equipo por hora.

* **BTU/h (BTU por hora):** En climatización, cuando se habla de la "potencia" de un aire acondicionado de 12,000 BTU, en realidad se refiere a **12,000 BTU por hora**. Esto significa que el equipo es capaz de extraer 12,000 unidades térmicas de calor del ambiente en el transcurso de una hora.

---

## Equivalencias Comunes
Para entender su magnitud frente a otros sistemas de medida de energía y potencia, se suelen utilizar las siguientes conversiones:

* **1 BTU** equivale aproximadamente a:
  * **1,055 Joules (J)**
  * **0.252 Kilocalorías (kcal)**
  * **0.000293 Kilovatios-hora (kWh)**

* **Equivalencias de capacidad comercial:**
  * **1 Tonelada de Refrigeración (TR):** Equivalente a **12,000 BTU/h** (es la cantidad de calor necesaria para fundir una tonelada de hielo puro en 24 horas).
  * **1 Kilovatio (kW) térmico:** Equivalente a aprox. **3,412 BTU/h**.

---

## ¿Cómo se calcula la capacidad necesaria (BTU) para un espacio?
Para dimensionar un aire acondicionado de forma correcta, se deben considerar factores como los metros cuadrados de la habitación, la cantidad de personas que la habitan, la iluminación, los aparatos electrónicos encendidos y la exposición al sol. 

Una regla práctica general (*regla de pulgar* básica) para climas templados es:
$$\text{BTU necesarios} \approx \text{Área en metros cuadrados} \times 600 \text{ a } 800 \text{ BTU/m²}$$
*(Nota: El valor exacto varía según el aislamiento térmico y la zona geográfica).*
