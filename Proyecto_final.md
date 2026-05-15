<!--
===================================================================
METADATOS DEL DOCUMENTO
===================================================================
Proyecto    : Diseño e Implementación de un Sistema IoT de Bajo
              Costo para la Monitorización No Intrusiva de Consumo
              Eléctrico Residencial mediante Arquitectura ESP32
Área        : Ingeniería Electrónica / Investigación Académica
-------------------------------------------------------------------
Archivo     : Proyecto_final.md
Tipo        : Documento consolidado (protocolo + desarrollo)
Descripción : Versión consolidada para entrega institucional.
              Integra el formato solicitado en Formato_proyecto_final.md
              y consolida contenido del documento maestro.
Autor       : Investigador (compilado con apoyo de IA)
Creado      : 2026-05-15
Etapa       : Taller de Investigación 1 – Consolidación final
Estado      : BORRADOR CONSOLIDADO – Pendiente de revisión final
Fuente base : Proyecto completo.md (documento maestro)
Ubicación   : Tenango del Valle, Estado de México
===================================================================
-->

# Diseño e Implementación de un Sistema IoT de Bajo Costo para la Monitorización No Intrusiva de Consumo Eléctrico Residencial mediante Arquitectura ESP32

## Datos de identificación

- Investigador: Jesus Uriel Uribe Diaz
- Institución: Instituto Tecnológico de Toluca
- Asignatura / Unidad: Taller de Investigación 1
- Asesor(a): _______________________________
- Periodo de ejecución: 02 de febrero de 2026 al 29 de mayo de 2026
- Ubicación del estudio: Tenango del Valle, Estado de México
- Fecha de entrega: _______________________________

## Índice

