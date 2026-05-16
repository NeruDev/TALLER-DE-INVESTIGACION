# Diseño e Implementación de un Sistema IoT de Bajo Costo para la Monitorización No Intrusiva de Consumo Eléctrico Residencial mediante Arquitectura ESP32

## Contenido

1. Antecedentes del problema
2. Planteamiento del problema
3. Objetivo general
4. Objetivos específicos
5. Justificación
6. Marco Teórico
7. Hipótesis
8. Diseño metodológico
9. Cronograma
10. Presupuesto y financiamiento
11. Fuentes de información
12. Anexos

## 1. Antecedentes del problema

La gestión de la demanda energética es fundamental en la transición hacia redes eléctricas inteligentes (*Smart Grids*). A nivel global, los Objetivos de Desarrollo Sostenible (ODS 7 y 12) subrayan la necesidad de mejorar la eficiencia energética residencial. En México, el esquema tarifario de la Comisión Federal de Electricidad (CFE) estructura el costo en categorías escalonadas (tarifas 1 a 1F), penalizando el alto consumo mediante la tarifa DAC (Doméstica de Alto Consumo), la cual elimina el subsidio gubernamental. Sin embargo, los medidores convencionales electromecánicos o digitales estándar funcionan como dispositivos de registro acumulativo sin capacidad de retroalimentación instantánea, limitando la capacidad del usuario para corregir hábitos de consumo en tiempo real.

Históricamente, el monitoreo no intrusivo de carga (NILM) ha evolucionado desde métodos analógicos hasta arquitecturas basadas en Internet de las Cosas (IoT). Plataformas de hardware abierto como OpenEnergyMonitor han demostrado la viabilidad de usar sensores de corriente de núcleo partido y la biblioteca `EmonLib`, pero sus costos de adquisición e importación (>$2,000 MXN) siguen siendo elevados para el mercado nacional. Estudios recientes como Kaselimi et al. (2022) identifican como brechas pendientes la confiabilidad en escenarios reales y la accesibilidad para su implementación masiva en el sector doméstico.

## 2. Planteamiento del problema

El problema central radica en la desconexión entre el consumo físico de energía y la conciencia del usuario. La falta de herramientas de diagnóstico accesibles impide la detección de consumos fantasma o ineficiencias en electrodomésticos. Las causas son multifactoriales: opacidad de la medición fiscal, barreras económicas (costo de equipos comerciales como Sense o Shelly EM >$1,500 MXN), complejidad de instalación y la invisibilidad inherente del recurso eléctrico. Además, las fluctuaciones de voltaje en la red mexicana distorsionan las estimaciones basadas exclusivamente en medición de corriente.

Pregunta de investigación: ¿Es factible desarrollar e implementar un sistema de monitoreo eléctrico residencial IoT que, mediante la medición simultánea de voltaje y corriente con sensores no intrusivos y un microcontrolador ESP32, reduzca el costo de adquisición en un 60% respecto a analizadores de red comerciales, garantizando una precisión superior al 95% en el cálculo de potencia activa real y permitiendo la detección de anomalías en el suministro, validándolo en una vivienda unifamiliar con servicio monofásico ubicada en Tenango del Valle, Estado de México?

## 3. Objetivo general

Diseñar, implementar y validar un sistema de monitoreo de consumo eléctrico residencial de bajo costo y no intrusivo, basado en el microcontrolador ESP32 y sensores de corriente tipo *clamp* (SCT-013) y de voltaje (ZMPT101B), capaz de calcular la potencia activa en tiempo real con un error inferior al 5% respecto a instrumentación de referencia, y de transmitir los datos de manera inalámbrica mediante conectividad WiFi.

## 4. Objetivos específicos

