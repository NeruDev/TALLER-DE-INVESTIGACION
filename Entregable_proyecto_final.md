# Diseño e Implementación de un Sistema IoT de Bajo Costo para la Monitorización No Intrusiva de Consumo Eléctrico Residencial mediante Arquitectura ESP32

## Contenido

* Antecedentes del problema
* Planteamiento del problema
* Objetivo general
* Objetivos específicos
* Justificación
* Marco Teórico
* Hipótesis
* Diseño metodológico
  * Universo
  * Tamaño de la muestra
  * Tipos de investigación a realizar
  * Tipo de instrumento a utilizar para la recolección de la información
  * Encuesta
* Cronograma
* Presupuesto y financiamiento
* Fuentes de información
* Anexos

## Antecedentes del problema

La gestión de la demanda energética es fundamental en la transición hacia redes eléctricas inteligentes (*Smart Grids*). A nivel global, los Objetivos de Desarrollo Sostenible (ODS 7 y 12) subrayan la necesidad de mejorar la eficiencia energética residencial. En México, el esquema tarifario de la Comisión Federal de Electricidad (CFE) estructura el costo en categorías escalonadas (tarifas 1 a 1F), penalizando el alto consumo mediante la tarifa DAC (Doméstica de Alto Consumo), la cual elimina el subsidio gubernamental. Sin embargo, los medidores convencionales electromecánicos o digitales estándar funcionan como dispositivos de registro acumulativo sin capacidad de retroalimentación instantánea, limitando la capacidad del usuario para corregir hábitos de consumo en tiempo real.

Históricamente, el monitoreo no intrusivo de carga (NILM) ha evolucionado desde métodos analógicos hasta arquitecturas basadas en Internet de las Cosas (IoT). Plataformas de hardware abierto como OpenEnergyMonitor han demostrado la viabilidad de usar sensores de corriente de núcleo partido y la biblioteca `EmonLib`, pero sus costos de adquisición e importación (>$2,000 MXN) siguen siendo elevados para el mercado nacional. Estudios recientes como Kaselimi et al. (2022) identifican como brechas pendientes la confiabilidad en escenarios reales y la accesibilidad para su implementación masiva en el sector doméstico.

## Planteamiento del problema

El problema central radica en la desconexión entre el consumo físico de energía y la conciencia del usuario. La falta de herramientas de diagnóstico accesibles impide la detección de consumos fantasma o ineficiencias en electrodomésticos. Las causas son multifactoriales: opacidad de la medición fiscal, barreras económicas (costo de equipos comerciales como Sense o Shelly EM >$1,500 MXN), complejidad de instalación y la invisibilidad inherente del recurso eléctrico. Además, las fluctuaciones de voltaje en la red mexicana distorsionan las estimaciones basadas exclusivamente en medición de corriente.

Pregunta de investigación: ¿Es factible desarrollar e implementar un sistema de monitoreo eléctrico residencial IoT que, mediante la medición simultánea de voltaje y corriente con sensores no intrusivos y un microcontrolador ESP32, reduzca el costo de adquisición en un 60% respecto a analizadores de red comerciales, garantizando una precisión superior al 95% en el cálculo de potencia activa real y permitiendo la detección de anomalías en el suministro, validándolo en una vivienda unifamiliar con servicio monofásico ubicada en Tenango del Valle, Estado de México?

## Objetivo general

Diseñar, implementar y validar un sistema de monitoreo de consumo eléctrico residencial de bajo costo y no intrusivo, basado en el microcontrolador ESP32 y sensores de corriente tipo *clamp* (SCT-013) y de voltaje (ZMPT101B), capaz de calcular la potencia activa en tiempo real con un error inferior al 5% respecto a instrumentación de referencia, y de transmitir los datos de manera inalámbrica mediante conectividad WiFi.

## Objetivos específicos

