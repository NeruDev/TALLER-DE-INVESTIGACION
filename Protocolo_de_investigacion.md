# Protocolo de investigación: Monitoreo IoT Residencial

**Investigador:** Jesus Uriel Uribe Diaz  
**Institución:** Instituto Tecnológico de Toluca  
**Proyecto:** Diseño e Implementación de un Sistema IoT de Bajo Costo para la Monitorización No Intrusiva de Consumo Eléctrico Residencial mediante Arquitectura ESP32.  
**Periodo de ejecución:** 2 de febrero de 2026 al 29 de mayo de 2026.  
**Ubicación del estudio:** Tenango del Valle, Estado de México.

---

## 1. Antecedentes del problema

En el panorama energético nacional, observo que la evaluación del consumo eléctrico residencial en México depende predominantemente de lecturas acumuladas bimestrales. Esta carencia de retroalimentación operativa en tiempo real impide a los usuarios identificar cargas ineficientes y patrones horarios de alto impacto económico.

Tras analizar la literatura técnica sobre el Monitoreo No Intrusivo de Cargas (NILM), confirmo que la medición simultánea de corriente y voltaje, integrada con algoritmos de procesamiento digital de señales, permite estimar la potencia activa con una precisión metrológica útil para la gestión doméstica. Por ello, propongo utilizar la arquitectura ESP32 para desarrollar un sistema de instrumentación accesible que cierre la brecha entre el costo tecnológico y la adopción residencial.

---

## 2. Planteamiento del problema

Detecto una desconexión crítica entre el consumo eléctrico real y la capacidad de decisión del usuario. En mis observaciones preliminares en el municipio de **Tenango del Valle**, identifico que la ausencia de medición continua produce sobrecostos por hábitos no optimizados y una baja detección de consumos en espera (*standby*).

Aunque existen soluciones comerciales, sus barreras de adopción (costo elevado y dependencia de ecosistemas cerrados) limitan su uso. Por tanto, asumo el desarrollo de una alternativa de bajo costo, técnicamente validada, que mantenga un costo de manufactura ≤ **$600 MXN** y garantice seguridad operativa.

### Pregunta de investigación

¿Es factible para mí implementar un sistema IoT residencial no intrusivo, basado en la arquitectura ESP32, que mantenga una precisión de error < 5% frente a un instrumento de referencia y un costo inferior a $600 MXN, validándolo en el contexto de Tenango del Valle?

---

## 3. Objetivos de la investigación

### Objetivo general

Desarrollar un sistema IoT de monitorización no intrusiva para la gestión del consumo eléctrico residencial, basado en la arquitectura ESP32 y sensado simultáneo de parámetros eléctricos, con el fin de validar su precisión metrológica y viabilidad económica en el municipio de Tenango del Valle.

### Objetivos específicos

1. Caracterizar los requerimientos técnicos y funcionales del sistema de medición considerando las normativas de la infraestructura eléctrica residencial mexicana.
2. Diseñar la arquitectura electrónica de adquisición y la etapa de acondicionamiento de señales para los transductores de corriente y voltaje.
3. Programar los algoritmos de procesamiento digital de señales para el cálculo de potencia activa real y la gestión de conectividad inalámbrica.
4. Integrar los módulos de visualización local y almacenamiento masivo para garantizar la persistencia de datos ante contingencias de red.
5. Evaluar el desempeño del prototipo mediante pruebas comparativas contra instrumentación TRMS de referencia para determinar el error porcentual absoluto medio.
6. Comparar la estructura de costos del prototipo final frente a soluciones comerciales para determinar su índice de ahorro y factibilidad de implementación.

---

## 4. Justificación e impacto

### Impacto tecnológico
Demostraré la integración de sensores no intrusivos y conectividad IoT en una plataforma de hardware abierto, validando protocolos de calibración para convertidores analógico-digitales de resolución limitada.

