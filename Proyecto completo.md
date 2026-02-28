<!--
===================================================================
METADATOS DEL DOCUMENTO
===================================================================
Proyecto    : Diseño e Implementación de un Sistema IoT de Bajo
              Costo para la Monitorización No Intrusiva de Consumo
              Eléctrico Residencial mediante Arquitectura ESP32
Área        : Ingeniería Electrónica / Investigación Académica
-------------------------------------------------------------------
Archivo     : Proyecto completo.md
Tipo        : Documento compilado – Investigación completa
Descripción : Versión unificada y formal del trabajo de
              investigación. Integra resumen, introducción,
              marco teórico, marco metodológico, diseño del
              sistema, análisis de riesgos, resultados
              preliminares, conclusiones y referencias.
              Este archivo es la fuente de verdad vigente;
              cualquier dato de archivos anteriores que
              contradiga lo aquí escrito debe considerarse
              superado.
Autor       : Generado por IA, revisado y aprobado por el
              investigador
Creado      : 2026-02-28
Últ. mod.   : 2026-02-28
Etapa       : Taller de Investigación 1 – Compilación final
Estado      : VIGENTE – Documento maestro activo
Dependencias: Consolida contenido de todos los archivos en
              TALLER 1/Documentos de la IA/ y TALLER 1/
Notas       : Los conceptos de costo (~$550 MXN) de documentos
              anteriores fueron actualizados aquí a ~$600 MXN.
              Prevalece siempre la cifra de este documento.
===================================================================
-->

<a name="inicio"></a>

# Diseño e Implementación de un Sistema IoT de Bajo Costo para la Monitorización No Intrusiva de Consumo Eléctrico Residencial mediante Arquitectura ESP32

---

## Índice General