* Analizar los requerimientos funcionales y no funcionales del sistema bajo las condiciones de la infraestructura eléctrica mexicana y las restricciones técnicas de los componentes.
* Diseñar la etapa de hardware del sistema, incluyendo el circuito de acondicionamiento de señal para los sensores SCT-013, ZMPT101B, y el sistema de alimentación conmutada AC-DC integrado.
* Desarrollar el firmware de adquisición de datos y procesamiento digital de señales —cálculo de corriente eficaz ($I_{RMS}$), voltaje eficaz ($V_{RMS}$) y potencia activa ($P$)— sobre la arquitectura de doble núcleo del ESP32.
* Implementar la interfaz de usuario local (pantalla OLED SSD1306) y el módulo de almacenamiento local (tarjeta microSD) para la visualización y registro histórico.
* Validar el desempeño del prototipo mediante pruebas comparativas contra instrumentación patrón (multímetro TRMS calibrado) en laboratorio y campo.
* Evaluar la viabilidad económica del dispositivo mediante el análisis de la lista de materiales (BOM) y la comparación de costos frente al mercado.

## Justificación

La investigación es conveniente porque proporciona una herramienta de diagnóstico instantáneo frente a la opacidad de la medición fiscal bimestral de CFE. Tiene relevancia social al democratizar el acceso a tecnología de eficiencia energética para familias mexicanas, reduciendo el costo de inversión a ~$600 MXN. Desde una implicación práctica, permite identificar patrones de uso ineficiente sin riesgos de instalación intrusiva, eliminando la necesidad de alterar el cableado fijo de la vivienda. Aporta valor teórico al validar la aplicabilidad de la Ley de Faraday y el teorema de Nyquist-Shannon en una plataforma de hardware con restricciones severas de costo y resolución (ADC de 12 bits).

## Marco Teórico

El desarrollo de sistemas de monitoreo eléctrico residencial basados en microcontroladores y plataformas IoT ha sido objeto de investigación creciente. Proyectos de código abierto como OpenEnergyMonitor han establecido precedentes en el monitoreo no intrusivo, pero con barreras de costo e importación significativas. A continuación, se definen las bases teóricas que sustentan la presente investigación:

* **Electromagnetismo y principios de medición:** El funcionamiento del sensor de corriente SCT-013 se fundamenta en la **Ley de Faraday de la Inducción Electromagnética** ($\varepsilon = -d\Phi_B/dt$). El núcleo ferromagnético concentra el flujo magnético del conductor primario para inducir una corriente proporcional en el secundario, permitiendo una medición aislada y segura. Para sistemas de corriente alterna, se requiere calcular los valores eficaces ($I_{RMS}$ y $V_{RMS}$).
* **Teoría de muestreo y procesamiento digital:** La transición de las señales analógicas al dominio digital está regida por el **teorema de Nyquist-Shannon** ($f_s \geq 2 f_{max}$). El sistema empleará una frecuencia de muestreo aproximada de 1 kHz para capturar fielmente la onda de 60 Hz. Los valores eficaces se calcularán mediante sumatorias finitas.
* **Cálculo de la potencia eléctrica:** La potencia activa ($P$) se calculará como el promedio del producto de las muestras instantáneas de voltaje y corriente: $P = \frac{1}{N} \sum v[n] \cdot i[n]$. Este método es superior a la simple estimación de potencia aparente, ya que incorpora de forma implícita el efecto del factor de potencia ($\cos\phi$) al contemplar el desfase real entre ambas ondas.
* **Sistemas embebidos e IoT:** La unidad central será el **SoC ESP32**, el cual posee una arquitectura de doble núcleo Xtensa® LX6 de 32 bits. Se utilizará el Núcleo 1 para la adquisición ininterrumpida de datos desde su convertidor analógico-digital (ADC de 12 bits) y el Núcleo 0 para gestionar la conectividad WiFi y el protocolo de telemetría MQTT.
* **Fuentes de alimentación conmutadas (SMPS):** El sistema integrará un módulo convertidor tipo *buck* de alta frecuencia (Hi-Link) para convertir eficientemente (con rendimiento >70%) la tensión alterna de 127 V a los niveles de continua requeridos por la electrónica, asegurando aislamiento galvánico y un diseño autónomo.
* **Marco Legal y Normativo:** El prototipo se apegará a los lineamientos de no intervención física estipulados en la **NOM-001-SEDE-2012** (Instalaciones Eléctricas). Es imperativo señalar que el sistema será una herramienta de autodiagnóstico informativo y no un instrumento con validez de facturación fiscal.