### Impacto económico
Reduciré la barrera de entrada para el monitoreo energético doméstico, posicionando el costo del dispositivo un 60% por debajo de las soluciones de mercado actuales.

### Impacto ambiental
Favoreceré prácticas de eficiencia energética en la vivienda, lo que impactará indirectamente en la reducción de la demanda eléctrica y las emisiones de CO2 asociadas.

---

## 5. Diseño del marco teórico (Ejes técnicos)

Fundamentaré mi investigación en cuatro pilares científicos:
1. **Fundamentos eléctricos:** Analizaré el valor eficaz (RMS), potencia activa y factor de potencia mediante el estudio de magnitudes instantáneas.
2. **Instrumentación y sensado:** Aplicaré los principios de inducción electromagnética para transformadores de corriente de núcleo partido y sensores de voltaje con aislamiento galvánico.
3. **Procesamiento digital de señales:** Implementaré técnicas de muestreo, cuantización y filtrado para el cálculo discreto de métricas eléctricas.
4. **Arquitectura IoT embebida:** Optimizaré el uso del ESP32 para la adquisición analógica y el cómputo en el borde (*Edge Computing*).

---

## 6. Hipótesis

### Hipótesis del investigador
Lograré cumplir simultáneamente con el costo de implementación de bajo presupuesto y un error de potencia activa inferior al 5% frente a un instrumento patrón, aplicando una calibración precisa del sistema.

### Supuestos técnicos
1. Estimo que la relación entre la corriente real y la lectura acondicionada del sensor SCT-013-030 mantendrá la linealidad adecuada en el rango operativo residencial.
2. Sostengo que la adquisición simultánea de voltaje mejora significativamente la estimación de potencia activa frente a métodos que asumen voltaje nominal constante.

---

## 7. Bosquejo del método

### 7.1 Universo y muestra
Delimitaré mi estudio a las condiciones de consumo residencial monofásico en el municipio de **Tenango del Valle, Estado de México**. Seleccionaré una vivienda unifamiliar de dicha localidad para la fase de validación de campo, recolectando registros de carga representativos bajo condiciones reales de operación.

### 7.2 Tipo de estudio
- **Investigación aplicada y tecnológica:** Aplicaré leyes fundamentales de la ingeniería electrónica para desarrollar un prototipo funcional que resuelva un problema práctico de visibilidad energética.
- **Enfoque cuantitativo:** Utilizaré la recolección de datos numéricos y herramientas estadísticas para validar la precisión del sistema.
- **Alcance correlacional y explicativo:** Determinaré la correlación entre las lecturas del prototipo y el instrumento patrón, analizando las causas técnicas de las desviaciones (como la no linealidad del ADC).
- **Diseño experimental mixto:** Alternaré entre pruebas controladas de laboratorio y monitoreo en campo.

### 7.3 Procedimiento experimental
1. **Fase de integración:** Ensamblaré el hardware y desarrollaré el código sobre la arquitectura de doble núcleo del ESP32.
2. **Fase de calibración:** Aplicaré cargas resistivas conocidas para ajustar los factores de escala y compensar el *offset* de los sensores.
3. **Fase de validación:** Instalaré el dispositivo en Tenango del Valle para realizar un monitoreo continuo de 24 a 72 horas, contrastando los resultados con un multímetro TRMS calibrado.

---

## 8. Cronograma (Etapa Documental)

| Fase | Actividad | Inicio | Fin | Entregable |
|---|---|---:|---:|---|
| F1 | Investigación de antecedentes y planteamiento técnico | 2026-02-02 | 2026-02-13 | Capítulos 1 y 2 |
| F2 | Definición de objetivos y análisis de impacto social/económico | 2026-02-16 | 2026-03-06 | Capítulos 3 y 4 |
| F3 | Estructuración del marco teórico y revisión del estado del arte | 2026-03-09 | 2026-03-20 | Capítulo 5 |
| F4 | Formulación de hipótesis y operacionalización de variables métricas | 2026-03-23 | 2026-04-03 | Capítulo 6 |
| F5 | Diseño del bosquejo metodológico y tipos de estudio detallados | 2026-04-06 | 2026-04-24 | Sección 7 |
| F6 | Integración final del protocolo, presupuesto y referencias APA 7 | 2026-04-27 | 2026-05-29 | Protocolo completo |