* Analizar los requerimientos funcionales y no funcionales del sistema bajo las condiciones de la infraestructura eléctrica mexicana y las restricciones técnicas de los componentes.
* Diseñar la etapa de hardware del sistema, incluyendo el circuito de acondicionamiento de señal para los sensores SCT-013, ZMPT101B, y el sistema de alimentación conmutada AC-DC integrado.
* Desarrollar el firmware de adquisición de datos y procesamiento digital de señales —cálculo de corriente eficaz ($I_{RMS}$), voltaje eficaz ($V_{RMS}$) y potencia activa ($P$)— sobre la arquitectura de doble núcleo del ESP32.
* Implementar la interfaz de usuario local (pantalla OLED SSD1306) y el módulo de almacenamiento local (tarjeta microSD) para la visualización y registro histórico.
* Validar el desempeño del prototipo mediante pruebas comparativas contra instrumentación patrón (multímetro TRMS calibrado) en laboratorio y campo.
* Evaluar la viabilidad económica del dispositivo mediante el análisis de la lista de materiales (BOM) y la comparación de costos frente al mercado.

## 5. Justificación

La investigación es conveniente porque proporciona una herramienta de diagnóstico instantáneo frente a la opacidad de la medición fiscal bimestral de CFE. Tiene relevancia social al democratizar el acceso a tecnología de eficiencia energética para familias mexicanas, reduciendo el costo de inversión a ~$600 MXN. Desde una implicación práctica, permite identificar patrones de uso ineficiente sin riesgos de instalación intrusiva, eliminando la necesidad de alterar el cableado fijo de la vivienda. Aporta valor teórico al validar la aplicabilidad de la Ley de Faraday y el teorema de Nyquist-Shannon en una plataforma de hardware con restricciones severas de costo y resolución (ADC de 12 bits).

## 6. Marco Teórico

El desarrollo de sistemas de monitoreo eléctrico residencial basados en microcontroladores y plataformas IoT ha sido objeto de investigación creciente. A continuación, se definen las bases teóricas y el funcionamiento detallado de los componentes de este proyecto:

* **Microcontrolador ESP32 y Sistemas Embebidos (IoT):** La unidad central de procesamiento y conectividad del proyecto es el System-on-Chip (SoC) ESP32, desarrollado por Espressif Systems. Su arquitectura específica es vital para este proyecto por las siguientes razones de diseño:
  * **Procesamiento de Doble Núcleo (Xtensa® LX6 de 32 bits a 240 MHz):** El sistema operativo en tiempo real FreeRTOS se utiliza para asignar tareas concurrentes de forma separada. El **Núcleo 1 (APP)** se dedica exclusivamente a tareas críticas de adquisición ininterrumpida de datos analógicos a alta velocidad (aprox. 1 kHz) y al procesamiento de señales digitales (cálculo iterativo de $I_{RMS}$, $V_{RMS}$ y potencia $P$). El **Núcleo 0 (PRO)** asume la carga de gestionar la interfaz de usuario local (pantalla OLED vía protocolo I2C), el almacenamiento de historial de consumos (tarjeta microSD por SPI) y, críticamente, la conectividad inalámbrica WiFi y la pila de protocolos TCP/IP (MQTT/HTTP). Esta separación garantiza que el muestreo de la red eléctrica nunca se interrumpa por retardos inherentes a la comunicación de red.
  * **Restricciones del Convertidor Analógico-Digital (ADC):** El ESP32 integra dos bloques ADC de 12 bits (ADC1 y ADC2). Existe una limitación arquitectónica documentada por el fabricante donde el bloque ADC2 no puede operar simultáneamente con el módem WiFi. Por esta razón, el diseño restringe rigurosamente los pines de sensado de corriente y voltaje al bloque ADC1 (pines GPIO 32 a 39). La resolución de 12 bits proporciona 4096 niveles de cuantización sobre un rango unipolar de 0 a 3.3 V, otorgando suficiente granularidad para electrodomésticos comunes, pero introduciendo un piso de ruido de cuantización para cargas inferiores a 25 W (modo *standby*), considerándose la zona muerta del proyecto.