## Hipótesis

* **Hipótesis de investigación ($H_i$):** Es factible desarrollar un sistema de monitoreo eléctrico residencial basado en IoT que, mediante el uso de hardware de código abierto y componentes genéricos optimizados (ESP32, SCT-013, ZMPT101B), reduzca los costos de manufactura por debajo de los $600.00 MXN por unidad, manteniendo un error de medición de potencia activa inferior al 5% en cargas domésticas estándar superiores a 25 W.
* **Hipótesis nula ($H_0$):** El sistema propuesto no alcanza la precisión requerida (error porcentual $> 5\%$) o su costo de manufactura excede los $600.00 MXN por unidad, invalidando la viabilidad técnico-económica de la propuesta.
* **Hipótesis alternativa ($H_1$):** El sistema propuesto logra un costo de manufactura ≤ $600.00 MXN por unidad y alcanza un error porcentual de potencia activa ≤ 5% en cargas domésticas superiores a 25 W.
* **Hipótesis específicas:**
  * El sensor SCT-013 acondicionado con un offset a 1.65 V mantendrá una relación lineal con la corriente real con $R^2 > 0.98$ en el rango de 0.5 A a 30 A.
  * La fuente integrada tipo Hi-Link presentará un rizado menor a 50 mVpp sin introducir ruido significativo en las mediciones del ADC del ESP32.
  * La medición simultánea de voltaje y corriente instantánea permitirá calcular la potencia activa con mayor precisión que las estimaciones basadas en voltaje nominal constante de 127 V.
  * La lista de materiales (BOM) no excederá los $600.00 MXN, logrando una reducción de costo de al menos 60% respecto a soluciones comerciales comparables.

## Diseño metodológico

### Universo
El conjunto de todas las posibles condiciones de carga eléctrica que pueden presentarse en una vivienda residencial monofásica, dentro del rango de operación del sensor de corriente (0 a 30 A). El entorno futuro de validación de campo será una vivienda unifamiliar con servicio monofásico (127 V, 60 Hz) ubicada en Tenango del Valle, Estado de México.

### Tamaño de la muestra
Se establecerán 270 pares de observaciones distribuidas en 9 niveles de carga (0.5 A, 1 A, 2 A, 5 A, 10 A, 15 A, 20 A, 25 A y 30 A) con un mínimo de 30 repeticiones por nivel. El muestreo será no probabilístico intencional, asegurando la cobertura del rango operativo completo del sensor.

### Tipos de investigación a realizar
La investigación será aplicada y tecnológica por su finalidad; cuantitativa por el enfoque de datos; correlacional-explicativa por su alcance; y experimental por la manipulación deliberada de la variable independiente (carga) observando la respuesta en el sistema de medición. Se empleará un diseño metodológico mixto (laboratorio y campo).

### Tipo de instrumento a utilizar para la recolección de la información
El instrumento principal será el Prototipo SME-IoT (ESP32, SCT-013, ZMPT101B) que será validado contra un multímetro TRMS calibrado. La recolección empleará observación estructurada, apoyada por registro automatizado de métricas procesadas con marca temporal mediante un módulo de tarjeta microSD y exportación por monitor serial a formato CSV para su posterior análisis estadístico.