---

## 9. Presupuesto y/o financiamiento

Invertiré en los siguientes componentes para la manufactura de una unidad del prototipo:

| Concepto | Especificación Técnica | Costo (MXN) |
|---|---|---|
| **ESP32 DevKit V1** | Microcontrolador Dual-Core con WiFi/BT integrado. | $130.00 |
| **Sensor SCT-013-030** | Transformador de corriente de núcleo partido (30A/1V). | $130.00 |
| **Sensor ZMPT101B** | Módulo de voltaje AC con aislamiento galvánico. | $48.50 |
| **Fuente HLK-PM01** | Convertidor AC-DC conmutado 5V/700mA. | $89.00 |
| **Módulo MicroSD** | Interfaz SPI para persistencia de datos local. | $18.90 |
| **Consumibles** | Cables, conectores, gabinete y soldadura. | $183.60 |
| **Total General** | | **$600.00** |

---

## 10. Glosario y Referencias

### 10.1 Glosario de términos técnicos

- **ADC (Analog-to-Digital Converter):** Periférico encargado de la cuantización de señales analógicas en valores digitales discretos.
- **ESP32:** System-on-Chip (SoC) basado en la arquitectura Xtensa® LX6 de 32 bits, optimizado para aplicaciones IoT.
- **NILM (Non-Intrusive Load Monitoring):** Estrategia de monitorización energética basada en la adquisición de señales en un punto de acometida común.
- **RMS (Root Mean Square):** Medida estadística de la magnitud de una cantidad variable, fundamental para el cálculo de potencia activa.
- **SCT-013-030:** Transductor de corriente basado en el principio de inducción, diseñado para instalación sin contacto galvánico.
- **TRMS (True Root Mean Square):** Capacidad de un instrumento para medir con precisión formas de onda no sinusoidales mediante el cálculo del valor eficaz real.
- **ZMPT101B:** Transformador de tensión de alta precisión con acondicionamiento de señal integrado para lectura de voltaje AC.

### 10.2 Referencias bibliográficas (APA 7)

1. Comisión Federal de Electricidad. (2024). *Tarifas domésticas de energía eléctrica*. https://app.cfe.mx/Aplicaciones/CCFE/Tarifas/TarifasCRECasa/Casa.aspx
2. Data México, Secretaría de Economía. (2025). *Ingenieros Electrónicos: salarios y fuerza laboral*. https://www.economia.gob.mx/datamexico/es/profile/occupation/ingenieros-electronicos
3. Espressif Systems. (2022). *ESP32 Series Datasheet*. https://www.espressif.com/documentation/esp32_datasheet_en.pdf
4. Kaselimi, M., Protopapadakis, E., Voulodimos, A., Doulamis, N., & Doulamis, A. (2022). Toward trustworthy energy disaggregation: A review of challenges, methods and perspectives for non-intrusive load monitoring. *Sensors, 22*(15), 5872. https://doi.org/10.3390/s22155872
5. Hart, G. W. (1992). Nonintrusive appliance load monitoring. *Proceedings of the IEEE, 80*(12), 1870–1891.
6. Bland, J. M., & Altman, D. G. (1986). Statistical methods for assessing agreement between two methods of clinical measurement. *The Lancet, 1*(8476), 307–310.
7. Shapiro, S. S., & Wilk, M. B. (1965). An analysis of variance test for normality (complete samples). *Biometrika, 52*(3–4), 591–611.
8. American Psychological Association. (2020). *Publication manual of the American Psychological Association* (7th ed.). https://apastyle.apa.org/
