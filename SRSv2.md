# Documento SRS: Firmware para un Sistema de Comunicación IoT Industrial

## 1. Introducción

### 1.1 Propósito del documento
Este documento tiene como objetivo especificar los requerimientos funcionales y no funcionales del firmware para un sistema de comunicación IoT industrial, diseñado para conectar sensores remotos en una planta de manufactura.

### 1.2 Alcance del sistema
El sistema consiste en una red de sensores inalámbricos que transmiten datos críticos al servidor central. El firmware desarrollado en C está diseñado para microcontroladores ARM de bajo consumo e incluye protocolos de comunicación, seguridad, gestión de energía y tolerancia a interferencias.

### 1.3 Definiciones, acrónimos y abreviaturas
- **IoT**: Internet of Things  
- **MQTT**: Message Queuing Telemetry Transport  
- **ARM**: Advanced RISC Machine  
- **SRS**: Software Requirements Specification

---

## 2. Descripción general

### 2.1 Perspectiva del producto
El firmware es una parte integral de un sistema IoT que permite la recolección y transmisión de datos desde sensores distribuidos hacia un servidor central, garantizando seguridad, confiabilidad y eficiencia energética.

### 2.2 Funciones del producto
- Recolección de datos desde sensores conectados.  
- Transmisión de datos utilizando MQTT.  
- Encriptación de datos para comunicación segura.  
- Implementación de algoritmos de corrección de errores.  
- Gestión de energía para extender la duración de la batería.

### 2.3 Características del usuario
Usuarios técnicos como ingenieros de automatización e integradores de sistemas industriales que requieren monitoreo remoto y mantenimiento predictivo.

### 2.4 Suposiciones y dependencias
- El hardware será un microcontrolador ARM con capacidad de comunicación inalámbrica.  
- Se cuenta con infraestructura de red estable en la planta.  
- Los sensores seguirán estándares industriales comunes.

---

## 3. Requerimientos del sistema

### 3.1 Requerimientos funcionales

#### RF1 - Adquisición de datos
El sistema debe poder adquirir datos de sensores analógicos o digitales conectados al microcontrolador.

#### RF2 - Transmisión segura de datos
El firmware debe transmitir los datos usando el protocolo MQTT sobre TLS.

#### RF3 - Corrección de errores
Se debe implementar detección y corrección de errores mediante algoritmos como CRC o Hamming.

#### RF4 - Encriptación
La información enviada debe estar cifrada mediante algoritmos AES de 128 bits.

#### RF5 - Gestión de energía
El sistema debe entrar en modo de bajo consumo tras cada transmisión y despertar periódicamente.

---

### 3.2 Requerimientos no funcionales

#### RNF1 - Rendimiento
El sistema debe ser capaz de transmitir un paquete de datos cada 30 segundos con una latencia máxima de 2 segundos.

#### RNF2 - Confiabilidad
El firmware debe garantizar una tasa de entrega de paquetes ≥ 98% incluso en ambientes ruidosos.

#### RNF3 - Seguridad
Todo dato transmitido debe estar cifrado, y el acceso al firmware debe requerir autenticación.

#### RNF4 - Mantenibilidad
El código debe estar documentado para permitir futuras actualizaciones y depuración.

---

## 4. Restricciones
- El tamaño del firmware no debe exceder los 128 KB.  
- La batería debe durar al menos 6 meses en operación intermitente.  
- Solo se permiten bibliotecas de código abierto para funciones de comunicación y seguridad.