* **Sensor de Corriente SCT-013-030 (Monitoreo No Intrusivo):** El funcionamiento de este sensor tipo *clamp* de núcleo partido se fundamenta en la **Ley de Faraday de la Inducción Electromagnética** ($\varepsilon = -d\Phi_B/dt$). Al abrazar únicamente el conductor de fase de la acometida eléctrica principal, concentra el flujo magnético e induce una señal analógica proporcional. El submodelo "030" integra una resistencia de carga interna (*burden resistor*) que entrega directamente una salida máxima de 1 V AC a 30 A. Debido a que el ADC del ESP32 no soporta voltajes negativos de corriente alterna, la etapa analógica requiere implementar un divisor de tensión resistivo (complementado con capacitores de desacoplo) para inyectar un *offset* DC de 1.65 V, permitiendo a la onda oscilar de manera segura entre 0 V y 3.3 V.
* **Sensor de Voltaje ZMPT101B:** Este componente incorpora un transformador miniatura que provee un aislamiento galvánico de alta seguridad para la lectura directa de la red eléctrica (127 V). A diferencia de métodos que asumen un voltaje teórico nominal constante, medir esta variable instantánea real permite contabilizar fidedignamente los armónicos, detectar caídas de tensión (sags), y proteger los cálculos de consumo frente a las variaciones comunes en la red eléctrica de CFE. Al igual que el de corriente, requiere un *offset* a 1.65 V para su integración al ESP32.
* **Procesamiento Digital de Señales y Potencia Eléctrica:** Las ondas analógicas acondicionadas se muestrean bajo el principio del **Teorema de Nyquist-Shannon** ($f_s \geq 2 f_{max}$). El algoritmo iterativo en el firmware neutraliza el *offset* de 1.65 V para centrar las medidas matemáticas en cero. El avance sustancial de este modelo radica en que la **potencia activa ($P$)** se calcula promediando el producto de las muestras instantáneas sincronizadas de voltaje y corriente: $P = \frac{1}{N} \sum v[n] \cdot i[n]$. Esta metodología reemplaza al cálculo de potencia aparente básica ($S = V \cdot I$), e integra implícitamente la distorsión del **Factor de Potencia ($\cos\phi$)** causada por cargas inductivas reales como bombas de agua o refrigeradores, igualando el estándar de la tarifa comercial.
* **Fuentes de Alimentación Conmutadas (SMPS) y Normatividad:** Se empleará un convertidor AC/DC tipo *buck* de alta frecuencia (Hi-Link) para bajar la tensión de 127 V AC a 5 V DC, proporcionando eficiencia energética (>70%) en un formato integrado. Todo el ensamble respetará las pautas de instalación de la **NOM-001-SEDE-2012**, operando exclusivamente como un prototipo educativo de autodiagnóstico no intrusivo, desprovisto de valor fiscal o legal ante dependencias federales.

## 7. Hipótesis

En el marco de la ingeniería de diseño con prototipos, las hipótesis de este estudio conectan de forma explícita las variables de **desempeño metrológico** ($I_{RMS}$, $V_{RMS}$, $P$, MAPE, $R^2$), las variables de **viabilidad económica** (costo de la BOM) y las condiciones de operación de la red eléctrica.

* **Hipótesis general (de investigación - $H_i$):** Es factible desarrollar un sistema de monitoreo eléctrico residencial basado en IoT que, mediante el uso de hardware de código abierto y componentes genéricos optimizados (ESP32, SCT-013, ZMPT101B), reduzca los costos de manufactura por debajo de los $600.00 MXN por unidad, manteniendo un error de medición de potencia activa inferior al 5% en cargas domésticas estándar superiores a 25 W. Esta hipótesis establece un umbral numérico que permite la validación rigurosa mediante un multímetro patrón.
* **Hipótesis nula ($H_0$):** El sistema propuesto no alcanza la precisión requerida (presentando un error porcentual sostenido $> 5\%$) o su costo de manufactura excede irremediablemente los $600.00 MXN por unidad, invalidando la viabilidad técnico-económica de la propuesta.
* **Hipótesis alternativa ($H_1$):** El sistema propuesto logra un costo de manufactura ≤ $600.00 MXN por unidad y alcanza un error porcentual de potencia activa ≤ 5% en cargas domésticas superiores a 25 W.
* **Hipótesis específicas (Operacionales):**
  * **Linealidad del sensado de corriente:** El sensor SCT-013-030 acondicionado analógicamente con un *offset* DC de 1.65 V mantendrá una relación estrictamente lineal con la corriente eficaz real de la carga, esperando un coeficiente de determinación $R^2 > 0.98$ en el rango de 0.5 A a 30 A.
  * **Estabilidad de la fuente de alimentación:** La fuente integrada conmutada tipo Hi-Link presentará un rizado de tensión menor a 50 mVpp, garantizando que no introducirá ruido paramétrico de alta frecuencia que desestabilice el piso de cuantización del ADC del ESP32.
  * **Cálculo de potencia activa real:** La medición síncrona de las magnitudes instantáneas $v[n]$ e $i[n]$ en bucle cerrado permitirá procesar la potencia $P$ con una exactitud estadísticamente superior a los modelos básicos (que asumen un voltaje nominal constante de 127 V).
  * **Viabilidad económica:** La Lista de Materiales completa (BOM) no superará los $600.00 MXN, materializando una reducción de costo de al menos el 60% frente a analizadores de espectro comerciales.

