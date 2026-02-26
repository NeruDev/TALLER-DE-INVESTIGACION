Sistema de Monitoreo de Consumo Eléctrico Residencial Basado en IoT (SME-IoT)

## 1. Resumen Ejecutivo

El presente proyecto detalla el diseño y la implementación de un dispositivo electrónico de bajo costo orientado a la medición no intrusiva de corriente eléctrica en entornos residenciales. El sistema utiliza un microcontrolador ESP32 para el procesamiento de señales y conectividad inalámbrica, permitiendo la visualización de métricas de consumo en tiempo real tanto en una interfaz local (OLED) como remota (Plataforma Web/App). El objetivo principal es proporcionar al usuario final herramientas de diagnóstico para fomentar el ahorro energético y evitar tarifas de alto consumo, utilizando una arquitectura de hardware económica y una fuente de alimentación conmutada compacta integrada a la red doméstica.

## 2. Planteamiento del Problema y Justificación

En México, la falta de retroalimentación inmediata sobre el consumo eléctrico impide que los usuarios domésticos ajusten sus hábitos de consumo de manera eficiente. Los medidores fiscales instalados por la Comisión Federal de Electricidad (CFE) no ofrecen métricas detalladas ni alertas en tiempo real, lo que frecuentemente deriva en facturaciones elevadas bajo el esquema DAC (Doméstica de Alto Consumo).

Este proyecto justifica su desarrollo al ofrecer una solución **accesible, segura y de arquitectura abierta**, capaz de estimar el consumo energético ($kWh$) y proyectar costos, sirviendo como una herramienta educativa y de control financiero para las familias mexicanas.

## 3. Objetivos

* **General:** Desarrollar un medidor de consumo eléctrico inteligente, de bajo costo y no intrusivo, capaz de monitorear la corriente de carga y transmitir la información vía Wi-Fi.
* **Específicos:**
* Implementar un sensor de corriente tipo *clamp* (SCT-013) para garantizar la seguridad de la instalación sin contacto galvánico directo.
* Diseñar un sistema de alimentación compacto mediante una fuente conmutada (AC-DC) integrada en el dispositivo.
* Integrar un módulo de medición de voltaje (ZMPT101B) para obtener lecturas de Potencia Activa y Factor de Potencia.
* Optimizar la lista de materiales (BOM) para reducir el costo de manufactura por unidad.



## 4. Descripción Técnica del Sistema

### 4.1. Hardware y Adquisición de Señales

El núcleo del sistema es el SoC **ESP32**, seleccionado por su relación costo-beneficio y su doble núcleo que permite gestionar la pila TCP/IP y el muestreo del ADC simultáneamente.

* **Sensor de Corriente:** Se utiliza un transformador de corriente (CT) modelo **SCT-013-030** (30A/1V). Este sensor entrega una señal de corriente alterna proporcional al consumo.
* **Sensor de Voltaje:** Se emplea un módulo transformador de voltaje **ZMPT101B**. Este componente reduce el voltaje de red (127V) a una señal segura para el ADC, proporcionando aislamiento galvánico y permitiendo medir la forma de onda del voltaje.
* **Acondicionamiento de Señal:** Dado que el ESP32 opera con lógica de 3.3V y no admite voltajes negativos, se implementa un circuito de *offset* (divisor de tensión) para elevar la señal AC a un punto medio ($1.65V$), permitiendo la lectura completa de la onda senoidal.
* **Interfaz de Usuario:** Pantalla OLED de 0.96" (protocolo I2C) para visualización *in-situ*.

### 4.2. Sistema de Alimentación (Fuente Conmutada)

Para cumplir con el requisito de integración y tamaño reducido, se sustituye el uso de cargadores externos por un **Módulo de Fuente Conmutada AC-DC Integrado (Tipo Hi-Link o equivalente genérico)**.

* **Entrada:** 90-240V AC (Red doméstica).
* **Salida:** 5V DC regulados.
* **Eficiencia:** $>70\%$.
Esta fuente se conecta internamente a la línea de alimentación, permitiendo que el dispositivo sea "plug-and-play" sin depender de baterías ni puertos USB externos.

### 4.3. Fundamentación Matemática

El microcontrolador realiza un muestreo de la señal analógica para calcular la Corriente Eficaz ($I_{RMS}$) mediante la siguiente ecuación discretizada:

$$I_{RMS} = \sqrt{\frac{1}{N} \sum_{n=0}^{N-1} i[n]^2}$$

Al contar con lecturas instantáneas de voltaje $v[n]$ y corriente $i[n]$, el sistema calcula la **Potencia Activa ($P$)**, que es la que realmente cobra CFE:

$$P = \frac{1}{N} \sum_{n=0}^{N-1} (v[n] \times i[n])$$

## 5. Análisis de Costos y Presupuesto (Optimizado)

A continuación, se presenta la Lista de Materiales (BOM) cotizada con precios promedio en proveedores de electrónica económica en México (MercadoLibre, tiendas de componentes locales en Toluca o distribuidores en línea masivos). Se han seleccionado componentes genéricos para minimizar costos.

| Componente | Descripción Técnica | Costo Unitario Estimado (MXN) |
| --- | --- | --- |
| **Microcontrolador** | ESP32 DevKit V1 (Clónico/Genérico) | $130.00 |
| **Sensor de Corriente** | SCT-013-030 (30A, salida 1V) | $185.00 |
| **Sensor de Voltaje** | Módulo ZMPT101B (Transformador de voltaje activo) | $50.00 |
| **Fuente de Alimentación** | Módulo AC-DC 220V a 5V 700mA (Tipo Hi-Link HLK-PM01 o genérico) | $75.00 |
| **Pantalla** | Display OLED 0.96" I2C (SSD1306) | $65.00 |
| **PCB / Montaje** | Placa perforada, borneras, resistencias, capacitores, jack 3.5mm | $45.00 |
| **Gabinete** | Caja plástica estándar o impresión 3D (PLA genérico) | $50.00 |
| **Total Materiales** | **Costo Directo de Hardware** | **$600.00 MXN** |

*Nota: Los precios pueden variar ±15% según el volumen de compra y el proveedor. Se asume ensamblaje manual por parte del estudiante/ingeniero.*

## 6. Metodología de Implementación (Fases)

1. **Diseño de Circuito:** Integración del ESP32, el acondicionamiento del sensor SCT-013 y el módulo de fuente conmutada en un esquema de conexiones seguro.
2. **Desarrollo de Firmware:** Programación en C++ (Arduino IDE o PlatformIO). Implementación de librerías `EmonLib` para cálculos energéticos.
3. **Calibración:** Ajuste de los factores de conversión para voltaje y corriente comparando contra un multímetro TRMS de referencia.
4. **Pruebas de Campo:** Instalación en un circuito derivado del hogar (ej. cocina o lavandería) para monitoreo continuo de 24 horas.

## 7. Conclusión

El diseño propuesto cumple con los requisitos de funcionalidad técnica y viabilidad económica. Con un costo de materiales aproximado de 600.00 MXN,
el dispositivo se posiciona como una solución competitiva frente a medidores comerciales que superan los  1,500.00 MXN. El uso de una fuente conmutada integrada profesionaliza el acabado del dispositivo, eliminando cables externos innecesarios y facilitando su instalación final en cajas de registro o tableros eléctricos.