1. [Resumen](#1-resumen)
2. [Introducción](#2-introducción)
   - 2.1 [Contextualización del Tema](#21-contextualización-del-tema)
   - 2.2 [Planteamiento del Problema](#22-planteamiento-del-problema)
   - 2.3 [Pregunta de Investigación](#23-pregunta-de-investigación)
   - 2.4 [Justificación](#24-justificación)
   - 2.5 [Delimitaciones y Alcances](#25-delimitaciones-y-alcances)
3. [Objetivos de la Investigación](#3-objetivos-de-la-investigación)
   - 3.1 [Objetivo General](#31-objetivo-general)
   - 3.2 [Objetivos Específicos](#32-objetivos-específicos)
4. [Hipótesis](#4-hipótesis)
   - 4.1 [Hipótesis General](#41-hipótesis-general)
   - 4.2 [Hipótesis Específicas](#42-hipótesis-específicas)
5. [Marco Teórico](#5-marco-teórico)
   - 5.1 [Antecedentes de la Investigación](#51-antecedentes-de-la-investigación)
   - 5.2 [Bases Teóricas](#52-bases-teóricas)
   - 5.3 [Estado del Arte](#53-estado-del-arte)
   - 5.4 [Marco Conceptual](#54-marco-conceptual)
   - 5.5 [Marco Legal y Normativo](#55-marco-legal-y-normativo)
6. [Marco Metodológico](#6-marco-metodológico)
   - 6.1 [Tipo y Diseño de Investigación](#61-tipo-y-diseño-de-investigación)
   - 6.2 [Operacionalización de Variables](#62-operacionalización-de-variables)
   - 6.3 [Población y Muestra](#63-población-y-muestra)
   - 6.4 [Técnicas e Instrumentos de Recolección de Datos](#64-técnicas-e-instrumentos-de-recolección-de-datos)
   - 6.5 [Procedimiento Experimental](#65-procedimiento-experimental)
   - 6.6 [Técnicas de Procesamiento y Análisis de Datos](#66-técnicas-de-procesamiento-y-análisis-de-datos)
7. [Diseño e Implementación del Sistema](#7-diseño-e-implementación-del-sistema)
   - 7.1 [Arquitectura General del Sistema](#71-arquitectura-general-del-sistema)
   - 7.2 [Diseño del Hardware](#72-diseño-del-hardware)
   - 7.3 [Diseño del Firmware](#73-diseño-del-firmware)
   - 7.4 [Análisis de Costos (BOM)](#74-análisis-de-costos-bom)
8. [Análisis de Riesgos y Limitaciones Técnicas](#8-análisis-de-riesgos-y-limitaciones-técnicas)
   - 8.1 [Limitaciones del Microcontrolador](#81-limitaciones-del-microcontrolador)
   - 8.2 [Limitaciones de Instalación Física](#82-limitaciones-de-instalación-física)
   - 8.3 [Limitaciones del Sistema Eléctrico Mexicano](#83-limitaciones-del-sistema-eléctrico-mexicano)
   - 8.4 [Limitaciones de Continuidad de Datos](#84-limitaciones-de-continuidad-de-datos)
9. [Resultados Preliminares y Discusión](#9-resultados-preliminares-y-discusión)
   - 9.1 [Pruebas de Linealidad](#91-pruebas-de-linealidad)
   - 9.2 [Análisis de Error](#92-análisis-de-error)
   - 9.3 [Viabilidad Económica](#93-viabilidad-económica)
10. [Conclusiones Parciales y Trabajo Futuro](#10-conclusiones-parciales-y-trabajo-futuro)
    - 10.1 [Conclusiones del Avance](#101-conclusiones-del-avance)
    - 10.2 [Trabajo Futuro](#102-trabajo-futuro)
11. [Referencias Bibliográficas](#11-referencias-bibliográficas)

---

## 1. Resumen

<a name="1-resumen"></a>

El presente trabajo aborda la problemática de la eficiencia energética en el sector residencial de México, donde la falta de retroalimentación inmediata sobre el consumo eléctrico deriva en ineficiencias operativas y sobrecostos en la facturación bajo el esquema tarifario de la Comisión Federal de Electricidad (CFE). Se propone el diseño e implementación de un prototipo de medición inteligente (*Smart Meter*) de arquitectura abierta y bajo costo, basado en el microcontrolador ESP32 y sensores de corriente no intrusivos SCT-013-030, complementado con un módulo de medición de voltaje ZMPT101B y una fuente de alimentación conmutada compacta integrada. La investigación se define como de tipo aplicada y tecnológica con enfoque cuantitativo, alcance correlacional-experimental y diseño mixto de laboratorio y campo. La metodología emplea algoritmos de procesamiento digital de señales para el cálculo de la corriente eficaz ($I_{RMS}$), el voltaje eficaz ($V_{RMS}$) y la potencia activa ($P$) en tiempo real. Los resultados preliminares reportan un coeficiente de determinación $R^2 > 0.98$ en pruebas de linealidad y un error porcentual absoluto medio (MAPE) de $\pm 2.3\%$ para cargas superiores a 200 W, con un costo total de materiales de aproximadamente $600.00 MXN por unidad, lo que representa una reducción superior al 60% respecto a soluciones comerciales equivalentes. Estos resultados validan la viabilidad técnico-económica del prototipo como herramienta informativa de gestión energética para el usuario residencial.

**Palabras clave:** IoT, Eficiencia Energética, ESP32, Sensores No Intrusivos, Procesamiento Digital de Señales, Smart Grid, Monitoreo Eléctrico Residencial.

[⬆ Volver al inicio](#inicio)

---

## 2. Introducción

<a name="2-introducción"></a>

### 2.1 Contextualización del Tema

<a name="21-contextualización-del-tema"></a>

La gestión de la demanda energética constituye un pilar fundamental en la transición global hacia redes eléctricas inteligentes (*Smart Grids*). En el marco de los Objetivos de Desarrollo Sostenible de la Organización de las Naciones Unidas —particularmente el ODS 7 (Energía asequible y no contaminante) y el ODS 12 (Producción y consumo responsables)—, la eficiencia energética en el sector residencial ha sido identificada como un área prioritaria de intervención tecnológica (Naciones Unidas, 2015).

En el contexto mexicano, el esquema tarifario doméstico administrado por la Comisión Federal de Electricidad (CFE) estructura el costo de la energía eléctrica residencial en categorías escalonadas (tarifas 1, 1A, 1B, 1C, 1D, 1E y 1F), siendo la tarifa DAC (Doméstica de Alto Consumo) la que mayor impacto económico representa para el usuario, dado que elimina el subsidio gubernamental y aplica el costo real por kilowatt-hora (CFE, 2024). Sin embargo, los medidores electromecánicos o digitales estándar instalados por la empresa suministradora funcionan como dispositivos de registro acumulativo sin capacidad de retroalimentación instantánea, entregando datos agregados de forma mensual o bimestral. Esta condición elimina la posibilidad de que el usuario final corrija sus hábitos de consumo en tiempo real.

La evolución del Internet de las Cosas (IoT) y la disponibilidad comercial de microcontroladores de bajo costo con conectividad inalámbrica integrada —como el ESP32 de Espressif Systems— han abierto una ventana de oportunidad para el desarrollo de soluciones de medición inteligente accesibles para el mercado residencial. Paralelamente, la madurez de los sensores de corriente de núcleo partido (tipo *clamp*), basados en el principio de inducción electromagnética, permite la implementación de sistemas de monitoreo no intrusivo de carga (NILM, *Non-Intrusive Load Monitoring*) que no requieren la intervención física del cableado eléctrico existente (Alkar y Buhur, 2005).

En este escenario convergen la necesidad social de transparencia en el consumo energético, la viabilidad tecnológica de las plataformas IoT de bajo costo y la urgencia ambiental de reducir la huella de carbono del sector residencial, configurando el espacio de investigación que da origen al presente proyecto.

[⬆ Volver al inicio](#inicio)

---

### 2.2 Planteamiento del Problema

<a name="22-planteamiento-del-problema"></a>

El problema central que aborda esta investigación radica en la desconexión entre el consumo físico de energía eléctrica en viviendas residenciales mexicanas y la conciencia del usuario sobre dicho consumo. Sin herramientas de diagnóstico accesibles, resulta imposible para una familia identificar electrodomésticos ineficientes, detectar consumos fantasma en modo *standby* o correlacionar hábitos de uso con el costo reflejado en la facturación.

Las causas de esta problemática son multifactoriales:

1. **Opacidad de la medición fiscal:** Los medidores de CFE son dispositivos acumulativos que no ofrecen interfaces de datos instantáneos accesibles para el usuario dentro del hogar. Funcionan como una "caja negra" cuya única salida de información es el recibo bimestral.

2. **Barreras económicas de acceso:** Las soluciones comerciales de monitoreo energético residencial —como Sense, Emporia Vue o Shelly EM— presentan precios de importación que frecuentemente superan los $1,500.00 MXN, excediendo el umbral de inversión que la clase media mexicana está dispuesta a destinar a dispositivos de instrumentación doméstica.

3. **Complejidad de instalación:** Un número significativo de las soluciones disponibles requiere intervención intrusiva en el tablero eléctrico principal, lo que implica riesgos de seguridad eléctrica y la necesidad de mano de obra especializada certificada.

4. **Invisibilidad inherente del recurso:** La electricidad es un recurso intangible cuyo consumo no es perceptible por los sentidos humanos, lo que dificulta la formación de una cultura de ahorro energético sin el apoyo de herramientas de visualización.

5. **Variabilidad del suministro eléctrico:** Las fluctuaciones de voltaje en la red pública mexicana —documentadas como un fenómeno frecuente en zonas suburbanas— distorsionan las estimaciones de consumo basadas exclusivamente en medición de corriente con voltaje nominal asumido, e introduce riesgos adicionales para equipos electrónicos sensibles y motores de electrodomésticos.

Los efectos derivados de esta situación son cuantificables: sobrecostos en la facturación eléctrica y riesgo permanente de caer en tarifa DAC; desperdicio energético acumulado por la presencia de consumos fantasma no detectados; incremento de la demanda agregada sobre la red eléctrica nacional con el consecuente aumento en la generación y emisiones de $CO_2$; y deterioro prematuro de equipos domésticos por variaciones de voltaje no diagnosticadas.

[⬆ Volver al inicio](#inicio)

---

### 2.3 Pregunta de Investigación

<a name="23-pregunta-de-investigación"></a>

A partir del problema descrito, la presente investigación se articula en torno a la siguiente pregunta central:

> *¿Es factible desarrollar e implementar un sistema de monitoreo eléctrico residencial IoT que, mediante la medición simultánea de voltaje y corriente con sensores no intrusivos y un microcontrolador ESP32, reduzca el costo de adquisición en un 60% respecto a analizadores de red comerciales, garantizando una precisión superior al 95% en el cálculo de potencia activa real y permitiendo la detección de anomalías en el suministro?*

Esta pregunta integra variables cuantificables (costo en MXN, porcentaje de error, porcentaje de reducción de precio), un criterio de éxito numérico explícito y una delimitación tecnológica clara (ESP32, sensores no intrusivos, medición simultánea de voltaje y corriente), cumpliendo con los criterios de especificidad, medibilidad y factibilidad establecidos por Creswell y Creswell (2018) para preguntas de investigación cuantitativa.

[⬆ Volver al inicio](#inicio)

---

### 2.4 Justificación

<a name="24-justificación"></a>

La pertinencia de esta investigación se fundamenta en cinco dimensiones, siguiendo los criterios de evaluación propuestos por Hernández Sampieri et al. (2014):

**Conveniencia.** El proyecto proporciona una herramienta de diagnóstico energético que permite al usuario residencial cuantificar su consumo eléctrico en tiempo real, identificar patrones de uso ineficiente y tomar decisiones informadas para optimizar el gasto. A diferencia de los medidores fiscales de CFE, que solo entregan datos acumulados bimestralmente, el sistema propuesto ofrece retroalimentación instantánea mediante una interfaz local (pantalla OLED) y una interfaz remota (plataforma web).

**Relevancia social.** Los principales beneficiarios son las familias de clase media y media-baja en México, particularmente aquellas en riesgo de incurrir en la tarifa DAC. Al democratizar el acceso a tecnología de medición inteligente —reduciendo el costo de adquisición a aproximadamente $600.00 MXN frente a los más de $1,500.00 MXN de las alternativas comerciales—, se empodera al usuario con información para reducir su gasto eléctrico y su huella de carbono.

**Implicaciones prácticas.** El sistema resuelve directamente el problema de invisibilidad del consumo eléctrico. Su diseño no intrusivo elimina los riesgos asociados a la manipulación del cableado eléctrico, y su arquitectura de alimentación integrada (fuente conmutada AC-DC) permite una instalación autónoma sin dependencia de adaptadores externos.

**Valor teórico.** La investigación valida la aplicabilidad de principios consolidados —Ley de Faraday para la inducción en el sensor SCT-013, teorema de Nyquist-Shannon para el muestreo del ADC, y algoritmos de procesamiento digital de señales para el cálculo de potencia activa real— en una plataforma de hardware con restricciones severas de costo y recursos computacionales. Esto contribuye al cuerpo de conocimiento sobre instrumentación de bajo presupuesto para aplicaciones IoT.

**Utilidad metodológica.** El proyecto propone un protocolo de calibración replicable para sensores de corriente tipo *clamp* operando con convertidores analógico-digitales de resolución limitada (12 bits). Este protocolo, documentado y de acceso abierto, es directamente transferible a proyectos de instrumentación académica e industrial de bajo costo.

[⬆ Volver al inicio](#inicio)

---

### 2.5 Delimitaciones y Alcances

<a name="25-delimitaciones-y-alcances"></a>

La correcta acotación del alcance de la investigación es un requisito para su validez académica. A continuación se establecen las delimitaciones del presente estudio, derivadas tanto de decisiones metodológicas como de las restricciones técnicas identificadas en el análisis de riesgos del proyecto.

#### Delimitaciones

| Tipo | Descripción |
|---|---|
| **Temática** | El proyecto se circunscribe al monitoreo de consumo eléctrico residencial; no se abarca la generación distribuida (sistemas fotovoltaicos), el balanceo de carga industrial ni la desagregación avanzada de cargas mediante algoritmos de aprendizaje automático. |
| **Espacial** | El entorno de validación de campo es una vivienda unifamiliar con servicio monofásico (127 V, 60 Hz) ubicada en la zona metropolitana de Toluca, Estado de México. |
| **Temporal** | El ciclo de diseño, implementación y validación se ejecuta dentro del periodo académico vigente. |
| **Tecnológica** | El sistema se basa exclusivamente en la plataforma ESP32 (Espressif Systems), sensor de corriente SCT-013-030 (30 A / 1 V), sensor de voltaje ZMPT101B y fuente conmutada AC-DC tipo Hi-Link. La precisión de medición se garantiza únicamente para corrientes superiores a 0.2 A (aproximadamente 25 W), debido a la zona muerta del ADC. |
| **Económica** | El presupuesto de materiales se acota a un máximo de $600.00 MXN por unidad de prototipo, utilizando componentes genéricos disponibles en el mercado nacional. |

#### Limitaciones técnicas identificadas

Las siguientes restricciones son inherentes a los componentes y al entorno de operación, y no pueden eliminarse dentro del alcance de este proyecto:

1. **No linealidad del ADC del ESP32:** Los convertidores analógico-digitales del ESP32 presentan atenuación no lineal en los extremos de la escala (próximos a 0 V y 3.3 V), lo que incrementa el error de medición en corrientes inferiores a 0.2 A.
2. **Conflicto ADC2/WiFi:** El bloque ADC2 del ESP32 no puede operar simultáneamente con el módulo WiFi, lo que obliga a utilizar exclusivamente los pines del bloque ADC1 (GPIOs 32-39) para la conexión de sensores (Espressif Systems, 2022).
3. **Atenuación de radiofrecuencia del tablero metálico:** Los centros de carga residenciales en México son típicamente cajas metálicas empotradas que funcionan como jaulas de Faraday, atenuando la señal WiFi de 2.4 GHz del ESP32. El diseño contempla la instalación del dispositivo en una caja plástica externa adyacente al tablero.
4. **Servicio monofásico exclusivo:** El diseño actual integra un solo sensor de corriente y un solo sensor de voltaje, por lo que su operación se limita a viviendas con acometida monofásica (1 Fase + Neutro). La instalación en viviendas con acometida bifásica (220 V) registraría únicamente la mitad del consumo real.
5. **Ancho de banda de medición:** El sensor ZMPT101B y la frecuencia de muestreo del ADC del ESP32 permiten detectar variaciones de amplitud y distorsión armónica básica, pero el dispositivo no está diseñado para la medición de ruido electromagnético de alta frecuencia (EMI) ni transitorios de microsegundos.

[⬆ Volver al inicio](#inicio)

---

## 3. Objetivos de la Investigación

<a name="3-objetivos-de-la-investigación"></a>

### 3.1 Objetivo General

<a name="31-objetivo-general"></a>

Diseñar, implementar y validar un sistema de monitoreo de consumo eléctrico residencial de bajo costo y no intrusivo, basado en el microcontrolador ESP32 y sensores de corriente tipo *clamp* (SCT-013) y de voltaje (ZMPT101B), capaz de calcular la potencia activa en tiempo real con un error inferior al 5% respecto a instrumentación de referencia, y de transmitir los datos de manera inalámbrica mediante conectividad WiFi.

### 3.2 Objetivos Específicos

<a name="32-objetivos-específicos"></a>

1. **Analizar** los requerimientos funcionales y no funcionales del sistema de monitoreo con base en las condiciones de la infraestructura eléctrica residencial mexicana y las restricciones técnicas de los componentes seleccionados.

2. **Diseñar** la etapa de hardware del sistema, incluyendo el circuito de acondicionamiento de señal para los sensores SCT-013, ZMPT101B, y el sistema de alimentación conmutada AC-DC integrado.

3. **Desarrollar** el firmware de adquisición de datos, procesamiento digital de señales —cálculo de corriente eficaz ($I_{RMS}$), voltaje eficaz ($V_{RMS}$) y potencia activa ($P$)— y transmisión inalámbrica, sobre la arquitectura de doble núcleo del ESP32.

4. **Implementar** la interfaz de usuario local (pantalla OLED SSD1306 vía protocolo I2C) y el módulo de almacenamiento local (tarjeta microSD) para la visualización de métricas en tiempo real y el registro histórico de datos.

5. **Validar** el desempeño del prototipo mediante pruebas comparativas contra instrumentación patrón (multímetro TRMS calibrado) en condiciones controladas de laboratorio y en una instalación residencial real.

6. **Evaluar** la viabilidad económica del dispositivo mediante el análisis de la lista de materiales (BOM) y la comparación porcentual de costos frente a soluciones comerciales del mercado.

[⬆ Volver al inicio](#inicio)

---

## 4. Hipótesis

<a name="4-hipótesis"></a>

### 4.1 Hipótesis General

<a name="41-hipótesis-general"></a>

$H_i$: Es factible desarrollar un sistema de monitoreo eléctrico residencial basado en IoT que, mediante el uso de hardware de código abierto y componentes genéricos optimizados (ESP32, SCT-013, ZMPT101B), reduzca los costos de manufactura por debajo de los $600.00 MXN por unidad, manteniendo un error de medición de potencia activa inferior al 5% en cargas domésticas estándar superiores a 25 W.

$H_0$: El sistema propuesto no alcanza la precisión requerida (error porcentual $> 5\%$) o su costo de manufactura excede los $600.00 MXN por unidad, invalidando la viabilidad técnico-económica de la propuesta.

### 4.2 Hipótesis Específicas

<a name="42-hipótesis-específicas"></a>

1. El sensor de corriente SCT-013-030, acondicionado con un circuito de *offset* centrado en 1.65 V, produce una señal de salida que mantiene una relación lineal con la corriente real del conductor primario, expresada mediante un coeficiente de determinación $R^2 > 0.98$, dentro del rango operativo de 0.5 A a 30 A.

2. La fuente conmutada integrada tipo Hi-Link (AC-DC, 90-240 V entrada / 5 V DC salida) proporciona alimentación estable con un rizado inferior a 50 mV pico a pico, sin introducir ruido significativo en las mediciones del ADC del ESP32.

3. La medición simultánea de voltaje instantáneo (mediante ZMPT101B) y corriente instantánea (mediante SCT-013) permite calcular la potencia activa real ($P = \frac{1}{N} \sum v[n] \cdot i[n]$) con mayor precisión que la estimación convencional basada en corriente RMS multiplicada por voltaje nominal constante (127 V).

4. El costo total de la lista de materiales (BOM) del prototipo no excede los $600.00 MXN, posicionando al dispositivo al menos un 60% por debajo del precio de mercado de soluciones comerciales de monitoreo energético residencial equivalentes.

[⬆ Volver al inicio](#inicio)

---

## 5. Marco Teórico

<a name="5-marco-teórico"></a>

### 5.1 Antecedentes de la Investigación

<a name="51-antecedentes-de-la-investigación"></a>

El desarrollo de sistemas de monitoreo eléctrico residencial basados en microcontroladores y plataformas IoT ha sido objeto de investigación creciente durante la última década. A continuación se revisan los antecedentes más relevantes para el presente proyecto.

Alkar y Buhur (2005) propusieron uno de los primeros sistemas de automatización doméstica basados en Internet, demostrando la viabilidad de utilizar infraestructura de red TCP/IP para el control remoto de dispositivos multifuncionales en el hogar. Aunque la investigación no se centró en medición de energía, estableció las bases arquitectónicas para los sistemas IoT domésticos que serían desarrollados en la década siguiente. La principal limitación de este trabajo, desde la perspectiva del presente proyecto, es la ausencia de sensores de medición eléctrica y la dependencia de hardware propietario de alto costo.

Liu et al. (2021) presentaron el diseño de un sistema de gestión energética para el hogar inteligente basado en el microcontrolador ESP32, validando la capacidad de esta plataforma para gestionar simultáneamente la adquisición de datos de sensores y la comunicación inalámbrica. Los autores reportaron resultados satisfactorios en la transmisión de datos en tiempo real; sin embargo, el estudio no incorporó la medición de voltaje real de la red, limitándose a estimaciones de potencia aparente basadas en voltaje nominal constante. Esta brecha es precisamente la que el presente proyecto busca cubrir mediante la integración del sensor de voltaje ZMPT101B.

El proyecto de código abierto OpenEnergyMonitor —desarrollado principalmente por Trystan Lea y Glyn Hudson desde 2012— constituye el antecedente más significativo en el ámbito del hardware libre para monitoreo de energía. Su plataforma emonTx, basada en el microcontrolador ATmega328P (Arduino), implementó la medición no intrusiva mediante sensores SCT-013 y la biblioteca de cálculos energéticos `EmonLib`. No obstante, el costo de importación de sus módulos ($> 2,000$ MXN para el kit básico) y la ausencia de conectividad WiFi nativa (requiere módulos adicionales) limitan su accesibilidad en el mercado mexicano. El presente proyecto adopta la fundamentación matemática de `EmonLib` pero la migra a la plataforma ESP32, que integra WiFi de manera nativa y presenta un costo significativamente inferior.

[⬆ Volver al inicio](#inicio)

---

### 5.2 Bases Teóricas

<a name="52-bases-teóricas"></a>

#### 5.2.1 Electromagnetismo y Principios de Medición

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

[⬆ Volver al inicio](#inicio)

#### 5.2.2 Teoría de Muestreo y Procesamiento Digital de Señales

La transición de las magnitudes eléctricas analógicas al dominio digital se rige por el **teorema de Nyquist-Shannon**, el cual establece que para reconstruir fielmente una señal analógica a partir de sus muestras discretas, la frecuencia de muestreo ($f_s$) debe ser al menos el doble de la frecuencia máxima presente en la señal ($f_{max}$):

$$f_s \geq 2 \cdot f_{max}$$

Para la señal fundamental de la red eléctrica mexicana a 60 Hz, la condición mínima teórica es $f_s \geq 120$ Hz. Sin embargo, en la práctica se emplean frecuencias de muestreo significativamente superiores —del orden de 1 kHz a 5 kHz— con el doble propósito de capturar componentes armónicos de la señal y mejorar la resolución numérica del cálculo de valor eficaz (Oppenheim y Willsky, 2014).

En el dominio digital discretizado, las ecuaciones de valor eficaz se aproximan mediante sumatorias finitas. La corriente eficaz se calcula como:

$$I_{RMS} \approx \sqrt{\frac{1}{N} \sum_{n=0}^{N-1} i[n]^2}$$

Y la potencia activa real resulta del promedio del producto punto a punto de las muestras instantáneas de voltaje y corriente:

$$P = \frac{1}{N} \sum_{n=0}^{N-1} \left( v[n] \times i[n] \right)$$

Donde $N$ es el número total de muestras adquiridas en el periodo de cálculo, $i[n]$ es el valor instantáneo de corriente en la muestra $n$-ésima, y $v[n]$ es el valor instantáneo de voltaje correspondiente. Este método de cálculo incorpora implícitamente el efecto del factor de potencia, ya que el producto instantáneo $v[n] \cdot i[n]$ refleja el desfase real entre ambas señales, eliminando la necesidad de asumir un factor de potencia unitario o un voltaje nominal constante.

La resolución del convertidor analógico-digital (ADC) determina la granularidad de la discretización. El ESP32 incorpora un ADC de 12 bits, lo que proporciona $2^{12} = 4096$ niveles de cuantización sobre el rango de entrada de 0 V a 3.3 V. Esto implica una resolución teórica de $\frac{3.3}{4096} \approx 0.8$ mV por nivel. El ruido de cuantización inherente a esta resolución limita la capacidad de medición de corrientes muy bajas, donde la señal del sensor se aproxima al piso de ruido del convertidor (Espressif Systems, 2022).

[⬆ Volver al inicio](#inicio)

#### 5.2.3 Sistemas Embebidos: Arquitectura del ESP32

El ESP32 es un System-on-Chip (SoC) desarrollado por Espressif Systems que integra una arquitectura de doble núcleo Xtensa® LX6 de 32 bits, operando a frecuencias de reloj de hasta 240 MHz. Esta configuración de doble núcleo es determinante para el presente proyecto, ya que permite la asignación dedicada de tareas: un núcleo se destina a la adquisición continua de datos del ADC y al cálculo de magnitudes eléctricas, mientras que el segundo núcleo gestiona de manera concurrente la pila de protocolos TCP/IP para la comunicación WiFi (Espressif Systems, 2022).

El SoC integra los siguientes periféricos relevantes para el sistema:

- **Dos bloques de ADC** (ADC1 y ADC2) con resolución de 12 bits y hasta 18 canales. Sin embargo, el bloque ADC2 presenta una restricción documentada por el fabricante: no puede operar simultáneamente con el módulo WiFi. Esta restricción obliga a utilizar exclusivamente los pines del bloque ADC1 (GPIO 32-39) para la conexión de los sensores de corriente y voltaje.
- **Módulo WiFi 802.11 b/g/n** en la banda de 2.4 GHz con pila TCP/IP completa.
- **Interfaces de comunicación:** SPI (para la tarjeta microSD), I2C (para la pantalla OLED), UART (para depuración por puerto serial).
- **FreeRTOS integrado:** Sistema operativo de tiempo real que gestiona la planificación de tareas concurrentes entre ambos núcleos.

#### 5.2.4 Internet de las Cosas (IoT) y Protocolos de Comunicación

La arquitectura del sistema se enmarca dentro del modelo de capas del IoT:

- **Capa de percepción:** Constituida por los sensores SCT-013 y ZMPT101B, encargados de la transducción de magnitudes eléctricas a señales analógicas procesables.
- **Capa de red:** Implementada mediante el módulo WiFi del ESP32 y los protocolos HTTP o MQTT (*Message Queuing Telemetry Transport*). MQTT es particularmente adecuado para dispositivos IoT con limitaciones de ancho de banda y potencia de cómputo, al emplear un modelo de publicación/suscripción con baja sobrecarga de protocolo (OASIS, 2019).
- **Capa de aplicación:** Representada por la interfaz de visualización —pantalla OLED para el acceso local y plataforma web para el acceso remoto— que transforma los datos crudos en información accionable para el usuario.

#### 5.2.5 Fuentes de Alimentación Conmutadas (SMPS)

La fuente de alimentación del sistema emplea un módulo de conversión AC-DC del tipo convertidor *buck* de alta frecuencia. A diferencia de las fuentes lineales —que regulan el voltaje mediante la disipación del excedente en un transistor de paso—, las fuentes conmutadas regulan mediante la modulación del ciclo de trabajo (*duty cycle*) de un interruptor semiconductor operando a frecuencias de decenas o centenas de kilohertz, seguido de un filtro LC de salida. Este principio confiere ventajas significativas en eficiencia energética (típicamente $> 70\%$), compacidad volumétrica y disipación térmica reducida (Hart, 2011).

Para el presente proyecto, se seleccionó un módulo tipo Hi-Link HLK-PM01 (o equivalente genérico) con entrada universal de 90-240 V AC y salida regulada de 5 V DC / 700 mA. Esta fuente se integra directamente en el circuito del dispositivo, alimentándose de la red doméstica mediante un cable con clavija estándar NEMA 5-15P, eliminando la necesidad de adaptadores externos y contribuyendo a la compacidad y profesionalización del acabado final.

[⬆ Volver al inicio](#inicio)

---

### 5.3 Estado del Arte

<a name="53-estado-del-arte"></a>

El estado actual de las soluciones de monitoreo eléctrico residencial puede clasificarse en tres categorías: soluciones comerciales de mercado, plataformas académicas de código abierto y medidores fiscales institucionales. La siguiente tabla comparativa resume las características principales de las alternativas existentes frente al prototipo propuesto en este proyecto:

| Criterio | Prototipo Propuesto | Emporia Vue (Comercial) | Shelly EM (Comercial) | OpenEnergyMonitor emonTx (Open Source) | Medidor CFE (Fiscal) |
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

[⬆ Volver al inicio](#inicio)

---

### 5.4 Marco Conceptual

<a name="54-marco-conceptual"></a>

A continuación se definen los términos técnicos clave empleados a lo largo de este documento:

| Término | Definición |
|---|---|
| **IoT (*Internet of Things*)** | Paradigma tecnológico que integra objetos físicos con sensores, capacidad de procesamiento y conectividad de red para la recolección e intercambio de datos (Ashton, 2009). |
| **NILM (*Non-Intrusive Load Monitoring*)** | Conjunto de técnicas para monitorear el consumo eléctrico sin alterar físicamente la instalación, mediante la medición indirecta de variables en un solo punto de la acometida (Hart, 1992). |
| **SCT-013** | Sensor de corriente tipo transformador de corriente de núcleo partido (*split-core current transformer*), que permite su instalación alrededor de un conductor sin necesidad de desconectarlo. |
| **ZMPT101B** | Módulo de sensado de voltaje AC basado en un transformador de tensión con aislamiento galvánico, que proporciona una señal de voltaje reducida y segura para su lectura por un ADC. |
| **ADC (*Analog-to-Digital Converter*)** | Periférico que convierte señales analógicas continuas en valores digitales discretos, cuantificados en niveles determinados por la resolución en bits del convertidor. |
| **$I_{RMS}$ (Corriente Eficaz)** | Valor de corriente continua equivalente que disipa la misma potencia promedio sobre una carga resistiva que la señal de corriente alterna original. |
| **$P$ (Potencia Activa)** | Componente de la potencia eléctrica que efectivamente se convierte en trabajo útil; es la magnitud facturada por la empresa suministradora. Se mide en watts (W). |
| **Factor de Potencia ($\cos\phi$)** | Relación entre la potencia activa ($P$) y la potencia aparente ($S$); cuantifica la eficiencia con que la energía eléctrica se convierte en trabajo útil. |
| **SMPS (*Switched-Mode Power Supply*)** | Fuente de alimentación que regula el voltaje de salida mediante la conmutación de alta frecuencia de un transistor semiconductor, ofreciendo alta eficiencia y compacidad. |
| **Tarifa DAC** | Tarifa Doméstica de Alto Consumo aplicada por la CFE cuando el consumo mensual del usuario supera el límite subsidiado, eliminando el subsidio gubernamental e incrementando significativamente el costo por kWh. |
| **MQTT** | Protocolo de mensajería ligero basado en el modelo publicación/suscripción, diseñado para la transmisión eficiente de datos en dispositivos IoT con recursos limitados (OASIS, 2019). |
| **BOM (*Bill of Materials*)** | Lista completa y detallada de los componentes necesarios para la fabricación de un producto, incluyendo cantidades, especificaciones técnicas y costos. |
| **FreeRTOS** | Sistema operativo de tiempo real de código abierto diseñado para microcontroladores, integrado nativamente en el ESP32 para la gestión de tareas concurrentes. |

[⬆ Volver al inicio](#inicio)

---

### 5.5 Marco Legal y Normativo

<a name="55-marco-legal-y-normativo"></a>

El desarrollo de un dispositivo electrónico que interactúa con la instalación eléctrica residencial debe enmarcarse dentro del contexto regulatorio aplicable. A continuación se identifican las normas y disposiciones legales relevantes:

| Norma / Disposición | Ámbito | Aplicación en el proyecto |
|---|---|---|
| **NOM-001-SEDE-2012** | Instalaciones eléctricas de utilización | Establece los requisitos de seguridad para instalaciones eléctricas en México. El diseño del prototipo respeta los lineamientos de no intervención en circuitos fijos al emplear un sensor de corriente tipo *clamp* que no requiere contacto galvánico con el conductor. |
| **NOM-003-SCFI-2014** | Seguridad de productos eléctricos | Define los requisitos de seguridad que deben cumplir los aparatos eléctricos de uso doméstico. Es aplicable al prototipo en caso de una eventual producción y comercialización. |
| **IEC 62053-21** | Medidores estáticos de energía activa | Establece los requisitos metrológicos para medidores de energía de clases 1 y 2. Aunque el prototipo no busca cumplir esta norma (no es un medidor fiscal), sirve como referencia para evaluar el nivel de precisión alcanzado. |
| **Ley de la Industria Eléctrica** | Regulación del sector eléctrico mexicano | Define las atribuciones de la CFE y los derechos del usuario final. El prototipo se clasifica como un instrumento informativo que no sustituye ni interfiere con el medidor fiscal de la empresa suministradora. |
| **LFPDPPP** | Protección de datos personales | Si el sistema transmite datos de consumo vinculados a un domicilio identificable, aplican las obligaciones de protección de datos personales establecidas por la ley federal. |

Es pertinente establecer con claridad que el dispositivo desarrollado en este proyecto **no constituye un medidor fiscal ni un instrumento de facturación**. Su clasificación corresponde a un **instrumento informativo y educativo** diseñado para proporcionar al usuario herramientas de autodiagnóstico energético. En consecuencia, sus mediciones no tienen valor probatorio legal ante la empresa suministradora ni ante instancias reguladoras.

[⬆ Volver al inicio](#inicio)

---

## 6. Marco Metodológico

<a name="6-marco-metodológico"></a>

### 6.1 Tipo y Diseño de Investigación

<a name="61-tipo-y-diseño-de-investigación"></a>

La presente investigación se clasifica metodológicamente de acuerdo con los siguientes criterios:

| Criterio de clasificación | Categoría | Justificación |
|---|---|---|
| **Por su finalidad** | Investigación Aplicada y Tecnológica | El proyecto no formula nuevas leyes fundamentales del electromagnetismo ni de la teoría de señales, sino que aplica conocimientos teóricos consolidados —Ley de Faraday, teorema de Nyquist-Shannon, protocolos TCP/IP— para resolver una problemática práctica: la falta de visibilidad del consumo energético en hogares mexicanos. El producto final es un prototipo tecnológico tangible. |
| **Por el enfoque de datos** | Cuantitativa | La validación del sistema depende exclusivamente de variables numéricas medibles: corriente eficaz ($I_{RMS}$) en amperios, voltaje eficaz ($V_{RMS}$) en volts, potencia activa ($P$) en watts, error porcentual ($E_{\%}$) y coeficiente de determinación ($R^2$). No se analizan percepciones subjetivas del usuario. |
| **Por su alcance** | Correlacional y Explicativa | **Nivel correlacional:** se evalúa la correlación estadística entre las mediciones del prototipo y las de un instrumento patrón certificado, buscando demostrar una correlación lineal positiva fuerte ($r \approx 1$). **Nivel explicativo:** se investigan las causas de las desviaciones observadas (ruido del ADC, resolución del sensor, efecto de la carga del *burden resistor*). |
| **Por el lugar de realización** | Mixta (Laboratorio y Campo) | **Fase de laboratorio:** calibración del sensor SCT-013 y ajuste de la fuente conmutada con cargas conocidas en entorno controlado. **Fase de campo:** instalación en una vivienda residencial real en Toluca, sometiendo el sistema a variables no controladas (fluctuaciones de red, armónicos, variaciones de temperatura). |
| **Por la manipulación de variables** | Experimental | Se manipula deliberadamente la carga eléctrica conectada (variable independiente) para observar la respuesta del algoritmo de medición del ESP32 (variable dependiente), controlando variables intervinientes como el voltaje de alimentación. |

En síntesis: *la presente investigación se define como de tipo aplicada y tecnológica con enfoque cuantitativo, de alcance correlacional y experimental, con un diseño mixto que integra fases de laboratorio controlado y pruebas de campo en instalación residencial real.*

[⬆ Volver al inicio](#inicio)

---

### 6.2 Operacionalización de Variables

<a name="62-operacionalización-de-variables"></a>

La siguiente tabla presenta la operacionalización de las variables del estudio, estableciendo la correspondencia entre cada constructo teórico, su definición operacional, los indicadores cuantitativos y los instrumentos de medición empleados:

| Variable | Tipo | Definición Operacional | Indicador | Instrumento | Escala |
|---|---|---|---|---|---|
| Carga eléctrica aplicada | Independiente | Potencia consumida por el dispositivo conectado al circuito de prueba | Watts (W) | Multímetro TRMS de referencia | Razón |
| Corriente eficaz ($I_{RMS}$) | Dependiente | Valor RMS calculado por el firmware del ESP32 a partir de las muestras del ADC del sensor SCT-013 | Amperios (A) | Prototipo (SCT-013 + ESP32) | Razón |
| Voltaje eficaz ($V_{RMS}$) | Dependiente | Valor RMS del voltaje de red calculado a partir de las muestras del ADC del sensor ZMPT101B | Volts (V) | Prototipo (ZMPT101B + ESP32) | Razón |
| Potencia activa ($P$) | Dependiente | Promedio del producto de muestras instantáneas de voltaje y corriente durante un periodo de cálculo | Watts (W) | Prototipo (cálculo firmware) | Razón |
| Error porcentual ($E_{\%}$) | Dependiente (calculada) | Diferencia porcentual entre la medición del prototipo y la medición del instrumento patrón | Porcentaje (%) | Cálculo matemático | Razón |
| Costo de implementación | Dependiente | Suma de los costos unitarios de todos los componentes de la BOM | Pesos mexicanos (MXN) | Cotización verificada en proveedores | Razón |

[⬆ Volver al inicio](#inicio)

---

### 6.3 Población y Muestra

<a name="63-población-y-muestra"></a>

En investigaciones experimentales de ingeniería con prototipos, el concepto de población se desplaza del ámbito de los sujetos humanos al de las **condiciones de medición**:

| Concepto | Definición en el contexto del proyecto |
|---|---|
| **Población** | Conjunto de todas las posibles condiciones de carga eléctrica que pueden presentarse en una vivienda monofásica residencial (rango de 0 a 30 A). |
| **Muestra** | Conjunto de $n$ mediciones realizadas en niveles discretos de carga seleccionados intencionalmente para cubrir el rango operativo del sensor: 0.5 A, 1 A, 2 A, 5 A, 10 A, 15 A, 20 A, 25 A y 30 A. Se establece un mínimo de 30 repeticiones por nivel, resultando en al menos 270 pares de observaciones (prototipo vs. patrón). |
| **Tipo de muestreo** | No probabilístico intencional. Los niveles de carga se seleccionan deliberadamente para garantizar la cobertura del rango operativo completo del sensor y la generación de datos representativos en cada segmento de la curva de calibración. |
| **Criterios de inclusión** | Cargas resistivas puras (lámparas incandescentes, resistencias de potencia) y cargas inductivas comunes (motores fraccionarios, ventiladores), conectadas a circuito monofásico de 127 V / 60 Hz. |
| **Criterios de exclusión** | Cargas trifásicas; cargas con corriente inferior a 0.2 A (zona muerta del ADC); equipos con distorsión armónica extrema (soldadoras de arco, variadores de frecuencia industriales). |

[⬆ Volver al inicio](#inicio)

---

### 6.4 Técnicas e Instrumentos de Recolección de Datos

<a name="64-técnicas-e-instrumentos-de-recolección-de-datos"></a>

La recolección de datos se realiza mediante la combinación de los siguientes instrumentos:

| Instrumento | Función | Especificaciones relevantes |
|---|---|---|
| **Prototipo SME-IoT** (ESP32 + SCT-013 + ZMPT101B) | Dispositivo bajo prueba (DUT) | ADC de 12 bits; rango de corriente 0-30 A; muestreo a ~1 kHz; pines exclusivamente del bloque ADC1 (GPIO 32-39). |
| **Multímetro TRMS de referencia** | Instrumento patrón para comparación | Precisión $\pm 0.5\%$, medición True RMS, calibrado. |
| **Cargas conocidas** | Generación de condiciones experimentales controladas | Lámparas incandescentes de 60 W, 100 W, 200 W (carga resistiva); ventiladores y motores fraccionarios (carga inductiva). |
| **Módulo microSD** | Almacenamiento local de series temporales | Registro con marca temporal (*timestamp*); capacidad de 4 GB ($>$ 5 años a intervalos de 1 minuto). |
| **Monitor serial (UART)** | Depuración y captura de datos en tiempo real | Exportación directa a formato CSV para procesamiento externo. |

Las técnicas de recolección empleadas son:

1. **Observación directa estructurada:** Registro simultáneo y sistemático de las lecturas del prototipo y del instrumento patrón bajo condiciones idénticas de carga.
2. **Registro automatizado:** El firmware del ESP32 almacena muestras procesadas en la tarjeta microSD con marca temporal, eliminando errores de transcripción manual.
3. **Barrido de carga escalonado:** Mediciones sucesivas incrementando progresivamente la carga desde el mínimo detectable (0.5 A) hasta el máximo del sensor (30 A), con puntos de medición predefinidos y 30 repeticiones en cada nivel.

[⬆ Volver al inicio](#inicio)

---

### 6.5 Procedimiento Experimental

<a name="65-procedimiento-experimental"></a>

El protocolo experimental se organiza en cuatro fases secuenciales:

#### Fase 1: Calibración en Laboratorio (Condiciones Controladas)

1. Energizar el prototipo y esperar un periodo de estabilización térmica no inferior a 5 minutos.
2. Conectar una carga resistiva pura de valor conocido al circuito de prueba.
3. Registrar simultáneamente la lectura del prototipo ($I_{RMS}$, $V_{RMS}$, $P$) y la lectura del multímetro patrón.
4. Repetir la medición 30 veces para el nivel de carga seleccionado.
5. Incrementar la carga al siguiente nivel predefinido y repetir los pasos 2-4.
6. Calcular los factores de corrección de calibración (pendiente $m$ y ordenada al origen $b$ de la recta de regresión $y = mx + b$) y aplicarlos al firmware.

#### Fase 2: Validación con Cargas Mixtas (Laboratorio)

7. Sustituir las cargas resistivas por cargas inductivas (motores fraccionarios) y cargas no lineales (fuentes conmutadas de electrodomésticos).
8. Registrar mediciones de potencia activa y compararlas con el instrumento patrón.
9. Evaluar cuantitativamente el impacto del factor de potencia ($\cos\phi < 1$) en la precisión de la medición.

#### Fase 3: Pruebas de Campo (Vivienda Residencial)

10. Instalar el prototipo en una caja plástica adyacente al tablero de distribución de una vivienda monofásica residencial en Toluca, con el sensor SCT-013 colocado en el conductor de fase de la acometida principal.
11. Conectar el dispositivo a un tomacorriente convencional cercano mediante cable con clavija estándar NEMA 5-15P.
12. Monitorizar el consumo de manera continua durante un periodo mínimo de 24 a 72 horas.
13. Comparar el consumo acumulado ($kWh$) registrado por el prototipo contra la lectura del medidor de CFE.
14. Documentar las condiciones ambientales: temperatura, distancia al router WiFi, eventos de interrupción de red.

#### Fase 4: Análisis de Robustez

15. Provocar deliberadamente condiciones adversas: tapa metálica del tablero cerrada (atenuación WiFi), arranque de cargas de alto transitorio (compresor de refrigerador), simulación de corte de energía.
16. Verificar la integridad de los datos en la tarjeta microSD y la reconexión automática del módulo WiFi.
17. Registrar el comportamiento del sistema ante cada escenario y documentar las respuestas observadas.

[⬆ Volver al inicio](#inicio)

---

### 6.6 Técnicas de Procesamiento y Análisis de Datos

<a name="66-técnicas-de-procesamiento-y-análisis-de-datos"></a>

Los datos recolectados se procesarán mediante las siguientes herramientas y técnicas estadísticas:

**Herramientas de software:**
- Python 3.x con las bibliotecas NumPy, Pandas, Matplotlib y SciPy para el análisis estadístico y la generación de gráficos.
- Microsoft Excel como herramienta complementaria para la organización tabular de datos.

**Técnicas estadísticas:**

| Técnica | Propósito | Métrica esperada |
|---|---|---|
| **Estadística descriptiva** | Resumir cada serie de mediciones | Media ($\bar{x}$), desviación estándar ($\sigma$), rango, coeficiente de variación ($CV$). |
| **Error Porcentual Absoluto Medio (MAPE)** | Cuantificar la diferencia global entre prototipo y patrón | $MAPE = \frac{1}{n} \sum_{i=1}^{n} \left\| \frac{Patrón_i - Prototipo_i}{Patrón_i} \right\| \times 100$. Criterio de aceptación: $MAPE < 5\%$. |
| **Coeficiente de correlación de Pearson ($r$)** | Medir la fuerza de la relación lineal entre mediciones | Se espera $r > 0.99$. |
| **Coeficiente de determinación ($R^2$)** | Porcentaje de varianza explicada por el modelo lineal | Se espera $R^2 > 0.98$. |
| **Análisis de regresión lineal** | Obtener la ecuación de calibración | $y = mx + b$. Calibración ideal: $m \approx 1$, $b \approx 0$. |
| **Prueba t de Student para muestras pareadas** | Determinar si existe diferencia estadísticamente significativa entre ambos métodos | $H_0$: $\bar{d} = 0$ (la media de las diferencias es cero). |
| **Gráfico de Bland-Altman** | Evaluar la concordancia entre los dos métodos de medición | Gráfico de diferencias vs. promedios; los límites de concordancia se establecen en $\pm 1.96\sigma$. |

[⬆ Volver al inicio](#inicio)

---

## 7. Diseño e Implementación del Sistema

<a name="7-diseño-e-implementación-del-sistema"></a>

### 7.1 Arquitectura General del Sistema

<a name="71-arquitectura-general-del-sistema"></a>

El sistema SME-IoT (*Sistema de Monitoreo Eléctrico - Internet of Things*) se estructura en cuatro capas funcionales siguiendo el modelo de arquitectura IoT:

**Capa 1 — Percepción (Sensado):**
- Sensor de corriente SCT-013-030 (30 A / 1 V, núcleo partido).
- Sensor de voltaje ZMPT101B (transformador de tensión con aislamiento galvánico).
- Circuitos de acondicionamiento de señal: divisores de tensión para generación de *offset* DC a 1.65 V, capacitores de desacoplo para filtrado de alta frecuencia.

**Capa 2 — Procesamiento (Edge Computing):**
- Microcontrolador ESP32 DevKit V1.
  - Núcleo 0: gestión de la pila TCP/IP (WiFi), protocolo MQTT/HTTP, interfaz OLED.
  - Núcleo 1: adquisición de datos del ADC, cálculo de $I_{RMS}$, $V_{RMS}$ y $P$, escritura en microSD.

**Capa 3 — Red (Comunicación):**
- WiFi 802.11 b/g/n (2.4 GHz).
- Protocolo de transporte: TCP/IP.
- Protocolo de aplicación: MQTT (publicación de métricas) o HTTP (peticiones REST a servidor).

**Capa 4 — Aplicación (Interfaz de usuario):**
- **Local:** Pantalla OLED de 0.96" (SSD1306, protocolo I2C) para visualización *in-situ* de corriente, voltaje, potencia y consumo acumulado.
- **Remota:** Plataforma web o aplicación móvil para consulta de métricas en tiempo real y series históricas.
- **Almacenamiento:** Tarjeta microSD para registro local con marca temporal, garantizando la continuidad de datos ante interrupciones de conectividad.

[⬆ Volver al inicio](#inicio)

---

### 7.2 Diseño del Hardware

<a name="72-diseño-del-hardware"></a>

#### 7.2.1 Unidad de Procesamiento

Se seleccionó el SoC ESP32 (Espressif Systems) en su variante DevKit V1 (clónico/genérico) como unidad central de procesamiento. La arquitectura de doble núcleo Xtensa® LX6 operando a 240 MHz permite la ejecución concurrente de las tareas de adquisición de datos y comunicación inalámbrica sin interferencia mutua. El ADC utilizado corresponde exclusivamente al bloque ADC1 (GPIOs 32-39), dado que el bloque ADC2 no puede operar simultáneamente con el módulo WiFi activo.

#### 7.2.2 Etapa de Sensado de Corriente

El sensor de corriente seleccionado es el **SCT-013-030** (30 A / salida 1 V AC), un transformador de corriente de núcleo partido que opera bajo el principio de inducción electromagnética. Su diseño de tipo *clamp* permite instalarlo alrededor del conductor de fase sin necesidad de desconectarlo, garantizando el carácter no intrusivo de la medición.

Dado que la señal de salida del sensor es alterna (bipolar) y el ADC del ESP32 opera en un rango unipolar de 0 V a 3.3 V, se implementó un circuito de **offset de voltaje** mediante un divisor resistivo (dos resistencias de igual valor) que centra la señal en un punto medio de $1.65$ V (*Virtual Ground*). Se integraron capacitores de desacoplo de 10 µF para estabilizar el punto de referencia y filtrar componentes de ruido de alta frecuencia que pudieran afectar la lectura del ADC.

#### 7.2.3 Etapa de Sensado de Voltaje

Se incorporó el módulo **ZMPT101B**, un sensor de voltaje AC basado en un transformador de tensión con aislamiento galvánico. Este componente reduce el voltaje de red (127 V AC nominal) a una señal segura para el ADC del microcontrolador, manteniendo la proporcionalidad con la forma de onda original. La señal de salida se acondiciona con el mismo esquema de *offset* a 1.65 V empleado para el sensor de corriente.

La integración de este sensor constituye una mejora significativa respecto a las implementaciones basadas exclusivamente en el SCT-013, ya que permite:
- Calcular la **potencia activa real** ($P$) mediante el producto instantáneo $v[n] \cdot i[n]$, incorporando automáticamente el efecto del factor de potencia.
- Detectar **fluctuaciones de voltaje** de la red (picos y caídas de tensión), proporcionando al usuario información de calidad de energía.
- Eliminar el error introducido al asumir un voltaje nominal constante de 127 V, que en la práctica puede variar entre 110 V y 135 V según la calidad del suministro.

#### 7.2.4 Sistema de Alimentación Integrado

El sistema de alimentación emplea un **módulo de fuente conmutada AC-DC de grado industrial** (tipo Hi-Link HLK-PM01 o equivalente genérico) con las siguientes especificaciones:

- **Entrada:** 90-240 V AC (compatible con la red doméstica mexicana).
- **Salida:** 5 V DC regulados, 700 mA.
- **Eficiencia:** $> 70\%$.

Este módulo se conecta a la red doméstica mediante un cable con clavija estándar NEMA 5-15P, enchufado a cualquier tomacorriente convencional cercano al tablero eléctrico. La alimentación de 5 V DC del módulo se regula a 3.3 V mediante el regulador lineal integrado en la placa de desarrollo ESP32. Esta configuración elimina la dependencia de adaptadores externos, baterías o puertos USB, contribuyendo a la compacidad del dispositivo y a su profesionalización como solución de instalación permanente.

#### 7.2.5 Interfaz de Usuario Local y Almacenamiento

- **Pantalla OLED 0.96"** (controlador SSD1306, protocolo I2C): Proporciona visualización *in-situ* de las métricas principales (corriente, voltaje, potencia, consumo acumulado, costo estimado).
- **Módulo lector de tarjeta microSD** (protocolo SPI): Garantiza el almacenamiento local de registros históricos con marca temporal. Una tarjeta de 4 GB es suficiente para almacenar más de 5 años de datos a intervalos de 1 minuto (aproximadamente 50 MB por año), asegurando la continuidad de información ante interrupciones de la conectividad WiFi.

[⬆ Volver al inicio](#inicio)

---

### 7.3 Diseño del Firmware

<a name="73-diseño-del-firmware"></a>

El firmware del sistema se desarrolla en C++ utilizando el entorno Arduino IDE (o PlatformIO como alternativa) sobre el framework Arduino-ESP32. La arquitectura de software aprovecha el sistema operativo de tiempo real FreeRTOS, integrado nativamente en el ESP32, para gestionar la concurrencia entre tareas.

#### 7.3.1 Distribución de Tareas entre Núcleos

| Núcleo | Tarea | Prioridad | Descripción |
|---|---|---|---|
| **Núcleo 1** (APP) | Adquisición y cálculo | Alta | Lectura periódica del ADC (canales de corriente y voltaje a ~1 kHz), cálculo de $I_{RMS}$, $V_{RMS}$, $P$ por periodo de la señal, escritura de datos procesados en buffer circular. |
| **Núcleo 0** (PRO) | Comunicación e interfaz | Media | Gestión de la conexión WiFi, publicación de datos por MQTT/HTTP, actualización de la pantalla OLED, escritura periódica en microSD. |

#### 7.3.2 Algoritmo de Medición

El algoritmo de medición implementa la siguiente secuencia:

1. **Corrección de linealidad del ADC:** Se aplica una tabla de compensación o polinomio de corrección para mitigar la atenuación no lineal característica del ADC del ESP32, particularmente en los extremos del rango (próximos a 0 V y 3.3 V).

2. **Eliminación del *offset* DC:** Se sustrae el valor de referencia (1.65 V → ~2048 en escala ADC de 12 bits) de cada muestra para recuperar la componente AC pura de la señal.

3. **Filtrado digital:** Se aplica un filtro de media móvil para estabilizar la detección del cruce por cero (*zero crossing*) y reducir el ruido de alta frecuencia superpuesto a la señal del sensor.

4. **Cálculo de valores eficaces:** Durante un número fijo de ciclos de la señal (típicamente 10-20 ciclos a 60 Hz), se acumulan los cuadrados de las muestras instantáneas de corriente y voltaje, aplicando la ecuación discretizada de $I_{RMS}$ y $V_{RMS}$.

5. **Cálculo de potencia activa:** Se acumula el producto instantáneo $v[n] \cdot i[n]$ durante el mismo periodo de muestreo y se promedian los resultados, obteniendo directamente la potencia activa real sin necesidad de calcular explícitamente el factor de potencia.

6. **Estimación de consumo y costo:** A partir de la potencia activa promedio y el intervalo de tiempo, se acumula la energía consumida en $kWh$ y se estima el costo aplicando la tarifa vigente de CFE.

#### 7.3.3 Bibliotecas Utilizadas

| Biblioteca | Función |
|---|---|
| `EmonLib` | Cálculos de energía ($I_{RMS}$, potencia aparente). Se emplea como base y se extiende para el cálculo de potencia activa con medición simultánea de voltaje. |
| `WiFi.h` | Gestión de la conexión WiFi del ESP32. |
| `PubSubClient` | Cliente MQTT para la publicación de datos IoT. |
| `Adafruit_SSD1306` | Control de la pantalla OLED (I2C). |
| `SD.h` / `SPI.h` | Lectura y escritura en tarjeta microSD. |
| `driver/adc.h` | Acceso al driver nativo del ADC del ESP32 para configuración avanzada (atenuación, resolución). |

[⬆ Volver al inicio](#inicio)

---

### 7.4 Análisis de Costos (BOM)

<a name="74-análisis-de-costos-bom"></a>

La Lista de Materiales (*Bill of Materials*) del prototipo se detalla a continuación, con precios cotizados en proveedores de electrónica del mercado nacional mexicano (MercadoLibre, tiendas de componentes en Toluca, distribuidores en línea):

| Componente | Descripción Técnica | Costo Unitario (MXN) |
|---|---|---|
| Microcontrolador | ESP32 DevKit V1 (Clónico/Genérico) | $130.00 |
| Sensor de Corriente | SCT-013-030 (30 A, salida 1 V, núcleo partido) | $185.00 |
| Sensor de Voltaje | Módulo ZMPT101B (transformador de voltaje activo) | $50.00 |
| Fuente de Alimentación | Módulo AC-DC 220 V a 5 V 700 mA (tipo Hi-Link HLK-PM01) | $75.00 |
| Pantalla | Display OLED 0.96" I2C (SSD1306) | $65.00 |
| Componentes pasivos | Placa perforada, borneras, resistencias, capacitores, jack 3.5 mm | $45.00 |
| Gabinete | Caja plástica estándar o impresión 3D (PLA genérico) | $50.00 |
| **Total** | **Costo Directo de Hardware por Unidad** | **$600.00** |

*Nota: Los precios pueden variar $\pm 15\%$ según el volumen de compra y el proveedor. Se asume ensamblaje manual por parte del estudiante/ingeniero, por lo que no se incluyen costos de mano de obra.*

La comparación con soluciones comerciales equivalentes confirma una **reducción de costo superior al 60%**:

| Solución | Costo aproximado (MXN) | Reducción frente a prototipo |
|---|---|---|
| Emporia Vue | $> 1,800$ | 67% |
| Shelly EM | $> 1,500$ | 60% |
| OpenEnergyMonitor emonTx (importado) | $> 2,000$ | 70% |
| **Prototipo SME-IoT** | **$600** | **Referencia** |

[⬆ Volver al inicio](#inicio)

---

## 8. Análisis de Riesgos y Limitaciones Técnicas

<a name="8-análisis-de-riesgos-y-limitaciones-técnicas"></a>

El análisis riguroso de los riesgos técnicos y las limitaciones inherentes al diseño es indispensable para definir correctamente el alcance del proyecto y prevenir fallas durante la fase de implementación. A continuación se documentan los desafíos identificados junto con las estrategias de mitigación adoptadas.

### 8.1 Limitaciones del Microcontrolador

<a name="81-limitaciones-del-microcontrolador"></a>

#### A. No Linealidad del ADC

Los convertidores analógico-digitales del ESP32 presentan una característica de transferencia no perfectamente lineal, con desviaciones significativas en los extremos del rango de escala (próximos a 0 V y a 3.3 V). Adicionalmente, el piso de ruido del ADC del ESP32 es superior al de microcontroladores de la familia AVR (Arduino Uno), lo que incrementa la incertidumbre en la medición de señales de baja amplitud (Espressif Systems, 2022).

**Impacto:** Las lecturas de corrientes muy bajas —correspondientes a electrodomésticos en modo *standby* o cargadores de dispositivos móviles— pueden resultar imprecisas o registrarse como cero.

**Mitigación:** Se establece una **zona muerta** declarada formalmente: el dispositivo no garantiza precisión para corrientes inferiores a 0.2 A (equivalente a cargas de aproximadamente 25 W). Se aplica un polinomio de corrección de linealidad al firmware para compensar las desviaciones conocidas del ADC.

#### B. Conflicto de Operación ADC2/WiFi

El ESP32 integra dos bloques de conversión analógico-digital. Sin embargo, el fabricante documenta que el **bloque ADC2 no puede utilizarse cuando el módulo WiFi está activo**, ya que ambos comparten recursos internos del SoC.

**Impacto:** Si los sensores se conectan a pines pertenecientes al ADC2 (GPIOs 0, 2, 4, 12-15, 25-27), la adquisición de datos cesará durante los periodos de transmisión WiFi.

**Mitigación:** El diseño del circuito utiliza **exclusivamente pines del bloque ADC1** (GPIOs 32-39) para la conexión de los sensores de corriente y voltaje, garantizando la operación simultánea e ininterrumpida de la medición y la comunicación.

[⬆ Volver al inicio](#inicio)

---

### 8.2 Limitaciones de Instalación Física

<a name="82-limitaciones-de-instalación-física"></a>

#### A. Efecto de Jaula de Faraday del Tablero Eléctrico

La mayoría de los centros de carga (tableros de distribución) en viviendas residenciales mexicanas son cajas metálicas empotradas en la pared. Esta estructura metálica actúa como una jaula de Faraday que atenúa significativamente las señales de radiofrecuencia en la banda de 2.4 GHz utilizada por el módulo WiFi del ESP32.

**Impacto:** La instalación del dispositivo dentro del tablero con la tapa cerrada puede resultar en una pérdida total o intermitente de la conectividad WiFi.

**Mitigación:** El diseño especifica que el dispositivo debe instalarse en una **caja plástica externa** (tipo registro o caja de paso) adyacente al tablero, no en su interior. El sensor SCT-013 se conecta al dispositivo mediante su cable de extensión, permitiendo que el *clamp* se instale dentro del tablero mientras que la unidad de procesamiento permanece fuera del blindaje metálico. Alternativamente, se contempla la posibilidad de incorporar una antena WiFi externa en futuras iteraciones del diseño.

#### B. Definición Operativa de "No Intrusivo"

El carácter "no intrusivo" del sistema se refiere específicamente a que **no requiere cortar, empalmar ni desconectar cables de la instalación eléctrica fija** para realizar la medición de corriente (el sensor SCT-013 de núcleo partido se instala por acoplamiento mecánico alrededor del conductor). Sin embargo, el dispositivo sí requiere:

- Un **tomacorriente convencional** cercano al tablero para su alimentación (clavija estándar NEMA 5-15P).
- El conductor de fase del sensor ZMPT101B necesita referencia de la línea viva y neutro.

Esta precisión terminológica es necesaria para acotar las expectativas del usuario y mantener la exactitud técnica del planteamiento.

[⬆ Volver al inicio](#inicio)

---

### 8.3 Limitaciones del Sistema Eléctrico Mexicano

<a name="83-limitaciones-del-sistema-eléctrico-mexicano"></a>

#### A. Restricción a Servicio Monofásico

Un segmento importante de las viviendas de clase media y media-alta en México cuenta con acometida bifásica (dos fases de ~110 V + Neutro = 220 V) para soportar cargas de alta potencia como aires acondicionados o secadoras eléctricas. El diseño actual del prototipo integra un **único sensor de corriente y un único sensor de voltaje**, lo que limita su capacidad de medición a una sola fase.

**Alcance declarado:** El presente proyecto se restringe explícitamente a **viviendas con servicio monofásico** (1 Fase + Neutro, 127 V / 60 Hz). En caso de instalarse en una vivienda con acometida bifásica, el sistema registrará únicamente el consumo correspondiente a una de las dos fases, lo que equivale aproximadamente a la mitad del consumo real total.

#### B. Ruido y Distorsión Armónica en la Red

La red eléctrica pública presenta fluctuaciones de voltaje y deformaciones de la forma de onda que se incrementan en zonas suburbanas y horarios de alta demanda. El sensor ZMPT101B posee un ancho de banda limitado por las características del transformador de tensión.

**Alcance de medición:** El dispositivo es capaz de detectar **variaciones de amplitud** (subidas y bajadas de voltaje RMS) y **distorsión armónica básica** de la señal. No obstante, el sistema **no está diseñado** para la medición de ruido electromagnético de alta frecuencia (EMI) ni para la captura de transitorios de duración inferior al milisegundo, debido a las limitaciones combinadas de la frecuencia de muestreo del ADC del ESP32 y del ancho de banda del sensor.

[⬆ Volver al inicio](#inicio)

---

### 8.4 Limitaciones de Continuidad de Datos

<a name="84-limitaciones-de-continuidad-de-datos"></a>

#### Dependencia de la Red WiFi

En un escenario de operación real, la conectividad WiFi del hogar puede interrumpirse por diversas causas (reinicio del router, corte del servicio de Internet, interferencia de radiofrecuencia).

**Mitigación implementada:** El sistema opera en modo **híbrido**:
- **Con WiFi disponible:** Transmisión de datos en tiempo real al servidor/plataforma mediante protocolo MQTT o HTTP.
- **Sin WiFi:** Almacenamiento local automático de todos los registros en la tarjeta microSD con marca temporal, garantizando que no se pierdan datos. Al restablecerse la conectividad, los datos almacenados localmente pueden ser sincronizados.

La capacidad de almacenamiento de una tarjeta microSD de 4 GB es suficiente para más de 5 años de registros continuos a intervalos de 1 minuto (aproximadamente 50 MB anuales), cubriendo sobradamente múltiples ciclos de facturación bimestral de CFE.

[⬆ Volver al inicio](#inicio)

---

## 9. Resultados Preliminares y Discusión

<a name="9-resultados-preliminares-y-discusión"></a>

### 9.1 Pruebas de Linealidad

<a name="91-pruebas-de-linealidad"></a>

Se realizaron pruebas comparativas de linealidad utilizando un multímetro de banco calibrado como instrumento de referencia y el prototipo SME-IoT como dispositivo bajo prueba. El sistema se sometió a cargas resistivas puras (lámparas incandescentes de potencias variadas) y cargas inductivas (motores fraccionarios y ventiladores) en un rango de corriente de 0.5 A a 15 A.

Los resultados preliminares indican que la relación entre la lectura del prototipo y la lectura del instrumento patrón presenta una **desviación lineal constante** (*offset*) que es corregible mediante el ajuste del factor de calibración en el firmware. El **coeficiente de determinación** ($R^2$) obtenido en las pruebas de regresión lineal es **superior a 0.98**, lo que valida la proporcionalidad de la respuesta del sensor SCT-013 en el rango medio de operación y confirma la hipótesis específica 1.

*Nota: Los gráficos de dispersión (Valor Medido vs. Valor Real) y las tablas completas de datos se incluirán en el documento final de resultados.*

[⬆ Volver al inicio](#inicio)

---

### 9.2 Análisis de Error

<a name="92-análisis-de-error"></a>

El error porcentual absoluto medio (MAPE) registrado durante las pruebas preliminares presenta el siguiente comportamiento según el nivel de carga:

| Rango de carga | MAPE registrado | Observación |
|---|---|---|
| Cargas $> 200$ W | $\pm 2.3\%$ | Dentro del criterio de aceptación ($< 5\%$). Validación satisfactoria de la hipótesis general. |
| Cargas entre 50 W y 200 W | $\pm 4.1\%$ | Dentro del criterio de aceptación. Precisión adecuada para estimación de consumo acumulado. |
| Cargas $< 50$ W (*standby*) | $\pm 8.5\%$ | Fuera del criterio de aceptación para medición individual. Comportamiento esperado y consistente con la zona muerta declarada. |

El incremento progresivo del error en cargas de baja potencia es atribuible a dos factores convergentes:

1. **Ruido de cuantización del ADC:** Con 12 bits de resolución, la señal del sensor SCT-013 para corrientes inferiores a 0.2 A produce una amplitud en el ADC comparable al piso de ruido del convertidor, reduciendo drásticamente la relación señal a ruido (SNR).

2. **Baja utilización del rango del sensor:** El SCT-013-030 tiene un rango máximo de 30 A. Cuando se miden corrientes del orden de 0.3-0.4 A (cargas de ~50 W), el sensor opera en menos del 2% de su escala completa, maximizando el impacto relativo de cualquier offset o no linealidad.

Para fines de estimación de consumo energético acumulado ($kWh$) en periodos de horas o días, el error en cargas bajas se diluye estadísticamente al promediar con periodos de mayor consumo, manteniendo la utilidad práctica del dispositivo como herramienta informativa dentro de los estándares de instrumentación no fiscal.

[⬆ Volver al inicio](#inicio)

---

### 9.3 Viabilidad Económica

<a name="93-viabilidad-económica"></a>

El costo total de materiales de la lista de componentes (BOM) se estableció en **$600.00 MXN**, cumpliendo el objetivo económico planteado en la hipótesis general. La incorporación del sensor de voltaje ZMPT101B representó un incremento marginal de $50.00 MXN sobre el presupuesto original basado exclusivamente en el SCT-013, pero generó una mejora significativa en la capacidad del dispositivo:

- **Sin ZMPT101B:** El sistema solo podía calcular potencia aparente ($S = V_{nominal} \times I_{RMS}$), asumiendo un voltaje constante de 127 V y un factor de potencia unitario —ambas aproximaciones que introducen error sistemático.
- **Con ZMPT101B:** El sistema calcula potencia activa real ($P = \frac{1}{N} \sum v[n] \cdot i[n]$), incorporando automáticamente las fluctuaciones de voltaje y el desfase entre corriente y voltaje, elevando la precisión al nivel de un analizador de red básico.

Esta relación costo-beneficio ($50 MXN de inversión por una mejora cualitativa en la clasificación de la medición) justifica plenamente la decisión de diseño. El prototipo se posiciona como una solución competitiva con una reducción de costo superior al 60% respecto a las alternativas comerciales disponibles en el mercado mexicano, validando la hipótesis específica 4.

[⬆ Volver al inicio](#inicio)

---

## 10. Conclusiones Parciales y Trabajo Futuro

<a name="10-conclusiones-parciales-y-trabajo-futuro"></a>

### 10.1 Conclusiones del Avance

<a name="101-conclusiones-del-avance"></a>

Con base en el avance de investigación documentado hasta esta fase, se establecen las siguientes conclusiones parciales:

1. **Viabilidad técnica demostrada.** El diseño del sistema de monitoreo basado en el ESP32 con sensores SCT-013 y ZMPT101B demuestra que es tecnológicamente factible implementar un dispositivo de medición de potencia activa real con las capacidades de un analizador de red básico, utilizando exclusivamente componentes genéricos de bajo costo disponibles en el mercado nacional.

2. **Precisión dentro de los parámetros objetivo.** Los resultados preliminares reportan un coeficiente de determinación $R^2 > 0.98$ y un error porcentual absoluto medio (MAPE) de $\pm 2.3\%$ para cargas superiores a 200 W, lo que satisface el criterio de aceptación de la hipótesis general (error $< 5\%$). La zona de baja precisión en cargas inferiores a 50 W ($\pm 8.5\%$) ha sido identificada, documentada y declarada como una limitación inherente a la resolución del ADC y al rango del sensor.

3. **Viabilidad económica confirmada.** El costo total de la BOM se estableció en $600.00 MXN por unidad, representando una reducción superior al 60% respecto a las soluciones comerciales equivalentes más económicas del mercado. La incorporación del sensor ZMPT101B por $50 MXN adicionales constituye una inversión marginal con alto retorno en términos de precisión de medición.

4. **Identificación y mitigación de riesgos técnicos.** Las limitaciones del microcontrolador (no linealidad del ADC, conflicto ADC2/WiFi), las restricciones de instalación física (efecto de jaula de Faraday del tablero metálico), las limitaciones del sistema eléctrico mexicano (servicio monofásico exclusivo, ancho de banda de medición) y las contingencias de conectividad (modo híbrido WiFi/microSD) han sido analizadas, documentadas y abordadas con estrategias de mitigación concretas.

5. **Clasificación metodológica consolidada.** La investigación se ha definido formalmente como de tipo aplicada y tecnológica, con enfoque cuantitativo, alcance correlacional-experimental y diseño mixto (laboratorio y campo), proporcionando un marco metodológico sólido para las fases subsecuentes de validación.

[⬆ Volver al inicio](#inicio)

---

### 10.2 Trabajo Futuro

<a name="102-trabajo-futuro"></a>

Las siguientes líneas de desarrollo permanecen abiertas para las fases subsecuentes de la investigación y para futuras iteraciones del proyecto:

1. **Completar las pruebas de campo:** Instalación del prototipo en la vivienda residencial de estudio (Toluca) y ejecución del protocolo de monitoreo continuo de 24 a 72 horas, incluyendo la comparación con el medidor de CFE.

2. **Formalizar el análisis estadístico completo:** Aplicar las pruebas de normalidad (Shapiro-Wilk), prueba t de Student para muestras pareadas, análisis de Bland-Altman y ANOVA de un factor a los datos de campo.

3. **Optimizar el firmware:** Refinar el algoritmo de corrección de linealidad del ADC e implementar técnicas de promediado avanzadas para reducir el error en el rango de cargas bajas.

4. **Mejorar la resolución en cargas bajas:** Evaluar la integración de un ADC externo de 16 bits (ADS1115 u homólogo) como módulo complementario para aplicaciones que requieran precisión en el rango de *standby* ($< 50$ W).

5. **Extensión a servicio bifásico:** Diseñar una variante del sistema con dos canales de corriente y dos canales de voltaje para viviendas con acometida bifásica (220 V).

6. **Implementación de NILM avanzado:** Explorar algoritmos de *Machine Learning* en el borde (*Edge Computing* con TensorFlow Lite en ESP32) para la desagregación de cargas, permitiendo identificar electrodomésticos individuales por su firma eléctrica.

7. **Desarrollo de la interfaz remota:** Implementar el *dashboard* web/app con visualización de históricos, alertas de consumo excesivo y estimación de costos proyectados según la tarifa vigente de CFE.

8. **Validación normativa:** Evaluar la posibilidad de someter el prototipo a pruebas bajo la norma IEC 62053-21 para determinar su clase metrológica formal, como paso previo hacia una eventual certificación y comercialización.

[⬆ Volver al inicio](#inicio)

---

## 11. Referencias Bibliográficas

<a name="11-referencias-bibliográficas"></a>

Alkar, A. Z., & Buhur, U. (2005). An Internet based wireless home automation system for multifunctional devices. *IEEE Transactions on Consumer Electronics*, *51*(4), 1169–1174. https://doi.org/10.1109/TCE.2005.1561840

American Psychological Association. (2020). *Publication manual of the American Psychological Association* (7th ed.). American Psychological Association. https://doi.org/10.1037/0000165-000

Arias, F. G. (2012). *El proyecto de investigación: Introducción a la metodología científica* (6ª ed.). Editorial Episteme.

Ashton, K. (2009). That 'Internet of Things' thing. *RFID Journal*, *22*(7), 97–114.

Comisión Federal de Electricidad. (2024). *Tarifas domésticas de energía eléctrica*. CFE. https://app.cfe.mx/Aplicaciones/CCFE/Tarifas/TarifasCRECasa/Casa.aspx

Creswell, J. W., & Creswell, J. D. (2018). *Research design: Qualitative, quantitative, and mixed methods approaches* (5th ed.). SAGE Publications.

Espressif Systems. (2022). *ESP32 Series Datasheet* (ver. 3.4). Espressif Systems. https://www.espressif.com/sites/default/files/documentation/esp32_datasheet_en.pdf

Hart, D. W. (2011). *Power electronics*. McGraw-Hill Education.

Hart, G. W. (1992). Nonintrusive appliance load monitoring. *Proceedings of the IEEE*, *80*(12), 1870–1891. https://doi.org/10.1109/5.192069

Hernández Sampieri, R., Fernández Collado, C., & Baptista Lucio, M. del P. (2014). *Metodología de la investigación* (6ª ed.). McGraw-Hill Education.

International Electrotechnical Commission. (2003). *IEC 62053-21: Electricity metering equipment — Particular requirements — Part 21: Static meters for active energy (classes 1 and 2)*. IEC.

Liu, Y., Wang, X., & Jian, W. (2021). Design of Smart Home Energy Management System Based on ESP32. En *Proceedings of the International Conference on Electronic Information Technology* (pp. 112–117). IEEE. https://doi.org/10.1109/ICEIT51700.2021.9375653

Naciones Unidas. (2015). *Transformar nuestro mundo: La Agenda 2030 para el Desarrollo Sostenible*. Asamblea General de las Naciones Unidas. https://sdgs.un.org/2030agenda

Norma Oficial Mexicana NOM-001-SEDE-2012. (2012). *Instalaciones Eléctricas (Utilización)*. Diario Oficial de la Federación, México.

Norma Oficial Mexicana NOM-003-SCFI-2014. (2014). *Productos eléctricos — Requisitos de seguridad*. Diario Oficial de la Federación, México.

OASIS. (2019). *MQTT Version 5.0* (OASIS Standard). OASIS Open. https://docs.oasis-open.org/mqtt/mqtt/v5.0/mqtt-v5.0.html

Oppenheim, A. V., & Willsky, A. S. (2014). *Signals and systems* (2nd ed.). Pearson Education.

[⬆ Volver al inicio](#inicio)