## 8. Diseño metodológico

El bosquejo del método está diseñado para asegurar tanto la **validez interna** (en pruebas controladas de calibración) como la **validez externa** (operación real en campo), asegurando trazabilidad y repetibilidad.

### Universo (Población de estudio)
En el contexto de un estudio experimental con prototipos de hardware, el universo no está constituido por sujetos humanos, sino por el conjunto de **todas las posibles condiciones de carga eléctrica de medición** que pueden presentarse en una vivienda residencial monofásica, dentro del rango físico de operación del sensor (0 a 30 A). El entorno futuro de validación de campo será una vivienda unifamiliar con servicio monofásico (127 V, 60 Hz) ubicada en Tenango del Valle, Estado de México.

### Tamaño de la muestra
Se establecerán **270 pares de observaciones** (prototipo frente a instrumento patrón) distribuidas en 9 niveles de carga discretos (0.5 A, 1 A, 2 A, 5 A, 10 A, 15 A, 20 A, 25 A y 30 A) con un mínimo de 30 repeticiones por cada nivel. El muestreo será **no probabilístico intencional**, asegurando meticulosamente la cobertura del rango dinámico completo del dispositivo.
* **Criterios de inclusión:** Cargas resistivas puras (lámparas incandescentes, planchas) y cargas inductivas comunes (motores fraccionarios, ventiladores), conectadas a la red monofásica de 127 V/60 Hz.
* **Criterios de exclusión:** Cargas que demanden una corriente inferior a 0.2 A (situadas en la zona muerta de umbral de ruido del ADC), infraestructura trifásica, y equipos que generen distorsión armónica extrema (variadores de frecuencia industriales).

### Tipos de investigación a realizar
* **Finalidad:** *Aplicada y Tecnológica* (transforma la teoría de procesamiento de señales en un prototipo tangible).
* **Enfoque:** *Cuantitativo* (el éxito depende de magnitudes numéricas verificables como $I_{RMS}$, $V_{RMS}$, $P$, y reducción de costos).
* **Alcance:** *Correlacional y Explicativo* (se analizará la correlación directa entre el instrumento patrón y el prototipo, explicando variables de desviación estadística).
* **Lugar:** Diseño *Mixto*, comenzando con una rigurosa fase experimental en el entorno aislado de un **laboratorio**, seguida de validaciones observacionales en **campo** (vivienda real).

### Tipo de instrumento a utilizar para la recolección de la información
El instrumento tecnológico de medición principal (DUT, *Device Under Test*) será el **Prototipo SME-IoT** (arquitectura ESP32, SCT-013, ZMPT101B). Su lectura será validada estadísticamente contra un **Multímetro TRMS calibrado (Instrumento Patrón)** con precisión típica de ±0.5%. La recolección aplicará la observación estructurada sistemática, sustentada por el registro de métricas de forma persistente y automatizada con una marca temporal (*timestamp*) en una **tarjeta microSD**, permitiendo la exportación a archivos CSV.

