#   Informe de Validación del Documento SRS: Firmware para un Sistema de Comunicación IoT Industrial (Versiones 1 y 2)

**Introducción**

Este informe presenta una validación comparativa de dos versiones del Documento de Especificación de Requisitos de Software (SRS) para un firmware destinado a un sistema de comunicación IoT industrial. El objetivo es identificar cambios, mejoras y posibles áreas de preocupación entre la versión 1 y la versión 2.

**Metodología**

Se realizó una revisión exhaustiva de ambos documentos, comparando sección por sección para detectar diferencias en los requisitos funcionales, no funcionales, interfaces y restricciones. Además, se incorporan las siguientes prácticas de validación:

* Revisión entre Pares: Organizar una sesión de revisión donde los compañeros actúen como stakeholders y revisen la SRS, identificando posibles inconsistencias o ambigüedades.
* Feedback y Ajustes: Recoger las observaciones y ajustar los requerimientos según el feedback recibido.
* Trazabilidad: Verificar que cada requerimiento esté vinculado a los objetivos y necesidades del caso de estudio.

**Hallazgos**

1.  **Similitudes:**

    * Ambas versiones comparten la misma estructura básica, incluyendo introducción, descripción general, requerimientos del sistema y restricciones.
    * Los propósitos del documento, el alcance del sistema, las definiciones, la perspectiva del producto, las funciones del producto, las características del usuario, las suposiciones y dependencias, los requerimientos funcionales (RF1-RF5), los requerimientos no funcionales (RNF1-RNF3), y las restricciones son idénticos en ambas versiones.

2.  **Diferencias:**

    * **Requerimientos No Funcionales:** La versión 1 incluye un requerimiento no funcional adicional: "RNF4 - Portabilidad: El firmware debe poder adaptarse a distintos modelos de microcontroladores ARM de la misma familia." Este requerimiento está ausente en la versión 2.
    * **Interfaces del Sistema:** La versión 1 detalla las interfaces del sistema, dividiéndolas en interfaces de hardware (sensores, comunicación, fuente de energía) e interfaces de software (broker MQTT, herramientas de monitoreo). La versión 2 omite esta sección por completo.

**Análisis de Impacto**

* La eliminación del requerimiento de portabilidad en la versión 2 podría indicar un enfoque en una plataforma de hardware más específica, lo que podría simplificar el desarrollo pero reducir la flexibilidad del sistema.
* La omisión de la sección de interfaces del sistema en la versión 2 reduce la claridad sobre cómo interactúa el firmware con el hardware y otros componentes de software. Esta falta de detalle podría generar ambigüedad durante la implementación y las pruebas.

| ID del Requisito | Tipo               | Descripción                                                                 | Objetivo Relacionado                                               |
|------------------|--------------------|-----------------------------------------------------------------------------|--------------------------------------------------------------------|
| RF1              | Funcional          | El firmware debe recolectar datos de sensores industriales en tiempo real. | O1 - Monitoreo en tiempo real del entorno industrial               |
| RF2              | Funcional          | Debe transmitir los datos a través del protocolo MQTT.                      | O2 - Comunicación eficiente y estándar con servidores externos     |
| RF3              | Funcional          | Debe almacenar localmente los datos en caso de falla de red.               | O3 - Tolerancia a fallos y disponibilidad de datos                 |
| RF4              | Funcional          | El firmware debe reiniciarse automáticamente en caso de error crítico.     | O4 - Mantenimiento automático y alta disponibilidad                |
| RF5              | Funcional          | Debe permitir la actualización OTA (Over The Air).                         | O5 - Mantenimiento remoto y actualización de funcionalidades       |
| RNF1             | No Funcional       | El firmware debe operar con consumo energético bajo.                       | O6 - Eficiencia energética en dispositivos embebidos               |
| RNF2             | No Funcional       | Tiempo de arranque menor a 5 segundos.                                     | O7 - Arranque rápido para minimizar tiempo de inactividad          |
| RNF3             | No Funcional       | Cumplimiento de estándares de seguridad para comunicación IoT.            | O8 - Seguridad en la transferencia de información                  |
| RNF4 (v1)        | No Funcional       | Portabilidad entre microcontroladores ARM de la misma familia.             | O9 - Escalabilidad y reutilización del firmware en diferentes HW   |
| INT-HW (v1)      | Interfaz de HW     | Conexiones con sensores, módulos de comunicación y fuente de energía.      | O1, O2 - Interacción directa con hardware del entorno industrial   |
| INT-SW (v1)      | Interfaz de SW     | Comunicación con broker MQTT y herramientas de monitoreo.                  | O2, O8 - Integración con sistemas de monitoreo y comunicación      |


**Conclusión**

La versión 2 del SRS presenta cambios significativos en comparación con la versión 1, particularmente en la omisión del requerimiento de portabilidad y la eliminación de la sección de interfaces del sistema. Si bien algunas simplificaciones pueden ser beneficiosas, es crucial que estos cambios se realicen de manera justificada y documentada para mantener la claridad y completitud de la especificación. Se recomienda abordar las recomendaciones anteriores, incluyendo las prácticas de revisión, feedback y trazabilidad, para mejorar la calidad y utilidad del documento SRS.

