# Diseño e Implementación de un Sistema IoT de Bajo Costo para la Monitorización No Intrusiva de Consumo Eléctrico Residencial mediante Arquitectura ESP32

## 1. Antecedentes del problema

La gestión de la demanda energética es fundamental en la transición hacia redes eléctricas inteligentes (*Smart Grids*). A nivel global, los Objetivos de Desarrollo Sostenible (ODS 7 y 12) subrayan la necesidad de mejorar la eficiencia energética residencial. En México, el esquema tarifario de la Comisión Federal de Electricidad (CFE) penaliza el alto consumo (Tarifa DAC), sin embargo, los medidores convencionales no proporcionan retroalimentación en tiempo real al usuario, limitando su capacidad de corrección de hábitos de consumo.

Históricamente, el monitoreo no intrusivo de carga (NILM) ha evolucionado desde métodos analógicos hasta arquitecturas basadas en Internet de las Cosas (IoT). Plataformas como OpenEnergyMonitor han demostrado la viabilidad de usar sensores de corriente de núcleo partido, pero sus costos de adquisición e importación siguen siendo elevados para el mercado nacional.

## 2. Planteamiento del problema

El problema central radica en la asimetría de información entre el consumo físico de energía y la conciencia del usuario. La falta de herramientas de diagnóstico accesibles impide la detección de consumos fantasma o ineficiencias en electrodomésticos. Las barreras económicas (costo de equipos comerciales >$1,500 MXN) y la complejidad de instalación técnica desincentivan la adopción de estas tecnologías.

Pregunta de investigación: ¿Es factible desarrollar un sistema de monitoreo eléctrico residencial IoT que, mediante la medición simultánea de voltaje y corriente con sensores no intrusivos y un microcontrolador ESP32, reduzca el costo de adquisición en un 60% respecto a analizadores comerciales, garantizando una precisión superior al 95%?

## 3. Objetivo general

Diseñar, implementar y validar un sistema de monitoreo de consumo eléctrico residencial de bajo costo y no intrusivo, basado en el microcontrolador ESP32 y sensores de corriente (SCT-013) y voltaje (ZMPT101B), capaz de calcular la potencia activa en tiempo real con un error inferior al 5%.

## 4. Objetivos específicos

4.1 Analizar los requerimientos funcionales del sistema bajo las condiciones de la infraestructura eléctrica mexicana.
4.2 Diseñar la etapa de hardware incluyendo el acondicionamiento de señal para sensores y alimentación AC-DC integrada.
4.3 Desarrollar el firmware de adquisición y procesamiento digital de señales sobre la arquitectura de doble núcleo del ESP32.
4.4 Implementar una interfaz local OLED y almacenamiento en tarjeta microSD.
4.5 Validar el desempeño del prototipo mediante pruebas comparativas contra instrumentación de referencia TRMS.

## 5. Justificación

La investigación es conveniente porque proporciona una herramienta de diagnóstico instantáneo frente a la opacidad de la medición fiscal bimestral. Tiene relevancia social al democratizar el acceso a tecnología de eficiencia energética para familias en riesgo de incurrir en la tarifa DAC. Desde una implicación práctica, resuelve la invisibilidad del consumo eléctrico sin riesgos de instalación intrusiva. Aporta valor teórico al validar protocolos de calibración en hardware de bajo costo con restricciones de resolución de 12 bits.

## 6. Marco Teórico

6.1 Electromagnetismo: El sensor SCT-013 opera bajo la Ley de Faraday de la Inducción Electromagnética, donde el flujo magnético generado por el conductor primario induce una corriente proporcional en la bobina secundaria.
6.2 Procesamiento Digital: Se aplica el teorema de Nyquist-Shannon para garantizar que la frecuencia de muestreo (~1 kHz) sea suficiente para capturar la señal de 60 Hz y sus armónicos.
6.3 Potencia Eléctrica: La potencia activa (P) se calcula mediante el promedio del producto de las muestras instantáneas de voltaje y corriente, incorporando el factor de potencia de forma intrínseca.
6.4 Arquitectura ESP32: El uso de una arquitectura SoC de doble núcleo permite separar las tareas críticas de medición de las tareas de comunicación WiFi y gestión de archivos.

## 7. Hipótesis

Hi: Es factible desarrollar un sistema de monitoreo basado en ESP32, SCT-013 y ZMPT101B con costos de manufactura inferiores a $600.00 MXN, manteniendo un error de medición de potencia activa inferior al 5% en cargas superiores a 25 W.

H0: El sistema excede el costo de $600.00 MXN o presenta un error superior al 5%, invalidando la viabilidad técnica y económica de la propuesta.

## 8. Diseño metodológico

8.1 Universo: El universo comprende los sistemas de gestión energética residencial en México bajo condiciones de suministro monofásico.
8.2 Tamaño de la muestra: Se seleccionaron 270 pares de observaciones (prototipo vs. patrón) distribuidas en 9 niveles de carga (0.5 A a 30 A) con 30 repeticiones por nivel.
8.3 Tipos de investigación: Aplicada, tecnológica, cuantitativa y experimental.
8.4 Instrumento para recolección: Se utiliza un prototipo basado en ESP32 con almacenamiento en microSD y un multímetro de referencia True RMS calibrado.
8.5 Encuesta: Se realizó una consulta técnica preliminar a 10 usuarios de tarifa doméstica para identificar el umbral de inversión aceptable para dispositivos de monitoreo, fijándolo en un rango de $500 a $700 MXN.

## 9. Cronograma

| Actividad | Mes 1 | Mes 2 | Mes 3 | Mes 4 |
| :--- | :---: | :---: | :---: | :---: |
| Revisión bibliográfica | X | | | |
| Diseño de hardware y PCB | X | X | | |
| Desarrollo de firmware | | X | X | |
| Pruebas de laboratorio | | | X | |
| Pruebas de campo y validación | | | X | X |
| Redacción de reporte final | | | | X |

## 10. Presupuesto y financiamiento

10.1 Presupuesto de materiales:
- ESP32 DevKit V1: $130.00
- SCT-013-030: $185.00
- ZMPT101B: $50.00
- Fuente AC-DC HLK-PM01: $75.00
- Pantalla OLED: $65.00
- Accesorios y gabinete: $95.00
Total: $600.00 MXN por unidad.
10.2 Financiamiento: El proyecto es financiado con recursos propios del investigador para la fase de prototipado inicial.

## 11. Fuentes de información

Espressif Systems. (2022). ESP32 Series Datasheet (ver. 3.4).
Hernández Sampieri, R. (2014). Metodología de la investigación (6ª ed.).
Kaselimi, M., et al. (2022). Towards Trustworthy Energy Disaggregation. Sensors, 22(15).
Naciones Unidas. (2015). Agenda 2030 para el Desarrollo Sostenible.
Norma Oficial Mexicana NOM-001-SEDE-2012. Instalaciones Eléctricas.

## 12. Anexos

Anexo A: Diagrama esquemático del circuito de acondicionamiento de señal.
Anexo B: Código fuente del algoritmo de cálculo de potencia activa.
Anexo C: Tabla comparativa de resultados de linealidad (Prototipo vs TRMS).
