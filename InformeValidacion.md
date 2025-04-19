# Informe de Validación del Firmware para Sistema de Comunicación IoT Industrial

## 1. Introducción

Este documento presenta el informe de validación del firmware desarrollado para un sistema de comunicación IoT en entornos industriales. El objetivo es verificar que el firmware cumpla con los requerimientos funcionales y no funcionales especificados en el Documento SRS.

---

## 2. Objetivos de la Validación

- Verificar la correcta adquisición y transmisión de datos desde los sensores.  
- Asegurar la integridad, confidencialidad y disponibilidad de la información transmitida.  
- Evaluar el desempeño energético y la estabilidad en entornos de alta interferencia.  
- Comprobar la interoperabilidad del sistema con el servidor central y los protocolos definidos.

---

## 3. Entorno de Pruebas

- **Microcontrolador**: ARM Cortex-M4  
- **Sensores**: Analógicos (temperatura, humedad) y digitales (vibración, presencia)  
- **Protocolo de Comunicación**: MQTT sobre TLS  
- **Servidor MQTT**: Mosquitto en Raspberry Pi  
- **Herramientas de monitoreo**: Node-RED, Wireshark  
- **Red inalámbrica**: Wi-Fi con interferencias simuladas  
- **Fuente de alimentación**: Batería Li-Ion de 3.7V, 2000mAh  

---

## 4. Casos de Prueba

### 4.1 Prueba de adquisición de datos (RF1)

- **Descripción**: Se conectaron sensores al microcontrolador para validar la lectura de señales.
- **Resultado esperado**: Datos numéricos coherentes y estables.
- **Resultado obtenido**: Lectura continua y precisa de todos los sensores.

---

### 4.2 Prueba de transmisión segura (RF2)

- **Descripción**: Se probó la transmisión MQTT con cifrado TLS.
- **Resultado esperado**: Comunicación exitosa sin pérdidas ni paquetes corruptos.
- **Resultado obtenido**: 100% de los paquetes recibidos correctamente en el servidor.

---

### 4.3 Prueba de corrección de errores (RF3)

- **Descripción**: Se introdujo ruido electromagnético para forzar errores.
- **Resultado esperado**: El firmware detecta y corrige errores sin reinicios.
- **Resultado obtenido**: Corrección efectiva de errores, sin pérdida de funcionalidad.

---

### 4.4 Prueba de encriptación (RF4)

- **Descripción**: Se inspeccionó el tráfico de red con Wireshark.
- **Resultado esperado**: Los datos deben aparecer cifrados.
- **Resultado obtenido**: Todos los datos en tránsito están encriptados con AES-128.

---

### 4.5 Prueba de gestión energética (RF5)

- **Descripción**: Se midió el consumo energético durante el ciclo de trabajo.
- **Resultado esperado**: Menos de 50 mA en reposo, menos de 150 mA en transmisión.
- **Resultado obtenido**: 42 mA en reposo y 135 mA durante envío.

---

## 5. Validación de Requerimientos No Funcionales

| Requerimiento | Descripción | Resultado |
|---------------|-------------|-----------|
| RNF1 - Rendimiento | Transmisión en menos de 2 s cada 30 s | Cumplido |
| RNF2 - Confiabilidad | ≥ 98% entrega de paquetes | 99.3% alcanzado |
| RNF3 - Seguridad | Encriptación y autenticación | Verificado |
| RNF4 - Portabilidad | Compatible con Cortex-M3 | Probado en M3 |
| RNF5 - Mantenibilidad | Código comentado y modular | Revisado por pares |

---

## 6. Conclusión

El firmware ha superado exitosamente todas las pruebas de validación, cumpliendo con los requerimientos definidos en el Documento SRS. Está apto para ser desplegado en el entorno industrial de la planta. Se recomienda documentación continua y monitoreo de desempeño para futuras mejoras.

---

## 7. Anexos

- Capturas de Node-RED mostrando los datos recibidos  
- Logs del servidor MQTT  
- Gráficas de consumo energético  
- Código fuente con anotaciones de prueba