### Procesamiento y Análisis de Datos Estadísticos
Los datos recopilados en laboratorio y campo serán filtrados a través de herramientas especializadas (Python con NumPy/SciPy y Excel). Se ejecutarán las siguientes técnicas para comprobar empíricamente las métricas operacionales del prototipo frente al instrumento patrón:
* Análisis estadístico descriptivo (Media, Desviación Estándar).
* **Regresión lineal simple** para consolidar la ecuación de calibración de los sensores ($y = mx + b$).
* Correlación matemática a través de los coeficientes de **Pearson ($r$)** y **determinación ($R^2$)**.
* Medición precisa de la desviación mediante el **Error Porcentual Absoluto Medio (MAPE)**, el cual será crucial para aceptar o refutar el límite de tolerancia técnica (error $< 5\%$).
* **Gráficos de Bland-Altman** y análisis **t de Student pareada** (verificando antes con Shapiro-Wilk) para determinar rigurosamente la concordancia metrológica entre las mediciones dadas por el prototipo IoT vs. el multímetro de banco.

### Encuesta y Prueba Piloto Técnica
Se realizará una consulta técnica preliminar a 10 usuarios de tarifa doméstica en Tenango del Valle para identificar el umbral de inversión aceptable, estimándolo en un rango de $500 a $700 MXN. De forma complementaria y crucial, se ejecutará una **prueba piloto técnica acotada en campo** utilizando únicamente 2 a 3 niveles de carga. El propósito de este piloto es validar que el sistema logre la estabilización térmica adecuada (≥ 5 min sin saturar el ADC), revisar la coherencia de reconexión del protocolo MQTT en caso de cortes WiFi, y certificar la integridad de los datos vaciados en la SD, previo a dar inicio a la recolección experimental exhaustiva estipulada a futuro.

## 9. Cronograma

| Fase | Actividad | Inicio | Fin |
| :--- | :--- | :---: | :---: |
| F1 | Investigación de antecedentes y estructuración del planteamiento técnico | 02-Feb | 13-Feb |
| F2 | Definición de objetivos y delimitación del impacto del proyecto | 16-Feb | 06-Mar |
| F3 | Integración del marco teórico y revisión del estado del arte | 09-Mar | 20-Mar |
| F4 | Formulación de hipótesis y definición de variables | 23-Mar | 03-Abr |
| F5 | Diseño metodológico y preparación del protocolo experimental | 06-Abr | 24-Abr |
| F6 | Entrega del proyecto final (Protocolo de Investigación documental) | 27-Abr | 29-May |

## 10. Presupuesto y financiamiento

**Presupuesto detallado (MXN):**
* ESP32 DevKit V1: $130.00
* Sensor de Corriente SCT-013-030: $185.00
* Sensor de Voltaje ZMPT101B: $50.00
* Fuente Hi-Link HLK-PM01: $75.00
* Pantalla OLED SSD1306: $65.00
* Componentes pasivos (placa, resistencias, capacitores) y gabinete: $95.00
**Total aproximado:** $600.00 MXN

**Financiamiento:** 
El proyecto será autofinanciado por el investigador para el desarrollo del prototipo académico inicial en etapas posteriores.

## 11. Fuentes de información