### Encuesta
Se realizará una consulta técnica preliminar a 10 usuarios de tarifa doméstica en Tenango del Valle para identificar el umbral de inversión aceptable, estimándolo en un rango de $500 a $700 MXN. Complementariamente, se ejecutará una prueba piloto técnica acotada en campo (2 a 3 niveles de carga) para validar fallas operacionales, tiempos de reconexión y la integridad del registro automático antes de iniciar la recolección experimental exhaustiva planificada a futuro.

## Cronograma

| Fase | Actividad | Inicio | Fin |
| :--- | :--- | :---: | :---: |
| F1 | Investigación de antecedentes y estructuración del planteamiento técnico | 02-Feb | 13-Feb |
| F2 | Definición de objetivos y delimitación del impacto del proyecto | 16-Feb | 06-Mar |
| F3 | Integración del marco teórico y revisión del estado del arte | 09-Mar | 20-Mar |
| F4 | Formulación de hipótesis y definición de variables | 23-Mar | 03-Abr |
| F5 | Diseño metodológico y preparación del protocolo experimental | 06-Abr | 24-Abr |
| F6 | Entrega del proyecto final (Protocolo de Investigación documental) | 27-Abr | 29-May |

## Presupuesto y financiamiento

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

## Fuentes de información

Arias, F. G. (2012). *El proyecto de investigación: Introducción a la metodología científica* (6ª ed.). Editorial Episteme.
Bland, J. M., & Altman, D. G. (1986). Statistical methods for assessing agreement between two methods of clinical measurement. *The Lancet*, *1*(8476), 307–310. https://pubmed.ncbi.nlm.nih.gov/2868172/
Comisión Federal de Electricidad. (2024). *Tarifas domésticas de energía eléctrica*. CFE. https://app.cfe.mx/Aplicaciones/CCFE/Tarifas/TarifasCRECasa/Casa.aspx
Creswell, J. W., & Creswell, J. D. (2018). *Research design: Qualitative, quantitative, and mixed methods approaches* (5th ed.). SAGE Publications.
Espressif Systems. (2022). *ESP32 Series Datasheet* (ver. 3.4). https://www.espressif.com/documentation/esp32_datasheet_en.pdf
Hart, D. W. (2011). *Power electronics*. McGraw-Hill Education.
Hernández Sampieri, R., Fernández Collado, C., & Baptista Lucio, M. del P. (2014). *Metodología de la investigación* (6ª ed.). McGraw-Hill Education.
Kaselimi, M., Protopapadakis, E., Voulodimos, A., Doulamis, N., & Doulamis, A. (2022). Towards Trustworthy Energy Disaggregation: A Review of Challenges, Methods, and Perspectives for Non-Intrusive Load Monitoring. *Sensors*, *22*(15), 5872. https://doi.org/10.3390/s22155872
Naciones Unidas. (2015). *Transformar nuestro mundo: La Agenda 2030 para el Desarrollo Sostenible*. https://sdgs.un.org/2030agenda
Norma Oficial Mexicana NOM-001-SEDE-2012. *Instalaciones Eléctricas (Utilización)*. Diario Oficial de la Federación, México.
Shapiro, S. S., & Wilk, M. B. (1965). An analysis of variance test for normality (complete samples). *Biometrika*, *52*(3–4), 591–611. https://doi.org/10.1093/biomet/52.3-4.591
Tamayo y Tamayo, M. (2009). *El proceso de la investigación científica* (5. ed.). Limusa.

## Anexos

Anexo A: Diagrama esquemático del circuito de acondicionamiento de señal.
Anexo B: Código fuente del algoritmo de cálculo True RMS y Potencia Activa.
Anexo C: Reporte de calibración y curvas de error porcentual (MAPE).
Anexo D: Prueba piloto: Protocolo de verificación de integridad de datos.
Anexo E: Técnicas de procesamiento y análisis estadístico (Bland-Altman y Regresión).