1. [Resumen](#resumen)
2. [1 Antecedentes del problema](#1-antecedentes-del-problema)
3. [2 Planteamiento del problema](#2-planteamiento-del-problema)
4. [3 Objetivos de la investigación](#3-objetivos-de-la-investigación)
5. [4 Justificación](#4-justificación)
6. [5 Marco teórico](#5-marco-teórico)
7. [6 Hipótesis](#6-hipótesis)
8. [7 Diseño metodológico](#7-diseño-metodológico)
9. [8 Cronograma](#8-cronograma)
10. [9 Presupuesto y financiamiento](#9-presupuesto-y-financiamiento)
11. [10 Diseño e implementación del sistema](#10-diseño-e-implementación-del-sistema)
12. [11 Análisis de riesgos y limitaciones técnicas](#11-análisis-de-riesgos-y-limitaciones-técnicas)
13. [12 Resultados preliminares y discusión](#12-resultados-preliminares-y-discusión)
14. [13 Conclusiones parciales y trabajo futuro](#13-conclusiones-parciales-y-trabajo-futuro)
15. [14 Fuentes de información](#14-fuentes-de-información)
16. [15 Anexos](#15-anexos)

---

## Resumen

El presente trabajo aborda la problemática de la eficiencia energética en el sector residencial de México, donde la falta de retroalimentación inmediata sobre el consumo eléctrico deriva en ineficiencias operativas y sobrecostos en la facturación bajo el esquema tarifario de la Comisión Federal de Electricidad (CFE). Se propone el diseño e implementación de un prototipo de medición inteligente (*Smart Meter*) de arquitectura abierta y bajo costo, basado en el microcontrolador ESP32 y sensores de corriente no intrusivos SCT-013-030, complementado con un módulo de medición de voltaje ZMPT101B y una fuente de alimentación conmutada compacta integrada. La investigación se define como de tipo aplicada y tecnológica con enfoque cuantitativo, alcance correlacional-experimental y diseño mixto de laboratorio y campo. La metodología emplea algoritmos de procesamiento digital de señales para el cálculo de la corriente eficaz ($I_{RMS}$), el voltaje eficaz ($V_{RMS}$) y la potencia activa ($P$) en tiempo real. Los resultados preliminares reportan un coeficiente de determinación $R^2 > 0.98$ en pruebas de linealidad y un error porcentual absoluto medio (MAPE) de $\pm 2.3\%$ para cargas superiores a 200 W, con un costo total de materiales de aproximadamente $600.00 MXN por unidad, lo que representa una reducción superior al 60% respecto a soluciones comerciales equivalentes. Estos resultados validan la viabilidad técnico-económica del prototipo como herramienta informativa de gestión energética para el usuario residencial.

**Palabras clave:** IoT, Eficiencia Energética, ESP32, Sensores No Intrusivos, Procesamiento Digital de Señales, Smart Grid, Monitoreo Eléctrico Residencial.

---

## 1 Antecedentes del problema

La gestión de la demanda energética constituye un pilar fundamental en la transición global hacia redes eléctricas inteligentes (*Smart Grids*). En el marco de los Objetivos de Desarrollo Sostenible de la Organización de las Naciones Unidas —particularmente el ODS 7 (Energía asequible y no contaminante) y el ODS 12 (Producción y consumo responsables)—, la eficiencia energética en el sector residencial ha sido identificada como un área prioritaria de intervención tecnológica (Naciones Unidas, 2015).

En el contexto mexicano, el esquema tarifario doméstico administrado por la Comisión Federal de Electricidad (CFE) estructura el costo de la energía eléctrica residencial en categorías escalonadas (tarifas 1, 1A, 1B, 1C, 1D, 1E y 1F), siendo la tarifa DAC (Doméstica de Alto Consumo) la que mayor impacto económico representa para el usuario, dado que elimina el subsidio gubernamental y aplica el costo real por kilowatt-hora (CFE, 2024). Sin embargo, los medidores electromecánicos o digitales estándar instalados por la empresa suministradora funcionan como dispositivos de registro acumulativo sin capacidad de retroalimentación instantánea, entregando datos agregados de forma mensual o bimestral. Esta condición elimina la posibilidad de que el usuario final corrija sus hábitos de consumo en tiempo real.

La evolución del Internet de las Cosas (IoT) y la disponibilidad comercial de microcontroladores de bajo costo con conectividad inalámbrica integrada —como el ESP32 de Espressif Systems— han abierto una ventana de oportunidad para el desarrollo de soluciones de medición inteligente accesibles para el mercado residencial. Paralelamente, la madurez de los sensores de corriente de núcleo partido (tipo *clamp*), basados en el principio de inducción electromagnética, permite la implementación de sistemas de monitoreo no intrusivo de carga (NILM, *Non-Intrusive Load Monitoring*) que no requieren la intervención física del cableado eléctrico existente (Kaselimi et al., 2022).

En este escenario convergen la necesidad social de transparencia en el consumo energético, la viabilidad tecnológica de las plataformas IoT de bajo costo y la urgencia ambiental de reducir la huella de carbono del sector residencial, configurando el espacio de investigación que da origen al presente proyecto.

---

## 2 Planteamiento del problema

### 2.1 Descripción del problema

El problema central que aborda esta investigación radica en la desconexión entre el consumo físico de energía eléctrica en viviendas residenciales mexicanas y la conciencia del usuario sobre dicho consumo. Sin herramientas de diagnóstico accesibles, resulta imposible para una familia identificar electrodomésticos ineficientes, detectar consumos fantasma en modo *standby* o correlacionar hábitos de uso con el costo reflejado en la facturación.

Las causas de esta problemática son multifactoriales:

1. **Opacidad de la medición fiscal:** Los medidores de CFE son dispositivos acumulativos que no ofrecen interfaces de datos instantáneos accesibles para el usuario dentro del hogar. Funcionan como una "caja negra" cuya única salida de información es el recibo bimestral.

2. **Barreras económicas de acceso:** Las soluciones comerciales de monitoreo energético residencial —como Sense, Emporia Vue o Shelly EM— presentan precios de importación que frecuentemente superan los $1,500.00 MXN, excediendo el umbral de inversión que la clase media mexicana está dispuesta a destinar a dispositivos de instrumentación doméstica.

3. **Complejidad de instalación:** Un número significativo de las soluciones disponibles requiere intervención intrusiva en el tablero eléctrico principal, lo que implica riesgos de seguridad eléctrica y la necesidad de mano de obra especializada certificada.

4. **Invisibilidad inherente del recurso:** La electricidad es un recurso intangible cuyo consumo no es perceptible por los sentidos humanos, lo que dificulta la formación de una cultura de ahorro energético sin el apoyo de herramientas de visualización.

5. **Variabilidad del suministro eléctrico:** Las fluctuaciones de voltaje en la red pública mexicana —documentadas como un fenómeno frecuente en zonas suburbanas— distorsionan las estimaciones de consumo basadas exclusivamente en medición de corriente con voltaje nominal asumido, e introduce riesgos adicionales para equipos electrónicos sensibles y motores de electrodomésticos.

Los efectos derivados de esta situación son cuantificables: sobrecostos en la facturación eléctrica y riesgo permanente de caer en tarifa DAC; desperdicio energético acumulado por la presencia de consumos fantasma no detectados; incremento de la demanda agregada sobre la red eléctrica nacional con el consecuente aumento en la generación y emisiones de $CO_2$; y deterioro prematuro de equipos domésticos por variaciones de voltaje no diagnosticadas.

### 2.2 Pregunta de investigación

> ¿Es factible desarrollar e implementar un sistema de monitoreo eléctrico residencial IoT que, mediante la medición simultánea de voltaje y corriente con sensores no intrusivos y un microcontrolador ESP32, reduzca el costo de adquisición en un 60% respecto a analizadores de red comerciales, garantizando una precisión superior al 95% en el cálculo de potencia activa real y permitiendo la detección de anomalías en el suministro, validándolo en una vivienda unifamiliar con servicio monofásico ubicada en Tenango del Valle, Estado de México?

Esta pregunta integra variables cuantificables (costo en MXN, porcentaje de error, porcentaje de reducción de precio), un criterio de éxito numérico explícito y una delimitación tecnológica clara (ESP32, sensores no intrusivos, medición simultánea de voltaje y corriente), cumpliendo con los criterios de especificidad, medibilidad y factibilidad establecidos por Creswell y Creswell (2018) para preguntas de investigación cuantitativa.

### 2.3 Delimitaciones y alcances

| Tipo | Descripción |
|---|---|
| **Temática** | El proyecto se circunscribe al monitoreo de consumo eléctrico residencial; no se abarca la generación distribuida (sistemas fotovoltaicos), el balanceo de carga industrial ni la desagregación avanzada de cargas mediante algoritmos de aprendizaje automático. |
| **Espacial** | El entorno de validación de campo es una vivienda unifamiliar con servicio monofásico (127 V, 60 Hz) ubicada en Tenango del Valle, Estado de México. |
| **Temporal** | El ciclo de diseño, implementación y validación se ejecuta dentro del periodo académico vigente. |
| **Tecnológica** | El sistema se basa exclusivamente en la plataforma ESP32 (Espressif Systems), sensor de corriente SCT-013-030 (30 A / 1 V), sensor de voltaje ZMPT101B y fuente conmutada AC-DC tipo Hi-Link. La precisión de medición se garantiza únicamente para corrientes superiores a 0.2 A (aproximadamente 25 W), debido a la zona muerta del ADC. |
| **Económica** | El presupuesto de materiales se acota a un máximo de $600.00 MXN por unidad de prototipo, utilizando componentes genéricos disponibles en el mercado nacional. |

**Limitaciones técnicas identificadas (síntesis):**

1. No linealidad del ADC del ESP32.
2. Conflicto ADC2/WiFi (uso exclusivo de ADC1 para sensado).
3. Atenuación de WiFi por tablero metálico (instalación en caja plástica externa adyacente).
4. Restricción a servicio monofásico (1 fase + neutro).
5. Ancho de banda limitado para transitorios de alta frecuencia.

---

## 3 Objetivos de la investigación

### 3.1 Objetivo general

Diseñar, implementar y validar un sistema de monitoreo de consumo eléctrico residencial de bajo costo y no intrusivo, basado en el microcontrolador ESP32 y sensores de corriente tipo *clamp* (SCT-013) y de voltaje (ZMPT101B), capaz de calcular la potencia activa en tiempo real con un error inferior al 5% respecto a instrumentación de referencia, y de transmitir los datos de manera inalámbrica mediante conectividad WiFi.

### 3.2 Objetivos específicos

1. **Analizar** los requerimientos funcionales y no funcionales del sistema de monitoreo con base en las condiciones de la infraestructura eléctrica residencial mexicana y las restricciones técnicas de los componentes seleccionados.
2. **Diseñar** la etapa de hardware del sistema, incluyendo el circuito de acondicionamiento de señal para los sensores SCT-013, ZMPT101B, y el sistema de alimentación conmutada AC-DC integrado.
3. **Desarrollar** el firmware de adquisición de datos, procesamiento digital de señales —cálculo de corriente eficaz ($I_{RMS}$), voltaje eficaz ($V_{RMS}$) y potencia activa ($P$)— y transmisión inalámbrica, sobre la arquitectura de doble núcleo del ESP32.
4. **Implementar** la interfaz de usuario local (pantalla OLED SSD1306 vía protocolo I2C) y el módulo de almacenamiento local (tarjeta microSD) para la visualización de métricas en tiempo real y el registro histórico de datos.
5. **Validar** el desempeño del prototipo mediante pruebas comparativas contra instrumentación patrón (multímetro TRMS calibrado) en condiciones controladas de laboratorio y en una instalación residencial real.
6. **Evaluar** la viabilidad económica del dispositivo mediante el análisis de la lista de materiales (BOM) y la comparación porcentual de costos frente a soluciones comerciales del mercado.

---

## 4 Justificación

La pertinencia de esta investigación se fundamenta en cinco dimensiones, siguiendo los criterios de evaluación propuestos por Hernández Sampieri et al. (2014):

**Conveniencia.** El proyecto proporciona una herramienta de diagnóstico energético que permite al usuario residencial cuantificar su consumo eléctrico en tiempo real, identificar patrones de uso ineficiente y tomar decisiones informadas para optimizar el gasto. A diferencia de los medidores fiscales de CFE, que solo entregan datos acumulados bimestralmente, el sistema propuesto ofrece retroalimentación instantánea mediante una interfaz local (pantalla OLED) y una interfaz remota (plataforma web).

**Relevancia social.** Los principales beneficiarios son las familias de clase media y media-baja en México, particularmente aquellas en riesgo de incurrir en la tarifa DAC. Al democratizar el acceso a tecnología de medición inteligente —reduciendo el costo de adquisición a aproximadamente $600.00 MXN frente a los más de $1,500.00 MXN de las alternativas comerciales—, se empodera al usuario con información para reducir su gasto eléctrico y su huella de carbono.

**Implicaciones prácticas.** El sistema resuelve directamente el problema de invisibilidad del consumo eléctrico. Su diseño no intrusivo elimina los riesgos asociados a la manipulación del cableado eléctrico, y su arquitectura de alimentación integrada (fuente conmutada AC-DC) permite una instalación autónoma sin dependencia de adaptadores externos.

**Valor teórico.** La investigación valida la aplicabilidad de principios consolidados —Ley de Faraday para la inducción en el sensor SCT-013, teorema de Nyquist-Shannon para el muestreo del ADC, y algoritmos de procesamiento digital de señales para el cálculo de potencia activa real— en una plataforma de hardware con restricciones severas de costo y recursos computacionales.

**Utilidad metodológica.** El proyecto propone un protocolo de calibración replicable para sensores de corriente tipo *clamp* operando con convertidores analógico-digitales de resolución limitada (12 bits).

---

## 5 Marco teórico

### 5.1 Antecedentes de la investigación

El desarrollo de sistemas de monitoreo eléctrico residencial basados en microcontroladores y plataformas IoT ha sido objeto de investigación creciente durante la última década. A continuación se revisan los antecedentes más relevantes para el presente proyecto.

Kaselimi et al. (2022) presentaron una revisión exhaustiva de los métodos, desafíos y perspectivas del monitoreo no intrusivo de carga (NILM), trazando la evolución desde las firmas de potencia originales hasta las arquitecturas modernas basadas en aprendizaje profundo e IoT. Los autores identifican como brechas pendientes la confiabilidad en escenarios reales, la generalización entre hogares y la limitada disponibilidad de conjuntos de datos abiertos. Desde la perspectiva del presente proyecto, esta revisión fundamenta la elección del enfoque no intrusivo como paradigma de monitoreo y confirma la vigencia de la medición en un solo punto de la acometida.

Ramadan et al. (2024) propusieron un sistema de gestión energética para microrredes residenciales que integra técnicas NILM con infraestructura IoT, logrando la desagregación de cargas individuales a partir de la medición agregada en el punto de acometida. Los autores validaron la viabilidad de combinar algoritmos de predicción de consumo con plataformas conectadas para la gestión de demanda en tiempo real. Sin embargo, su implementación se orientó a microrredes con generación distribuida y hardware de gama industrial, sin abordar la restricción de costo que caracteriza el mercado residencial mexicano. Esta brecha es precisamente la que el presente proyecto busca cubrir mediante la arquitectura de bajo costo basada en ESP32 y sensores genéricos.

El proyecto de código abierto OpenEnergyMonitor —desarrollado principalmente por Trystan Lea y Glyn Hudson desde 2012— constituye el antecedente más significativo en el ámbito del hardware libre para monitoreo de energía. Su plataforma emonTx, basada en el microcontrolador ATmega328P (Arduino), implementó la medición no intrusiva mediante sensores SCT-013 y la biblioteca de cálculos energéticos `EmonLib`. No obstante, el costo de importación de sus módulos ($> 2,000$ MXN para el kit básico) y la ausencia de conectividad WiFi nativa (requiere módulos adicionales) limitan su accesibilidad en el mercado mexicano. El presente proyecto adopta la fundamentación matemática de `EmonLib` pero la migra a la plataforma ESP32, que integra WiFi de manera nativa y presenta un costo significativamente inferior.

### 5.2 Bases teóricas

#### 5.2.1 Electromagnetismo y principios de medición

El funcionamiento del sensor de corriente SCT-013 se fundamenta en la **Ley de Faraday de la Inducción Electromagnética**, la cual establece que la fuerza electromotriz (fem) inducida en un circuito cerrado es directamente proporcional a la tasa de variación temporal del flujo magnético que lo atraviesa:

$$\varepsilon = -\frac{d\Phi_B}{dt}$$

En un transformador de corriente de núcleo partido, el conductor primario (cable de la instalación eléctrica) genera un campo magnético proporcional a la corriente que lo recorre. El núcleo ferromagnético del sensor concentra este flujo y lo enlaza con la bobina secundaria, induciendo una corriente proporcional que puede ser medida de manera segura, sin contacto galvánico con el conductor de alta tensión (Hart, 2011).

Para sistemas de corriente alterna (CA), la magnitud relevante para el cálculo de consumo energético es la **corriente eficaz** ($I_{RMS}$), definida como el valor equivalente de corriente continua que produce la misma disipación de potencia en una resistencia:

$$I_{RMS} = \sqrt{\frac{1}{T} \int_{0}^{T} i(t)^2 \, dt}$$

De manera análoga, el voltaje eficaz se expresa como:

$$V_{RMS} = \sqrt{\frac{1}{T} \int_{0}^{T} v(t)^2 \, dt}$$

La **potencia eléctrica en corriente alterna** se descompone en tres componentes fundamentales, representadas en el triángulo de potencias:

- **Potencia Aparente** ($S$): $S = V_{RMS} \cdot I_{RMS}$ [VA]
- **Potencia Activa** ($P$): $P = V_{RMS} \cdot I_{RMS} \cdot \cos(\phi)$ [W]
- **Potencia Reactiva** ($Q$): $Q = V_{RMS} \cdot I_{RMS} \cdot \sin(\phi)$ [VAR]

Donde $\phi$ es el ángulo de desfase entre las formas de onda de voltaje y corriente, y $\cos(\phi)$ corresponde al factor de potencia. La potencia activa es la que efectivamente se transforma en trabajo útil (calor, luz, movimiento) y es la magnitud que la CFE factura al usuario residencial. Por esta razón, el cálculo de $P$ constituye el objetivo primario de medición del prototipo.

#### 5.2.2 Teoría de muestreo y procesamiento digital de señales

La transición de las magnitudes eléctricas analógicas al dominio digital se rige por el **teorema de Nyquist-Shannon**, el cual establece que para reconstruir fielmente una señal analógica a partir de sus muestras discretas, la frecuencia de muestreo ($f_s$) debe ser al menos el doble de la frecuencia máxima presente en la señal ($f_{max}$):

$$f_s \geq 2 \cdot f_{max}$$

Para la señal fundamental de la red eléctrica mexicana a 60 Hz, la condición mínima teórica es $f_s \geq 120$ Hz. Sin embargo, en la práctica se emplean frecuencias de muestreo significativamente superiores —del orden de 1 kHz a 5 kHz— con el doble propósito de capturar componentes armónicos de la señal y mejorar la resolución numérica del cálculo de valor eficaz (Oppenheim y Willsky, 2014).

En el dominio digital discretizado, las ecuaciones de valor eficaz se aproximan mediante sumatorias finitas. La corriente eficaz se calcula como:

$$I_{RMS} \approx \sqrt{\frac{1}{N} \sum_{n=0}^{N-1} i[n]^2}$$

Y la potencia activa real resulta del promedio del producto punto a punto de las muestras instantáneas de voltaje y corriente:

$$P = \frac{1}{N} \sum_{n=0}^{N-1} \left( v[n] \times i[n] \right)$$

Donde $N$ es el número total de muestras adquiridas en el periodo de cálculo, $i[n]$ es el valor instantáneo de corriente en la muestra $n$-ésima, y $v[n]$ es el valor instantáneo de voltaje correspondiente. Este método de cálculo incorpora implícitamente el efecto del factor de potencia, ya que el producto instantáneo $v[n] \cdot i[n]$ refleja el desfase real entre ambas señales, eliminando la necesidad de asumir un factor de potencia unitario o un voltaje nominal constante.

La resolución del convertidor analógico-digital (ADC) determina la granularidad de la discretización. El ESP32 incorpora un ADC de 12 bits, lo que proporciona $2^{12} = 4096$ niveles de cuantización sobre el rango de entrada de 0 V a 3.3 V. Esto implica una resolución teórica de $\frac{3.3}{4096} \approx 0.8$ mV por nivel. El ruido de cuantización inherente a esta resolución limita la capacidad de medición de corrientes muy bajas, donde la señal del sensor se aproxima al piso de ruido del convertidor (Espressif Systems, 2022).

#### 5.2.3 Sistemas embebidos

El ESP32 es un System-on-Chip (SoC) desarrollado por Espressif Systems que integra una arquitectura de doble núcleo Xtensa® LX6 de 32 bits, operando a frecuencias de reloj de hasta 240 MHz. Esta configuración de doble núcleo es determinante para el presente proyecto, ya que permite la asignación dedicada de tareas: un núcleo se destina a la adquisición continua de datos del ADC y al cálculo de magnitudes eléctricas, mientras que el segundo núcleo gestiona de manera concurrente la pila de protocolos TCP/IP para la comunicación WiFi (Espressif Systems, 2022).

El SoC integra los siguientes periféricos relevantes para el sistema:

- **Dos bloques de ADC** (ADC1 y ADC2) con resolución de 12 bits y hasta 18 canales. Sin embargo, el bloque ADC2 presenta una restricción documentada por el fabricante: no puede operar simultáneamente con el módulo WiFi. Esta restricción obliga a utilizar exclusivamente los pines del bloque ADC1 (GPIO 32-39) para la conexión de los sensores de corriente y voltaje.
- **Módulo WiFi 802.11 b/g/n** en la banda de 2.4 GHz con pila TCP/IP completa.
- **Interfaces de comunicación:** SPI (para la tarjeta microSD), I2C (para la pantalla OLED), UART (para depuración por puerto serial).
- **FreeRTOS integrado:** Sistema operativo de tiempo real que gestiona la planificación de tareas concurrentes entre ambos núcleos.

#### 5.2.4 Internet de las cosas (IoT) y protocolos de comunicación

La arquitectura del sistema se enmarca dentro del modelo de capas del IoT:

- **Capa de percepción:** Constituida por los sensores SCT-013 y ZMPT101B, encargados de la transducción de magnitudes eléctricas a señales analógicas procesables.
- **Capa de red:** Implementada mediante el módulo WiFi del ESP32 y los protocolos HTTP o MQTT (*Message Queuing Telemetry Transport*). MQTT es particularmente adecuado para dispositivos IoT con limitaciones de ancho de banda y potencia de cómputo, al emplear un modelo de publicación/suscripción con baja sobrecarga de protocolo (OASIS, 2019).
- **Capa de aplicación:** Representada por la interfaz de visualización —pantalla OLED para el acceso local y plataforma web para el acceso remoto— que transforma los datos crudos en información accionable para el usuario.

#### 5.2.5 Fuentes de alimentación conmutadas (SMPS)

La fuente de alimentación del sistema emplea un módulo de conversión AC-DC del tipo convertidor *buck* de alta frecuencia. A diferencia de las fuentes lineales —que regulan el voltaje mediante la disipación del excedente en un transistor de paso—, las fuentes conmutadas regulan mediante la modulación del ciclo de trabajo (*duty cycle*) de un interruptor semiconductor operando a frecuencias de decenas o centenas de kilohertz, seguido de un filtro LC de salida. Este principio confiere ventajas significativas en eficiencia energética (típicamente $> 70\%$), compacidad volumétrica y disipación térmica reducida (Hart, 2011).

Para el presente proyecto, se seleccionó un módulo tipo Hi-Link HLK-PM01 (o equivalente genérico) con entrada universal de 90-240 V AC y salida regulada de 5 V DC / 700 mA. Esta fuente se integra directamente en el circuito del dispositivo, alimentándose de la red doméstica mediante un cable con clavija estándar NEMA 5-15P, eliminando la necesidad de adaptadores externos y contribuyendo a la compacidad y profesionalización del acabado final.

### 5.3 Estado del arte

El estado actual de las soluciones de monitoreo eléctrico residencial puede clasificarse en tres categorías: soluciones comerciales de mercado, plataformas académicas de código abierto y medidores fiscales institucionales. La siguiente tabla comparativa resume las características principales de las alternativas existentes frente al prototipo propuesto en este proyecto:

| Criterio | Prototipo propuesto | Emporia Vue (comercial) | Shelly EM (comercial) | OpenEnergyMonitor emonTx (open source) | Medidor CFE (fiscal) |
|---|---|---|---|---|---|
| **Costo aproximado (MXN)** | ~$600 | >$1,800 | >$1,500 | >$2,000 (importado) | N/A (propiedad CFE) |
| **Medición de voltaje real** | Sí (ZMPT101B) | Sí | Sí | Sí | Sí |
| **Tipo de instalación** | No intrusiva (clamp) | Semi-intrusiva | Semi-intrusiva | No intrusiva (clamp) | Intrusiva (fiscal) |
| **Conectividad** | WiFi 2.4 GHz | WiFi | WiFi | RF (requiere módulo WiFi adicional) | Sin conectividad al usuario |
| **Almacenamiento local** | Sí (microSD) | No | No | Sí (tarjeta SD) | No |
| **Datos en tiempo real al usuario** | Sí | Sí | Sí | Sí | No |
| **Arquitectura** | Abierta (ESP32) | Propietaria | Propietaria | Abierta (ATmega328P) | Propietaria |
| **Disponibilidad en México** | Componentes nacionales | Importación | Importación | Importación | Solo CFE |

El análisis comparativo evidencia que las soluciones comerciales, si bien ofrecen mayor refinamiento industrial, presentan barreras de costo e importación que limitan su penetración en el mercado residencial mexicano. La plataforma OpenEnergyMonitor comparte la filosofía de hardware abierto; sin embargo, su dependencia de componentes importados y la ausencia de conectividad WiFi nativa en el ATmega328P incrementan su costo y complejidad. El prototipo propuesto ocupa un nicho diferenciado al combinar: (a) un costo de materiales inferior a $600 MXN con componentes disponibles en el mercado nacional, (b) medición de potencia activa real mediante sensado simultáneo de voltaje y corriente, (c) conectividad WiFi integrada de manera nativa, y (d) almacenamiento local para operación híbrida ante interrupciones de red.

### 5.4 Marco conceptual

A continuación se definen los términos técnicos clave empleados a lo largo de este documento:

| Término | Definición |
|---|---|
| **IoT (*Internet of Things*)** | Paradigma tecnológico que integra objetos físicos con sensores, capacidad de procesamiento y conectividad de red para la recolección e intercambio de datos (Ashton, 2009). |
| **NILM (*Non-Intrusive Load Monitoring*)** | Conjunto de técnicas para monitorear el consumo eléctrico sin alterar físicamente la instalación, mediante la medición indirecta de variables en un solo punto de la acometida (Hart, 1992). |
| **SCT-013** | Sensor de corriente tipo transformador de corriente de núcleo partido (*split-core current transformer*), que permite su instalación alrededor de un conductor sin necesidad de desconectarlo. |
| **ZMPT101B** | Módulo de sensado de voltaje AC basado en un transformador de tensión con aislamiento galvánico, que proporciona una señal de voltaje reducida y segura para su lectura por un ADC. |
| **ADC (*Analog-to-Digital Converter*)** | Periférico que convierte señales analógicas continuas en valores digitales discretos, cuantificados en niveles determinados por la resolución en bits del convertidor. |
| **$I_{RMS}$ (corriente eficaz)** | Valor de corriente continua equivalente que disipa la misma potencia promedio sobre una carga resistiva que la señal de corriente alterna original. |
| **$P$ (potencia activa)** | Componente de la potencia eléctrica que efectivamente se convierte en trabajo útil; es la magnitud facturada por la empresa suministradora. Se mide en watts (W). |
| **Factor de potencia ($\cos\phi$)** | Relación entre la potencia activa ($P$) y la potencia aparente ($S$); cuantifica la eficiencia con que la energía eléctrica se convierte en trabajo útil. |
| **SMPS (*Switched-Mode Power Supply*)** | Fuente de alimentación que regula el voltaje de salida mediante la conmutación de alta frecuencia de un transistor semiconductor, ofreciendo alta eficiencia y compacidad. |
| **Tarifa DAC** | Tarifa Doméstica de Alto Consumo aplicada por la CFE cuando el consumo mensual del usuario supera el límite subsidiado. |
| **MQTT** | Protocolo de mensajería ligero basado en el modelo publicación/suscripción, diseñado para la transmisión eficiente de datos en dispositivos IoT con recursos limitados (OASIS, 2019). |
| **BOM (*Bill of Materials*)** | Lista completa y detallada de los componentes necesarios para la fabricación de un producto, incluyendo cantidades, especificaciones técnicas y costos. |
| **FreeRTOS** | Sistema operativo de tiempo real de código abierto diseñado para microcontroladores, integrado nativamente en el ESP32 para la gestión de tareas concurrentes. |

### 5.5 Marco legal y normativo

El desarrollo de un dispositivo electrónico que interactúa con la instalación eléctrica residencial debe enmarcarse dentro del contexto regulatorio aplicable. A continuación se identifican las normas y disposiciones legales relevantes:

| Norma / Disposición | Ámbito | Aplicación en el proyecto |
|---|---|---|
| **NOM-001-SEDE-2012** | Instalaciones eléctricas de utilización | Establece requisitos de seguridad para instalaciones eléctricas en México. El diseño del prototipo respeta los lineamientos de no intervención en circuitos fijos al emplear un sensor de corriente tipo *clamp* que no requiere contacto galvánico con el conductor. |
| **NOM-003-SCFI-2014** | Seguridad de productos eléctricos | Define requisitos de seguridad para aparatos eléctricos de uso doméstico; aplicable en caso de comercialización futura. |
| **IEC 62053-21** | Medidores estáticos de energía activa | Referencia metrológica para evaluar el nivel de precisión; el prototipo no es un medidor fiscal. |
| **Ley de la Industria Eléctrica** | Regulación del sector eléctrico mexicano | Delimita atribuciones de CFE y derechos del usuario; el prototipo es informativo y no sustituye el medidor fiscal. |
| **LFPDPPP** | Protección de datos personales | Aplica si se transmiten datos de consumo vinculados a un domicilio identificable. |

Es pertinente establecer con claridad que el dispositivo desarrollado en este proyecto **no constituye un medidor fiscal ni un instrumento de facturación**. Su clasificación corresponde a un **instrumento informativo y educativo** diseñado para proporcionar al usuario herramientas de autodiagnóstico energético. En consecuencia, sus mediciones no tienen valor probatorio legal ante la empresa suministradora ni ante instancias reguladoras.

---

## 6 Hipótesis

### 6.1 Hipótesis general

$H_i$: Es factible desarrollar un sistema de monitoreo eléctrico residencial basado en IoT que reduzca costos por debajo de $600.00 MXN por unidad, manteniendo error de potencia activa inferior al 5% en cargas superiores a 25 W.

### 6.2 Hipótesis nula

$H_0$: El sistema no alcanza precisión (error > 5%) o excede $600.00 MXN por unidad.

### 6.3 Hipótesis específicas

1. Linealidad del SCT-013-030 con $R^2 > 0.98$ en 0.5–30 A.
2. Estabilidad de la fuente con rizado < 50 mVpp.
3. Cálculo de potencia activa con mayor precisión por medición simultánea de voltaje y corriente.
4. BOM ≤ $600.00 MXN y reducción ≥ 60% respecto a alternativas comerciales.

---

## 7 Diseño metodológico

### 7.1 Universo

En investigaciones experimentales de ingeniería con prototipos, el universo (población) se define como el conjunto de **condiciones de medición** posibles.

**Universo (población):** conjunto de todas las posibles condiciones de carga eléctrica que pueden presentarse en una vivienda monofásica residencial dentro del rango operativo del sensor (0 a 30 A).

### 7.2 Tamaño de la muestra

En el contexto de este estudio, la muestra corresponde al conjunto de mediciones realizadas en niveles discretos de carga seleccionados intencionalmente para cubrir el rango operativo.

| Concepto | Definición en el contexto del proyecto |
|---|---|
| **Muestra** | Conjunto de $n$ mediciones realizadas en niveles discretos de carga: 0.5 A, 1 A, 2 A, 5 A, 10 A, 15 A, 20 A, 25 A y 30 A. Se establece un mínimo de 30 repeticiones por nivel, resultando en al menos 270 pares de observaciones (prototipo vs. patrón). |
| **Tipo de muestreo** | No probabilístico intencional. Los niveles de carga se seleccionan deliberadamente para garantizar la cobertura del rango operativo completo del sensor. |
| **Criterios de inclusión** | Cargas resistivas puras (lámparas incandescentes, resistencias de potencia) y cargas inductivas comunes (motores fraccionarios, ventiladores), conectadas a circuito monofásico de 127 V / 60 Hz. |
| **Criterios de exclusión** | Cargas trifásicas; cargas con corriente inferior a 0.2 A (zona muerta del ADC); equipos con distorsión armónica extrema (soldadoras de arco, variadores de frecuencia industriales). |

### 7.3 Tipos de investigación a realizar

La presente investigación se clasifica metodológicamente de acuerdo con los siguientes criterios:

| Criterio de clasificación | Categoría | Justificación |
|---|---|---|
| **Por su finalidad** | Investigación aplicada y tecnológica | Aplica conocimientos consolidados (Ley de Faraday, Nyquist-Shannon, protocolos TCP/IP) para resolver una problemática práctica mediante un prototipo tecnológico tangible. |
| **Por el enfoque de datos** | Cuantitativa | La validación metrológica depende de variables numéricas medibles: $I_{RMS}$, $V_{RMS}$, $P$, $E_{\%}$, MAPE, $R^2$ y costo. La encuesta (apartado 7.5) se considera complementaria y de análisis descriptivo, sin afectar el enfoque principal. |
| **Por su alcance** | Correlacional y explicativa | **Correlacional:** relación estadística entre prototipo y patrón (esperado $r \approx 1$). **Explicativa:** causas de desviaciones (ruido del ADC, resolución del sensor, cargas no lineales). |
| **Por el lugar de realización** | Mixta (laboratorio y campo) | **Laboratorio:** calibración/ajuste con cargas conocidas. **Campo:** instalación en una vivienda residencial real en Tenango del Valle, con variables no controladas (fluctuaciones de red, armónicos, temperatura). |
| **Por la manipulación de variables** | Experimental | Se manipula la carga conectada para observar la respuesta del sistema y su precisión respecto al patrón. |

En síntesis, el estudio se define como de tipo aplicada y tecnológica, con enfoque cuantitativo, alcance correlacional-experimental y diseño mixto (laboratorio y campo).

La operacionalización de variables se presenta en el **Anexo A**.

### 7.4 Tipo de instrumento a utilizar para la recolección de la información

La recolección de datos se realiza mediante la combinación de los siguientes instrumentos:

| Instrumento | Función | Especificaciones relevantes |
|---|---|---|
| **Prototipo SME-IoT** (ESP32 + SCT-013 + ZMPT101B) | Dispositivo bajo prueba (DUT) | ADC de 12 bits; rango 0-30 A; muestreo ~1 kHz; pines del bloque ADC1 (GPIO 32-39). |
| **Multímetro TRMS de referencia** | Instrumento patrón para comparación | Precisión $\pm 0.5\%$, medición True RMS, calibrado. |
| **Cargas conocidas** | Condiciones experimentales controladas | Resistivas (60 W, 100 W, 200 W) e inductivas comunes. |
| **Módulo microSD** | Almacenamiento local | Registro con marca temporal (*timestamp*); capacidad 4 GB (\> 5 años a intervalos de 1 minuto). |
| **Monitor serial (UART)** | Depuración y captura en tiempo real | Exportación a CSV para procesamiento externo. |

Técnicas de recolección empleadas:

1. Observación directa estructurada (registro simultáneo prototipo y patrón).
2. Registro automatizado en microSD.
3. Barrido de carga escalonado con puntos predefinidos.

### 7.5 Encuesta

Este apartado se incorpora para cumplir con el formato institucional. Se plantea como instrumento complementario.

| Elemento | Definición |
|---|---|
| Objetivo de la encuesta | ____________________________________________ |
| Población objetivo | ____________________________________________ |
| Tamaño de muestra (encuesta) | ____________________________________________ |
| Tipo de escala | ____________________________________________ |
| Momento de aplicación | ____________________________________________ |

**Banco de preguntas:**

____________________________________________

### 7.6 Procedimiento experimental

El protocolo experimental se organiza en cuatro fases secuenciales:

#### Fase 1 Calibración en laboratorio (condiciones controladas)

1. Energizar el prototipo y esperar un periodo de estabilización térmica no inferior a 5 minutos.
2. Conectar una carga resistiva pura de valor conocido al circuito de prueba.
3. Registrar simultáneamente la lectura del prototipo ($I_{RMS}$, $V_{RMS}$, $P$) y la lectura del multímetro patrón.
4. Repetir la medición 30 veces para el nivel de carga seleccionado.
5. Incrementar la carga al siguiente nivel predefinido y repetir los pasos 2-4.
6. Calcular los factores de corrección de calibración (pendiente $m$ y ordenada al origen $b$ de la recta de regresión $y = mx + b$) y aplicarlos al firmware.

#### Fase 2 Validación con cargas mixtas (laboratorio)

7. Sustituir las cargas resistivas por cargas inductivas (motores fraccionarios) y cargas no lineales (fuentes conmutadas de electrodomésticos).
8. Registrar mediciones de potencia activa y compararlas con el instrumento patrón.
9. Evaluar cuantitativamente el impacto del factor de potencia ($\cos\phi < 1$) en la precisión de la medición.

#### Fase 3 Pruebas de campo (vivienda residencial)

10. Instalar el prototipo en una caja plástica adyacente al tablero de distribución de una vivienda monofásica residencial en Tenango del Valle, con el sensor SCT-013 colocado en el conductor de fase de la acometida principal.
11. Conectar el dispositivo a un tomacorriente convencional cercano mediante cable con clavija estándar NEMA 5-15P.
12. Monitorizar el consumo de manera continua durante un periodo mínimo de 24 a 72 horas.
13. Comparar el consumo acumulado ($kWh$) registrado por el prototipo contra la lectura del medidor de CFE.
14. Documentar las condiciones ambientales: temperatura, distancia al router WiFi, eventos de interrupción de red.

#### Fase 4 Análisis de robustez

15. Provocar deliberadamente condiciones adversas: tapa metálica del tablero cerrada (atenuación WiFi), arranque de cargas de alto transitorio (compresor de refrigerador), simulación de corte de energía.
16. Verificar la integridad de los datos en la tarjeta microSD y la reconexión automática del módulo WiFi.
17. Registrar el comportamiento del sistema ante cada escenario y documentar las respuestas observadas.

### 7.7 Técnicas de procesamiento y análisis de datos

Los datos recolectados se procesarán mediante las siguientes herramientas y técnicas estadísticas.

**Herramientas de software:**

- Python 3.x con NumPy, Pandas, Matplotlib y SciPy para análisis estadístico y gráficos.
- Microsoft Excel como herramienta complementaria para organización tabular de datos.

| Técnica | Propósito | Métrica esperada |
|---|---|---|
| **Estadística descriptiva** | Resumir cada serie de mediciones | Media ($\bar{x}$), desviación estándar ($\sigma$), rango, coeficiente de variación ($CV$). |
| **Error porcentual absoluto medio (MAPE)** | Cuantificar diferencia global prototipo vs. patrón | $MAPE = \frac{1}{n} \sum_{i=1}^{n} \left\| \frac{Patrón_i - Prototipo_i}{Patrón_i} \right\| \times 100$. Criterio: $MAPE < 5\%$. |
| **Pearson ($r$)** | Fuerza de relación lineal | Se espera $r > 0.99$. |
| **Coeficiente de determinación ($R^2$)** | Varianza explicada por el modelo lineal | Se espera $R^2 > 0.98$. |
| **Regresión lineal** | Ecuación de calibración | $y = mx + b$. Ideal: $m \approx 1$, $b \approx 0$. |
| **t de Student pareada** | Diferencias significativas entre métodos | $H_0$: $\bar{d} = 0$. |
| **Bland–Altman** | Concordancia entre métodos | Diferencias vs. promedios; límites $\pm 1.96\sigma$. |

---

## 8 Cronograma

| Fase | Actividad | Inicio | Fin |
|---|---|---:|---:|
| F1 | Investigación de antecedentes y estructuración del planteamiento técnico. | 02-Feb-2026 | 13-Feb-2026 |
| F2 | Definición de objetivos y delimitación del impacto del proyecto. | 16-Feb-2026 | 06-Mar-2026 |
| F3 | Integración del marco teórico y revisión del estado del arte. | 09-Mar-2026 | 20-Mar-2026 |
| F4 | Formulación de hipótesis y definición de variables. | 23-Mar-2026 | 03-Abr-2026 |
| F5 | Diseño metodológico y preparación del protocolo experimental. | 06-Abr-2026 | 24-Abr-2026 |
| F6 | Consolidación del documento final, presupuesto y referencias. | 27-Abr-2026 | 29-May-2026 |

---

## 9 Presupuesto y financiamiento

### 9.1 Presupuesto (BOM)

| Componente | Descripción técnica | Costo unitario (MXN) |
|---|---|---:|
| Microcontrolador | ESP32 DevKit V1 (clónico/genérico) | $130.00 |
| Sensor de corriente | SCT-013-030 (30 A, salida 1 V, núcleo partido) | $185.00 |
| Sensor de voltaje | Módulo ZMPT101B | $50.00 |
| Fuente de alimentación | Módulo AC-DC 220 V a 5 V 700 mA (tipo Hi-Link HLK-PM01) | $75.00 |
| Pantalla | OLED 0.96" I2C (SSD1306) | $65.00 |
| Componentes y módulos auxiliares | PCB/borneras/conectores/resistencias/capacitores/jack 3.5 mm (incluye microSD si aplica) | $45.00 |
| Gabinete | Caja plástica estándar o impresión 3D | $50.00 |
| **Total** | **Costo directo de hardware por unidad** | **$600.00** |

### 9.2 Financiamiento

- Fuente de financiamiento: ____________________________________________

---

## 10 Diseño e implementación del sistema

### 10.1 Arquitectura general del sistema

El sistema SME-IoT (*Sistema de Monitoreo Eléctrico - Internet of Things*) se estructura en cuatro capas funcionales siguiendo el modelo de arquitectura IoT:

**Capa 1 Percepción (sensado):**

- Sensor de corriente SCT-013-030 (30 A / 1 V, núcleo partido).
- Sensor de voltaje ZMPT101B (transformador de tensión con aislamiento galvánico).
- Circuitos de acondicionamiento de señal: divisores de tensión para generación de *offset* DC a 1.65 V, capacitores de desacoplo para filtrado de alta frecuencia.

**Capa 2 Procesamiento (edge computing):**

- Microcontrolador ESP32 DevKit V1.
    - Núcleo 0: gestión de la pila TCP/IP (WiFi), protocolo MQTT/HTTP, interfaz OLED.
    - Núcleo 1: adquisición de datos del ADC, cálculo de $I_{RMS}$, $V_{RMS}$ y $P$, escritura en microSD.

**Capa 3 Red (comunicación):**

- WiFi 802.11 b/g/n (2.4 GHz).
- Protocolo de transporte: TCP/IP.
- Protocolo de aplicación: MQTT (publicación de métricas) o HTTP (peticiones REST a servidor).

**Capa 4 Aplicación (interfaz de usuario):**

- **Local:** pantalla OLED 0.96" (SSD1306, I2C) para visualización *in-situ* de corriente, voltaje, potencia y consumo acumulado.
- **Remota:** plataforma web o aplicación móvil para consulta de métricas en tiempo real y series históricas.
- **Almacenamiento:** tarjeta microSD para registro local con marca temporal, garantizando continuidad de datos ante interrupciones de conectividad.

### 10.2 Diseño del hardware

#### 10.2.1 Unidad de procesamiento

Se seleccionó el SoC ESP32 (Espressif Systems) en su variante DevKit V1 (clónico/genérico) como unidad central de procesamiento. La arquitectura de doble núcleo Xtensa® LX6 operando a 240 MHz permite la ejecución concurrente de tareas de adquisición de datos y comunicación inalámbrica. El ADC utilizado corresponde exclusivamente al bloque ADC1 (GPIOs 32-39), dado que el bloque ADC2 no puede operar simultáneamente con el módulo WiFi activo.

#### 10.2.2 Etapa de sensado de corriente

El sensor de corriente seleccionado es el **SCT-013-030** (30 A / salida 1 V AC), un transformador de corriente de núcleo partido que opera bajo el principio de inducción electromagnética. Su diseño tipo *clamp* permite instalarlo alrededor del conductor de fase sin necesidad de desconectarlo.

Dado que la señal de salida es alterna (bipolar) y el ADC del ESP32 opera en un rango unipolar de 0 V a 3.3 V, se implementó un circuito de **offset de voltaje** mediante un divisor resistivo (dos resistencias de igual valor) que centra la señal en un punto medio de 1.65 V (*virtual ground*). Se integraron capacitores de desacoplo para estabilizar el punto de referencia y filtrar ruido de alta frecuencia.

#### 10.2.3 Etapa de sensado de voltaje

Se incorporó el módulo **ZMPT101B**, un sensor de voltaje AC basado en un transformador de tensión con aislamiento galvánico. Este componente reduce el voltaje de red (127 V AC nominal) a una señal segura para el ADC, manteniendo la proporcionalidad con la forma de onda original. La señal de salida se acondiciona con el mismo esquema de *offset* a 1.65 V empleado para el sensor de corriente.

La integración de este sensor permite:

- Calcular potencia activa real ($P$) mediante el producto instantáneo $v[n] \cdot i[n]$.
- Detectar fluctuaciones de voltaje (picos y caídas de tensión) como dato de calidad de energía.
- Eliminar el error introducido al asumir un voltaje nominal constante.

#### 10.2.4 Sistema de alimentación integrado

El sistema de alimentación emplea un módulo de fuente conmutada AC-DC (tipo Hi-Link HLK-PM01 o equivalente genérico): entrada 90-240 V AC y salida 5 V DC / 700 mA, con eficiencia típica superior al 70%.

El módulo se conecta a la red doméstica mediante cable con clavija estándar NEMA 5-15P a un tomacorriente cercano al tablero. La línea de 5 V se regula a 3.3 V mediante el regulador integrado en la placa de desarrollo ESP32.

#### 10.2.5 Interfaz de usuario local y almacenamiento

- **Pantalla OLED 0.96"** (SSD1306, I2C): visualización local de corriente, voltaje, potencia, consumo acumulado y costo estimado.
- **Módulo lector microSD** (SPI): almacenamiento local con *timestamp*. Una tarjeta de 4 GB permite almacenar más de 5 años de datos a intervalos de 1 minuto.

### 10.3 Diseño del firmware

El firmware se desarrolla en C++ sobre Arduino-ESP32, aprovechando FreeRTOS para gestionar concurrencia.

#### 10.3.1 Distribución de tareas

| Núcleo | Tarea | Prioridad | Descripción |
|---|---|---|---|
| **Núcleo 1 (APP)** | Adquisición y cálculo | Alta | Lectura periódica del ADC (corriente y voltaje a ~1 kHz), cálculo de $I_{RMS}$, $V_{RMS}$ y $P$ por periodo, escritura a buffer. |
| **Núcleo 0 (PRO)** | Comunicación e interfaz | Media | Gestión WiFi, publicación MQTT/HTTP, actualización OLED, escritura periódica en microSD. |

#### 10.3.2 Algoritmo de medición

1. Corrección de linealidad del ADC (tabla/polinomio de compensación).
2. Eliminación del *offset* DC (1.65 V) para recuperar componente AC.
3. Filtrado digital (media móvil) para reducir ruido.
4. Cálculo de $I_{RMS}$ y $V_{RMS}$ acumulando cuadrados durante un número fijo de ciclos.
5. Cálculo de potencia activa acumulando $v[n] \cdot i[n]$ y promediando.
6. Estimación de consumo ($kWh$) y costo (según tarifa vigente).

#### 10.3.3 Bibliotecas utilizadas

| Biblioteca | Función |
|---|---|
| `EmonLib` | Base para cálculos de energía ($I_{RMS}$, potencia aparente) y extensiones para potencia activa. |
| `WiFi.h` | Conexión WiFi del ESP32. |
| `PubSubClient` | Cliente MQTT. |
| `Adafruit_SSD1306` | Control OLED (I2C). |
| `SD.h` / `SPI.h` | Lectura/escritura en microSD. |
| `driver/adc.h` | Configuración avanzada del ADC. |

**Nota:** el análisis de costos (BOM) se detalla en el apartado 9.1.

---

## 11 Análisis de riesgos y limitaciones técnicas

El análisis riguroso de los riesgos técnicos y las limitaciones inherentes al diseño es indispensable para definir correctamente el alcance del proyecto y prevenir fallas durante la fase de implementación. A continuación se documentan los desafíos identificados junto con las estrategias de mitigación adoptadas.

### 11.1 Limitaciones del microcontrolador

#### 11.1.1 No linealidad del ADC

Los convertidores analógico-digitales del ESP32 presentan una característica de transferencia no perfectamente lineal, con desviaciones significativas en los extremos del rango (próximos a 0 V y a 3.3 V). Adicionalmente, el piso de ruido del ADC del ESP32 es superior al de microcontroladores AVR, lo que incrementa la incertidumbre en la medición de señales de baja amplitud (Espressif Systems, 2022).

**Impacto:** lecturas de corrientes muy bajas (modo *standby* o cargadores) pueden resultar imprecisas o registrarse como cero.

**Mitigación:** se establece una **zona muerta** formal: el dispositivo no garantiza precisión para corrientes inferiores a 0.2 A (≈ 25 W). Se aplica corrección de linealidad (tabla/polinomio) en firmware.

#### 11.1.2 Conflicto de operación ADC2 WiFi

El ESP32 integra dos bloques ADC; el fabricante documenta que **ADC2 no puede utilizarse cuando WiFi está activo**.

**Impacto:** si sensores se conectan a pines de ADC2 (GPIO 0, 2, 4, 12-15, 25-27), la adquisición puede cesar durante transmisión WiFi.

**Mitigación:** el diseño usa **exclusivamente pines de ADC1** (GPIO 32-39) para sensores de corriente y voltaje.

### 11.2 Limitaciones de instalación física

#### 11.2.1 Efecto de jaula de Faraday del tablero eléctrico

Los centros de carga residenciales suelen ser cajas metálicas empotradas que atenúan señales de radiofrecuencia en 2.4 GHz.

**Impacto:** instalar el dispositivo dentro del tablero con tapa cerrada puede provocar pérdida total o intermitente de conectividad WiFi.

**Mitigación:** instalar la unidad de procesamiento en una **caja plástica externa** adyacente al tablero. El SCT-013 se mantiene dentro del tablero, conectado por su cable.

#### 11.2.2 Definición operativa de no intrusivo

El carácter "no intrusivo" se refiere a que **no se cortan ni se empalman cables de la instalación fija** para medir corriente (sensor tipo *clamp*). No obstante, el sistema requiere:

- Tomacorriente cercano para alimentación (NEMA 5-15P).
- Referencia de línea y neutro para el sensado de voltaje (ZMPT101B).

### 11.3 Limitaciones del sistema eléctrico mexicano

#### 11.3.1 Restricción a servicio monofásico

El diseño integra un único sensor de corriente y un único sensor de voltaje.

**Alcance declarado:** el proyecto se restringe a **viviendas con servicio monofásico** (1 fase + neutro, 127 V / 60 Hz). En acometida bifásica, registraría solo una fase.

#### 11.3.2 Ruido y distorsión armónica en la red

La red pública puede presentar fluctuaciones y deformación de onda. El sensor ZMPT101B tiene ancho de banda limitado.

**Alcance de medición:** el dispositivo detecta variaciones de amplitud (voltaje RMS) y distorsión armónica básica. No está diseñado para EMI de alta frecuencia ni transitorios de microsegundos, por limitaciones de muestreo y del sensor.

### 11.4 Limitaciones de continuidad de datos

#### 11.4.1 Dependencia de la red WiFi

La conectividad WiFi doméstica puede interrumpirse por reinicio del router, cortes del servicio o interferencias.

**Mitigación implementada:** operación **híbrida**:

- Con WiFi: transmisión en tiempo real (MQTT/HTTP).
- Sin WiFi: almacenamiento automático en microSD con *timestamp*.

Una microSD de 4 GB es suficiente para más de 5 años de registros a intervalos de 1 minuto.

---

## 12 Resultados preliminares y discusión

### 12.1 Pruebas de linealidad

Se realizaron pruebas comparativas de linealidad utilizando un multímetro de banco calibrado como instrumento de referencia y el prototipo SME-IoT como dispositivo bajo prueba. El sistema se sometió a cargas resistivas puras (lámparas incandescentes de potencias variadas) y cargas inductivas (motores fraccionarios y ventiladores) en un rango de corriente de 0.5 A a 15 A.

Los resultados preliminares indican que la relación entre la lectura del prototipo y la lectura del instrumento patrón presenta una **desviación lineal constante** (*offset*) corregible mediante el ajuste del factor de calibración en firmware. El **coeficiente de determinación** ($R^2$) obtenido en regresión lineal es **superior a 0.98**, lo que valida la proporcionalidad de la respuesta del sensor SCT-013 en el rango medio de operación.

*Nota: Los gráficos de dispersión (Valor Medido vs. Valor Real) y las tablas completas de datos se incluirán en el documento final de resultados.*

### 12.2 Análisis de error

El error porcentual absoluto medio (MAPE) registrado durante las pruebas preliminares presenta el siguiente comportamiento según el nivel de carga:

| Rango de carga | MAPE registrado | Observación |
|---|---:|---|
| Cargas $> 200$ W | $\pm 2.3\%$ | Dentro del criterio de aceptación ($< 5\%$). |
| Cargas entre 50 W y 200 W | $\pm 4.1\%$ | Dentro del criterio de aceptación. |
| Cargas $< 50$ W (*standby*) | $\pm 8.5\%$ | Fuera del criterio para medición individual. |

El incremento del error en cargas de baja potencia se atribuye principalmente a:

1. **Ruido de cuantización del ADC:** la amplitud de señal en corrientes muy bajas se aproxima al piso de ruido del convertidor (12 bits).
2. **Baja utilización del rango del sensor:** el SCT-013-030 opera en menos del 2% de su escala completa cuando se miden corrientes del orden de 0.3–0.4 A.

Para fines de estimación de consumo acumulado ($kWh$) en periodos de horas o días, el error en cargas bajas se diluye estadísticamente al promediar con periodos de mayor consumo, manteniendo utilidad práctica como herramienta informativa no fiscal.

### 12.3 Viabilidad económica

El costo total de materiales (BOM) se estableció en **$600.00 MXN**, cumpliendo el objetivo económico planteado. La incorporación del sensor de voltaje ZMPT101B incrementa marginalmente el costo, pero habilita el cálculo de potencia activa real:

- **Sin ZMPT101B:** el sistema solo estima potencia aparente ($S = V_{nominal} \times I_{RMS}$), asumiendo voltaje constante y factor de potencia unitario.
- **Con ZMPT101B:** el sistema calcula potencia activa real ($P = \frac{1}{N} \sum v[n] \cdot i[n]$), incorporando fluctuaciones de voltaje y desfase, elevando la precisión.

Esta relación costo-beneficio justifica la decisión de diseño y posiciona el prototipo como solución competitiva frente a alternativas comerciales, con reducción de costo superior al 60%.

---

## 13 Conclusiones parciales y trabajo futuro

### 13.1 Conclusiones del avance

Con base en el avance documentado hasta esta fase, se establecen las siguientes conclusiones parciales:

1. **Viabilidad técnica demostrada.** El diseño del sistema basado en ESP32 con sensores SCT-013 y ZMPT101B muestra que es factible implementar un dispositivo de medición de potencia activa real con capacidades comparables a un analizador de red básico, utilizando componentes genéricos de bajo costo disponibles en el mercado nacional.

2. **Precisión dentro de los parámetros objetivo.** Los resultados preliminares reportan $R^2 > 0.98$ y MAPE de $\pm 2.3\%$ para cargas superiores a 200 W, cumpliendo el criterio de aceptación (error $< 5\%$). La menor precisión en cargas inferiores a 50 W ($\pm 8.5\%$) se identifica y se declara como limitación inherente a la resolución del ADC y al rango del sensor.

3. **Viabilidad económica confirmada.** El costo total de la BOM se estableció en $600.00 MXN por unidad, representando una reducción superior al 60% respecto a soluciones comerciales equivalentes. La incorporación del sensor ZMPT101B (≈ $50 MXN) es una inversión marginal con alto retorno en términos de precisión.

4. **Identificación y mitigación de riesgos técnicos.** Las limitaciones del microcontrolador (no linealidad del ADC, conflicto ADC2/WiFi), las restricciones de instalación física (jaula de Faraday), las limitaciones del sistema eléctrico (monofásico, ancho de banda) y las contingencias de conectividad (modo híbrido WiFi/microSD) fueron analizadas y mitigadas.

5. **Clasificación metodológica consolidada.** La investigación se definió como aplicada-tecnológica, cuantitativa, correlacional-experimental y mixta (laboratorio y campo), proporcionando un marco sólido para la validación.

### 13.2 Trabajo futuro

Las siguientes líneas de desarrollo permanecen abiertas para fases subsecuentes:

1. **Completar las pruebas de campo:** instalación del prototipo en la vivienda residencial de estudio (Tenango del Valle) y ejecución del monitoreo continuo 24–72 horas, incluyendo comparación con el medidor de CFE.
2. **Formalizar el análisis estadístico completo:** aplicar pruebas de normalidad (Shapiro–Wilk), t de Student pareada, Bland–Altman y ANOVA de un factor (si aplica) a datos de campo.
3. **Optimizar el firmware:** refinar corrección de linealidad del ADC e implementar técnicas de promediado avanzadas para reducir error en cargas bajas.
4. **Mejorar resolución en cargas bajas:** evaluar integración de ADC externo de 16 bits (ADS1115 u homólogo) para precisión en rango *standby*.
5. **Extensión a servicio bifásico:** diseñar variante con dos canales de corriente y voltaje.
6. **Implementación de NILM avanzado:** explorar algoritmos de *Machine Learning* en el borde para desagregación de cargas.
7. **Desarrollo de interfaz remota:** implementar *dashboard* web/app con históricos, alertas y estimación de costos.
8. **Validación normativa:** evaluar pruebas bajo IEC 62053-21 como referencia metrológica.

---

## 14 Fuentes de información

American Psychological Association. (2020). *Publication manual of the American Psychological Association* (7th ed.). American Psychological Association. https://apastyle.apa.org/

Arias, F. G. (2012). *El proyecto de investigación: Introducción a la metodología científica* (6ª ed.). Editorial Episteme.

Ashton, K. (2009). That 'Internet of Things' thing. *RFID Journal*, *22*(7), 97–114.

Bland, J. M., & Altman, D. G. (1986). Statistical methods for assessing agreement between two methods of clinical measurement. *The Lancet*, *1*(8476), 307–310. https://pubmed.ncbi.nlm.nih.gov/2868172/

Comisión Federal de Electricidad. (2024). *Tarifas domésticas de energía eléctrica*. CFE. https://app.cfe.mx/Aplicaciones/CCFE/Tarifas/TarifasCRECasa/Casa.aspx

Creswell, J. W., & Creswell, J. D. (2018). *Research design: Qualitative, quantitative, and mixed methods approaches* (5th ed.). SAGE Publications.

Espressif Systems. (2022). *ESP32 Series Datasheet* (ver. 3.4). Espressif Systems. https://www.espressif.com/documentation/esp32_datasheet_en.pdf

Hart, D. W. (2011). *Power electronics*. McGraw-Hill Education.

Hart, G. W. (1992). Nonintrusive appliance load monitoring. *Proceedings of the IEEE*, *80*(12), 1870–1891.

Hernández Sampieri, R., Fernández Collado, C., & Baptista Lucio, M. del P. (2014). *Metodología de la investigación* (6ª ed.). McGraw-Hill Education.

International Electrotechnical Commission. (2003). *IEC 62053-21: Electricity metering equipment — Particular requirements — Part 21: Static meters for active energy (classes 1 and 2)*. IEC.

Kaselimi, M., Protopapadakis, E., Voulodimos, A., Doulamis, N. & Doulamis, A. (2022). Towards Trustworthy Energy Disaggregation: A Review of Challenges, Methods, and Perspectives for Non-Intrusive Load Monitoring. *Sensors*, *22*(15), 5872. https://doi.org/10.3390/s22155872

Naciones Unidas. (2015). *Transformar nuestro mundo: La Agenda 2030 para el Desarrollo Sostenible*. Asamblea General de las Naciones Unidas. https://sdgs.un.org/2030agenda

Norma Oficial Mexicana NOM-001-SEDE-2012. (2012). *Instalaciones Eléctricas (Utilización)*. Diario Oficial de la Federación, México.

Norma Oficial Mexicana NOM-003-SCFI-2014. (2014). *Productos eléctricos — Requisitos de seguridad*. Diario Oficial de la Federación, México.

OASIS. (2019). *MQTT Version 5.0* (OASIS Standard). OASIS Open. https://docs.oasis-open.org/mqtt/mqtt/v5.0/mqtt-v5.0.html

Oppenheim, A. V., & Willsky, A. S. (2014). *Signals and systems* (2nd ed.). Pearson Education.

Ramadan, R., Huang, Q., Zalhaf, A. S., Bamisile, O., Li, J., Mansour, D.-E. A., Lin, X. & Yehia, D. M. (2024). Energy Management in Residential Microgrid Based on Non-Intrusive Load Monitoring and Internet of Things. *Smart Cities*, *7*(4), 1907–1935. https://doi.org/10.3390/smartcities7040075

Shapiro, S. S., & Wilk, M. B. (1965). An analysis of variance test for normality (complete samples). *Biometrika*, *52*(3–4), 591–611. https://doi.org/10.1093/biomet/52.3-4.591

Tamayo y Tamayo, M. (2009). *El proceso de la investigación científica: Incluye evaluación y administración de proyectos de investigación* (5. ed.). Limusa.

---

## 15 Anexos

### Anexo A Operacionalización de variables

| Variable | Tipo | Definición operacional | Indicador | Instrumento | Escala |
|---|---|---|---|---|---|
| Carga eléctrica aplicada | Independiente | Potencia consumida por el dispositivo conectado al circuito de prueba | Watts (W) | Multímetro TRMS de referencia | Razón |
| $I_{RMS}$ | Dependiente | Valor RMS calculado por el firmware del ESP32 a partir del SCT-013 | Amperios (A) | Prototipo | Razón |
| $V_{RMS}$ | Dependiente | Valor RMS calculado a partir del ZMPT101B | Volts (V) | Prototipo | Razón |
| $P$ | Dependiente | Promedio del producto $v[n]\cdot i[n]$ | Watts (W) | Prototipo | Razón |
| $E_{\%}$ | Calculada | Diferencia porcentual prototipo vs patrón | % | Cálculo matemático | Razón |
| Costo de implementación | Dependiente | Suma de costos unitarios BOM | MXN | Cotización | Razón |

### Anexo B Encuesta complementaria (borrador)

____________________________________________