* Arias, F. G. (2012). *El proyecto de investigación: Introducción a la metodología científica* (6ª ed.). Editorial Episteme.
* Bland, J. M., & Altman, D. G. (1986). Statistical methods for assessing agreement between two methods of clinical measurement. *The Lancet*, *1*(8476), 307–310. https://pubmed.ncbi.nlm.nih.gov/2868172/
* Comisión Federal de Electricidad. (2024). *Tarifas domésticas de energía eléctrica*. CFE. https://app.cfe.mx/Aplicaciones/CCFE/Tarifas/TarifasCRECasa/Casa.aspx
* Creswell, J. W., & Creswell, J. D. (2018). *Research design: Qualitative, quantitative, and mixed methods approaches* (5th ed.). SAGE Publications.
* Davis, F. D. (1989). Perceived usefulness, perceived ease of use, and user acceptance of information technology. *MIS Quarterly*, *13*(3), 319–340. https://doi.org/10.2307/249008
* Espressif Systems. (2022). *ESP32 Series Datasheet* (ver. 3.4). https://www.espressif.com/documentation/esp32_datasheet_en.pdf
* Hart, D. W. (2011). *Power electronics*. McGraw-Hill Education.
* Hernández Sampieri, R., Fernández Collado, C., & Baptista Lucio, M. del P. (2014). *Metodología de la investigación* (6ª ed.). McGraw-Hill Education.
* Kaselimi, M., Protopapadakis, E., Voulodimos, A., Doulamis, N., & Doulamis, A. (2022). Towards Trustworthy Energy Disaggregation: A Review of Challenges, Methods, and Perspectives for Non-Intrusive Load Monitoring. *Sensors*, *22*(15), 5872. https://doi.org/10.3390/s22155872
* Naciones Unidas. (2015). *Transformar nuestro mundo: La Agenda 2030 para el Desarrollo Sostenible*. https://sdgs.un.org/2030agenda
* Norma Oficial Mexicana NOM-001-SEDE-2012. *Instalaciones Eléctricas (Utilización)*. Diario Oficial de la Federación, México.
* Shapiro, S. S., & Wilk, M. B. (1965). An analysis of variance test for normality (complete samples). *Biometrika*, *52*(3–4), 591–611. https://doi.org/10.1093/biomet/52.3-4.591
* Tamayo y Tamayo, M. (2009). *El proceso de la investigación científica* (5. ed.). Limusa.

## 12. Anexos

### Anexo A: Matriz de operacionalización de las variables experimentales

Esta matriz define cómo las variables teóricas de la investigación serán medidas empíricamente por el prototipo, garantizando la rigurosidad cuantitativa del estudio.

| Variable | Tipo | Definición Conceptual | Definición Operacional (Instrumentación) | Unidad / Escala |
| :--- | :--- | :--- | :--- | :--- |
| **Carga Eléctrica** | Independiente | Demanda física de energía requerida por un electrodoméstico conectado a la red. | Corriente alterna inyectada de forma controlada a través de un banco de cargas resistivas e inductivas, capturada por el sensor SCT-013-030. | Amperios (A)<br>*Rango: 0.5 A – 30.0 A* |
| **Potencia Activa ($P$)** | Dependiente | Energía real consumida por la carga que produce un trabajo útil, considerando el desfase por el factor de potencia. | Promedio del producto iterativo de las lecturas analógicas instantáneas ($v[n]$ e $i[n]$) digitalizadas por el ADC1 del ESP32 a $f_s \approx 1$ kHz. | Vatios (W)<br>*Escala de Razón* |
| **Error Porcentual (MAPE)** | Dependiente | Desviación estadística promedio de la medición del prototipo respecto al valor real. | Diferencia absoluta entre la lectura del Multímetro TRMS calibrado (Patrón) y el Prototipo SME-IoT, dividida por el valor Patrón. | Porcentaje (%)<br>*Criterio de éxito: $<5\%$* |
| **Voltaje de Red** | Interviniente / Control | Diferencia de potencial eléctrico real suministrada por la CFE en la acometida. | Señal aislada obtenida mediante el ZMPT101B, digitalizada y centrada digitalmente para eliminar fluctuaciones y armónicos. | Voltios (V)<br>*Nominal: 127 V AC* |

### Anexo B: Borrador del instrumento de encuesta (Consulta técnica preliminar)

Este instrumento está fundamentado en el **Modelo de Aceptación de Tecnología (TAM)** propuesto por Davis (1989), adaptado para la evaluación de medidores inteligentes residenciales (*Smart Meters*). Evalúa la Utilidad Percibida (PU), Facilidad de Uso Percibida (PEOU), Confianza y Viabilidad Económica. Se aplicará a una muestra piloto de 10 usuarios residenciales.

**Objetivo:** Identificar la percepción de opacidad en la medición fiscal, evaluar la intención de adopción de tecnología IoT y validar empíricamente el umbral de viabilidad económica propuesto ($< 600$ MXN).

**Cuestionario (Escala Likert y Opción Múltiple):**

* **Sección 1: Utilidad Percibida (PU)**
  1. El recibo bimestral actual de CFE me permite entender claramente qué electrodomésticos consumen más energía en mi hogar.
     *(1: Totalmente en desacuerdo - 5: Totalmente de acuerdo)*
  2. Un dispositivo que me muestre mi consumo de energía en tiempo real en mi celular me ayudaría a reducir mis costos eléctricos.
     *(1: Totalmente en desacuerdo - 5: Totalmente de acuerdo)*

* **Sección 2: Facilidad de Uso y Confianza (PEOU & Trust)**
  3. Me preocupa la privacidad de mis datos de consumo si utilizo un dispositivo comercial que dependa de suscripciones o servidores extranjeros.
     *(1: Totalmente en desacuerdo - 5: Totalmente de acuerdo)*
  4. Me sentiría más seguro instalando un sensor "no intrusivo" (que solo se sujeta sobre el cable principal sin cortarlo) en comparación con solicitar modificaciones al cableado de mi casa.
     *(1: Totalmente en desacuerdo - 5: Totalmente de acuerdo)*

* **Sección 3: Viabilidad Económica e Intención de Uso (BI)**
  5. Sabiendo que los monitores de energía comerciales (ej. Sense o Shelly EM) cuestan más de $1,500 MXN, ¿Cuál es la inversión máxima que realizaría por un dispositivo de código abierto fabricado localmente que cumpla la misma función?
     [ ] Menos de $500 MXN
     [ ] Entre $500 y $700 MXN
     [ ] Entre $700 y $1,000 MXN
     [ ] Más de $1,000 MXN

### Anexo C: Diagrama esquemático preliminar del circuito de acondicionamiento de señal

Debido a que las señales eléctricas de la red domiciliaria oscilan en valores alternos (AC) que incluyen semiciclos de voltaje negativo, y el convertidor analógico-digital (ADC) del microcontrolador ESP32 únicamente admite valores unipolares positivos (0 a 3.3 V DC), es mandatario diseñar una etapa de acondicionamiento analógico previa. El siguiente esquema lógico fundamenta la construcción física del prototipo:

1. **Acondicionamiento de Corriente (Sensor SCT-013-030):**
   * El sensor de núcleo partido se ancla magnéticamente al conductor de fase. Su salida natural es una señal alterna proporcional (0 a 1 V AC).
   * Se implementa un divisor de tensión resistivo (constituido por dos resistores de precisión de $10\text{ k}\Omega$ en serie puenteando el pin de 3.3 V y GND del ESP32).
   * El punto medio de este divisor inyecta un nivel DC o *offset* de exactamente **1.65 V** a la señal del sensor.
   * Se añade un capacitor electrolítico de desacoplo de $10\,\mu\text{F}$ en paralelo al resistor conectado a tierra, estabilizando la referencia de voltaje y mitigando el ruido térmico de la fuente.
   * La onda de corriente ahora se desplaza en el plano cartesiano (oscilando de forma segura entre $\approx 0.65$ V y $2.65$ V) ingresando directamente al pin analógico **GPIO 32 (ADC1)**.
2. **Acondicionamiento de Voltaje (Módulo ZMPT101B):**
   * El transformador de aislamiento galvánico miniatura reduce y muestrea la red de 127 V AC.
   * Su placa integradora requiere ser alimentada a 5 V DC y regulada mediante su potenciómetro de ajuste de amplitud.
   * Al igual que la corriente, su salida analógica se acopla a un divisor de tensión resistivo independiente para sumarle un *offset* de 1.65 V.
   * La señal desplazada se conecta de forma segura al pin **GPIO 33 (ADC1)**.
3. **Módulo de Alimentación Aislada (SMPS):**
   * Se incorpora el bloque conversor Hi-Link HLK-PM01 conectado de forma paralela a los 127 V AC.
   * Entrega 5 V DC aislados magnéticamente en su salida, alimentando el pin `VIN` del ESP32 y el pin `VCC` de la placa del sensor ZMPT101B, consolidando la total autonomía energética del instrumento.
