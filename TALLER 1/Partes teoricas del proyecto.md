<!--
===================================================================
METADATOS DEL DOCUMENTO
===================================================================
Proyecto    : Diseño e Implementación de un Sistema IoT de Bajo
              Costo para la Monitorización No Intrusiva de Consumo
              Eléctrico Residencial mediante Arquitectura ESP32
Área        : Ingeniería Electrónica / Investigación Académica
-------------------------------------------------------------------
Archivo     : TALLER 1/Partes teoricas del proyecto.md
Tipo        : Guía teórica-metodológica (meta-documento)
Descripción : Documento de referencia que describe QUÉ debe
              contener cada sección de una investigación
              académica del tipo aplicada-tecnológica,
              cuantitativa, correlacional-experimental y de
              diseño mixto. No contiene datos del proyecto en
              sí, sino la teoría sobre cómo redactar cada
              apartado (portada, resumen, marco teórico,
              metodología, resultados, etc.).
Autor       : Generado por IA como material de apoyo
Creado      : 2026-02-28
Últ. mod.   : 2026-02-28
Etapa       : Taller de Investigación 1 – Fundamentación teórica
Estado      : VIGENTE – Documento de consulta permanente
Notas       : Este archivo NO contiene contenido del proyecto;
              es una guía estructural. No mezclar sus
              instrucciones genéricas con los datos específicos
              del prototipo ESP32.
===================================================================
-->

# Partes Teóricas del Proyecto de Investigación

<a name="inicio"></a>

> **Propósito de este documento:** Servir como guía teórica y metodológica que describe qué debe contener cada sección de una investigación académica del tipo **aplicada-tecnológica, cuantitativa, correlacional-experimental y de diseño mixto (laboratorio y campo)**, correspondiente al proyecto *"Diseño e Implementación de un Sistema IoT de Bajo Costo para la Monitorización No Intrusiva de Consumo Eléctrico Residencial mediante Arquitectura ESP32"*.

---

## Índice General

1. [Portada y Datos de Identificación](#1-portada-y-datos-de-identificación)
2. [Resumen / Abstract](#2-resumen--abstract)
3. [Introducción](#3-introducción)
   - 3.1 [Contextualización del Tema](#31-contextualización-del-tema)
   - 3.2 [Planteamiento del Problema](#32-planteamiento-del-problema)
   - 3.3 [Pregunta de Investigación](#33-pregunta-de-investigación)
   - 3.4 [Justificación](#34-justificación)
   - 3.5 [Delimitaciones y Alcances](#35-delimitaciones-y-alcances)
4. [Objetivos de la Investigación](#4-objetivos-de-la-investigación)
   - 4.1 [Objetivo General](#41-objetivo-general)
   - 4.2 [Objetivos Específicos](#42-objetivos-específicos)
5. [Hipótesis](#5-hipótesis)
   - 5.1 [Hipótesis General](#51-hipótesis-general)
   - 5.2 [Hipótesis Específicas u Operacionales](#52-hipótesis-específicas-u-operacionales)
6. [Marco Teórico](#6-marco-teórico)
   - 6.1 [Antecedentes de la Investigación](#61-antecedentes-de-la-investigación)
   - 6.2 [Bases Teóricas](#62-bases-teóricas)
   - 6.3 [Estado del Arte](#63-estado-del-arte)
   - 6.4 [Marco Conceptual (Glosario Técnico)](#64-marco-conceptual-glosario-técnico)
   - 6.5 [Marco Legal y Normativo](#65-marco-legal-y-normativo)
7. [Marco Metodológico](#7-marco-metodológico)
   - 7.1 [Tipo y Diseño de Investigación](#71-tipo-y-diseño-de-investigación)
   - 7.2 [Operacionalización de Variables](#72-operacionalización-de-variables)
   - 7.3 [Población y Muestra](#73-población-y-muestra)
   - 7.4 [Técnicas e Instrumentos de Recolección de Datos](#74-técnicas-e-instrumentos-de-recolección-de-datos)
   - 7.5 [Procedimiento Experimental](#75-procedimiento-experimental)
   - 7.6 [Técnicas de Procesamiento y Análisis de Datos](#76-técnicas-de-procesamiento-y-análisis-de-datos)
   - 7.7 [Criterios de Validez y Confiabilidad](#77-criterios-de-validez-y-confiabilidad)
8. [Diseño e Implementación del Sistema](#8-diseño-e-implementación-del-sistema)
   - 8.1 [Arquitectura General del Sistema](#81-arquitectura-general-del-sistema)
   - 8.2 [Diseño del Hardware](#82-diseño-del-hardware)
   - 8.3 [Diseño del Firmware / Software](#83-diseño-del-firmware--software)
   - 8.4 [Integración y Ensamblaje](#84-integración-y-ensamblaje)
   - 8.5 [Análisis de Costos (BOM)](#85-análisis-de-costos-bom)
9. [Resultados y Discusión](#9-resultados-y-discusión)
   - 9.1 [Presentación de Resultados](#91-presentación-de-resultados)
   - 9.2 [Análisis Estadístico](#92-análisis-estadístico)
   - 9.3 [Discusión e Interpretación](#93-discusión-e-interpretación)
   - 9.4 [Comparación con el Estado del Arte](#94-comparación-con-el-estado-del-arte)
10. [Conclusiones y Recomendaciones](#10-conclusiones-y-recomendaciones)
    - 10.1 [Conclusiones](#101-conclusiones)
    - 10.2 [Recomendaciones](#102-recomendaciones)
    - 10.3 [Trabajo Futuro](#103-trabajo-futuro)
11. [Referencias Bibliográficas](#11-referencias-bibliográficas)
12. [Anexos](#12-anexos)

---

## 1. Portada y Datos de Identificación

<a name="1-portada-y-datos-de-identificación"></a>

La portada es la primera página del documento y cumple una función identificadora institucional. Aunque no forma parte del cuerpo argumentativo, su correcta elaboración es un requisito formal obligatorio en toda investigación académica.

### ¿Qué debe contener?

| Elemento | Descripción |
|---|---|
| **Logo institucional** | Escudo o logotipo de la universidad en la parte superior. |
| **Nombre de la institución** | Nombre completo de la universidad, facultad o departamento. |
| **Título del trabajo** | Debe ser descriptivo, conciso y reflejar fielmente el contenido. En investigación aplicada tecnológica, se recomienda incluir el *qué* (sistema IoT), el *cómo* (ESP32, sensores no intrusivos) y el *para qué* (monitorización de consumo eléctrico residencial). |
| **Modalidad del trabajo** | Tesis, tesina, reporte técnico, proyecto de investigación, etc. |
| **Nombre del autor** | Nombre completo del o los investigadores. |
| **Nombre del asesor(es)** | Director de tesis o asesor técnico. |
| **Lugar y fecha** | Ciudad y fecha de presentación. |

### Teoría aplicada al proyecto

En proyectos de ingeniería aplicada, el título debe evitar la ambigüedad. Hernández Sampieri et al. (2014) recomiendan que un buen título no exceda las 20 palabras e incluya las variables principales del estudio. Para este proyecto, el título *"Diseño e Implementación de un Sistema IoT de Bajo Costo para la Monitorización No Intrusiva de Consumo Eléctrico Residencial mediante Arquitectura ESP32"* cumple con este criterio al especificar la acción (diseño e implementación), el objeto (sistema IoT), la cualidad diferenciadora (bajo costo, no intrusivo) y el medio tecnológico (ESP32).

[⬆ Volver al inicio](#inicio)

---

## 2. Resumen / Abstract

<a name="2-resumen--abstract"></a>

El resumen es una síntesis completa y autónoma del trabajo de investigación. Su función es permitir al lector determinar rápidamente la relevancia del documento sin necesidad de leerlo en su totalidad. Es, con frecuencia, la primera —y a veces única— sección que consultan los revisores, jurados y bases de datos académicas.

### ¿Qué debe contener?

Según las normas APA 7ª edición (American Psychological Association, 2020) y la norma ISO 214:1976 para resúmenes, un resumen académico debe incluir los siguientes elementos en un solo párrafo de entre **150 y 300 palabras**:

1. **Problema de investigación:** Una o dos oraciones que establezcan el contexto y la problemática.
2. **Objetivo:** Declaración clara del propósito del estudio.
3. **Metodología:** Breve descripción del enfoque, tipo de investigación, instrumentos y procedimiento.
4. **Resultados principales:** Los hallazgos más significativos expresados con datos cuantitativos cuando sea posible.
5. **Conclusión:** Implicación o aporte principal del trabajo.
6. **Palabras clave:** De 4 a 6 términos normalizados que faciliten la indexación del documento en bases de datos (IEEE Xplore, Scopus, Google Scholar).

### Características esenciales

- **Autonomía:** Debe comprenderse sin necesidad de leer el documento completo.
- **Precisión:** Debe reflejar fielmente el contenido, sin añadir información que no aparezca en el cuerpo del trabajo.
- **Concisión:** Evitar redundancias, adjetivos innecesarios y citas bibliográficas.
- **No evaluativo:** No debe contener juicios de valor ni opiniones subjetivas del autor.

### Teoría aplicada al proyecto

Para una investigación aplicada-tecnológica cuantitativa como la de este proyecto, el resumen debe enfatizar las métricas de validación. Por ejemplo, es indispensable mencionar el error porcentual ($E_{\%}$) obtenido, el coeficiente de determinación ($R^2$), el costo del prototipo y la comparación con soluciones comerciales. Esto permite al lector evaluar de inmediato la contribución técnica del trabajo.

El **abstract** es la traducción fiel del resumen al idioma inglés y debe acompañar al documento cuando la institución así lo requiera o cuando se busque visibilidad internacional.

[⬆ Volver al inicio](#inicio)

---

## 3. Introducción

<a name="3-introducción"></a>

La introducción es el capítulo que conduce al lector desde el panorama general del tema hasta el problema específico que se pretende resolver. Según Creswell y Creswell (2018), una buena introducción funciona como un "embudo": parte de lo amplio (contexto mundial o nacional) y progresivamente se estrecha hasta llegar al vacío de conocimiento o necesidad práctica que justifica la investigación.

### Estructura recomendada para investigación aplicada-tecnológica

---

### 3.1 Contextualización del Tema

<a name="31-contextualización-del-tema"></a>

#### ¿Qué debe contener?

Esta subsección establece el escenario general en el que se inscribe la investigación. Se presenta el estado actual del campo de conocimiento, las tendencias tecnológicas relevantes y la situación socioeconómica que da origen a la necesidad del proyecto.

#### Elementos clave

- **Contexto global:** Tendencias mundiales en Smart Grids, eficiencia energética y metas de desarrollo sustentable (ODS 7 y ODS 12 de la ONU).
- **Contexto nacional:** Situación del sector eléctrico mexicano, rol de la CFE, estructura tarifaria (1, 1A, 1B, 1C, DAC), nivel de penetración de tecnologías de medición inteligente en viviendas.
- **Contexto local:** Condiciones de la infraestructura eléctrica residencial en la zona de estudio (Toluca, Estado de México).
- **Contexto tecnológico:** Evolución del Internet de las Cosas (IoT), disponibilidad de microcontroladores de bajo costo (ESP32, ESP8266), madurez de los sensores de corriente no intrusivos.

#### Teoría aplicada al proyecto

En investigaciones cuantitativas de enfoque aplicado, el contexto debe incluir datos duros y estadísticas oficiales. Para este proyecto, es pertinente citar la Encuesta Nacional sobre Consumo de Energéticos en Viviendas Particulares (ENCEVI 2018) del INEGI y los informes anuales de la SENER sobre el balance de energía eléctrica en el sector residencial. Estos datos permiten dimensionar la magnitud del problema y sustentar la pertinencia del proyecto con evidencia cuantificable.

[⬆ Volver al inicio](#inicio)

---

### 3.2 Planteamiento del Problema

<a name="32-planteamiento-del-problema"></a>

#### ¿Qué debe contener?

El planteamiento del problema es, según Hernández Sampieri et al. (2014), el **corazón de la investigación**. Debe describir con claridad y exactitud la situación problemática, identificar sus causas y efectos, y demostrar que existe una brecha o necesidad no satisfecha que la investigación pretende abordar.

#### Elementos que debe incluir

1. **Descripción del fenómeno problemático:** ¿Qué está sucediendo que represente un problema? Para proyectos de ingeniería, se describe la falla, carencia o ineficiencia que se observa en un sistema real.
2. **Causas identificadas:** ¿Qué factores originan el problema? Se deben enumerar con sustento (no especular).
3. **Consecuencias o efectos:** ¿Qué impacto genera el problema si no se interviene? Consecuencias económicas, ambientales, sociales o técnicas.
4. **Evidencia del problema:** Datos, estadísticas o referencias que demuestren que el problema es real y vigente.
5. **Brecha de conocimiento o tecnológica:** ¿Qué es lo que aún no se ha resuelto o no existe en el mercado/literatura?

#### Técnica de formulación

Kerlinger y Lee (2002) establecen tres criterios para un buen planteamiento del problema:

1. Debe expresar una **relación entre dos o más variables**.
2. Debe formularse de manera **clara y sin ambigüedad**, preferentemente como pregunta.
3. Debe implicar la **posibilidad de realizar una prueba empírica**.

#### Teoría aplicada al proyecto

El problema de este proyecto cumple los tres criterios: establece una relación entre *variables de consumo eléctrico medidas por el prototipo* (Variable A) y *valores de referencia obtenidos por instrumentación certificada* (Variable B); se formula como una pregunta de factibilidad técnico-económica; y es verificable mediante experimentación cuantitativa en laboratorio y campo.

Las causas específicas del problema incluyen: (a) la opacidad de los medidores fiscales de CFE, (b) el alto costo de las soluciones comerciales de monitoreo, (c) la complejidad de instalación de dispositivos intrusivos, y (d) las fluctuaciones de la red eléctrica mexicana que invalidan estimaciones simples basadas únicamente en corriente.

[⬆ Volver al inicio](#inicio)

---

### 3.3 Pregunta de Investigación

<a name="33-pregunta-de-investigación"></a>

#### ¿Qué debe contener?

La pregunta de investigación es la formulación interrogativa y precisa del problema. Según Creswell y Creswell (2018), debe cumplir con los siguientes atributos:

- Ser **específica** (no genérica ni filosófica).
- Ser **medible** (contener variables cuantificables).
- Ser **alcanzable** (posible de responder con los recursos y el tiempo disponibles).
- Estar **delimitada** temporal y espacialmente.

#### Tipos de preguntas según el alcance

| Alcance | Ejemplo de pregunta |
|---|---|
| **Descriptivo** | ¿Cuál es el patrón de consumo eléctrico promedio de una vivienda de clase media en Toluca? |
| **Correlacional** | ¿Existe correlación significativa entre las mediciones del prototipo y las de un instrumento patrón? |
| **Explicativo** | ¿Cómo influye la resolución del ADC del ESP32 en la precisión de la medición de corrientes bajas? |
| **Experimental** | ¿Es factible obtener un error de medición inferior al 5% mediante un sistema basado en ESP32 y sensores no intrusivos? |

#### Teoría aplicada al proyecto

Dado que la investigación es de alcance **correlacional y experimental**, la pregunta central debe integrar ambos niveles. La formulación del proyecto es: *"¿Es factible desarrollar e implementar un sistema de monitoreo eléctrico residencial IoT que, mediante la medición simultánea de voltaje y corriente, reduzca el costo de adquisición en un 60% respecto a analizadores de red comerciales, garantizando una precisión superior al 95%?"*. Esta pregunta contiene variables cuantificables (costo, precisión), un criterio de éxito numérico (60%, 95%) y una delimitación implícita (residencial, IoT, voltaje y corriente simultáneos).

[⬆ Volver al inicio](#inicio)

---

### 3.4 Justificación

<a name="34-justificación"></a>

#### ¿Qué debe contener?

La justificación responde a la pregunta: *¿Por qué es necesaria esta investigación?* Hernández Sampieri et al. (2014) proponen evaluar la investigación bajo cinco criterios:

1. **Conveniencia:** ¿Para qué sirve? ¿Qué problema práctico resuelve?
2. **Relevancia social:** ¿Quiénes se benefician y de qué manera?
3. **Implicaciones prácticas:** ¿Ayuda a resolver un problema real y tangible?
4. **Valor teórico:** ¿Aporta conocimiento nuevo, llena un vacío o contribuye a una teoría existente?
5. **Utilidad metodológica:** ¿Propone un nuevo instrumento, método o enfoque replicable?

#### Teoría aplicada al proyecto

| Criterio | Aplicación al proyecto |
|---|---|
| **Conveniencia** | Proporciona una herramienta de diagnóstico energético accesible para hogares mexicanos. |
| **Relevancia social** | Beneficia a familias de clase media al evitar la tarifa DAC y reducir el gasto eléctrico. |
| **Implicaciones prácticas** | Resuelve el problema de invisibilidad del consumo eléctrico con un dispositivo funcional y de bajo costo (~$600 MXN). |
| **Valor teórico** | Valida la aplicabilidad de la Ley de Faraday y algoritmos de DSP en hardware de consumo masivo con restricciones de costo. |
| **Utilidad metodológica** | Propone un protocolo de calibración replicable para sensores SCT-013 con ADCs de baja resolución, útil para futuros proyectos de instrumentación de bajo costo. |

[⬆ Volver al inicio](#inicio)

---

### 3.5 Delimitaciones y Alcances

<a name="35-delimitaciones-y-alcances"></a>

#### ¿Qué debe contener?

Las delimitaciones establecen las fronteras del estudio. Según Arias (2012), delimitar la investigación implica definir con exactitud:

- **Delimitación temática:** ¿Qué aspectos abarca y cuáles quedan fuera?
- **Delimitación espacial:** ¿Dónde se realiza el estudio?
- **Delimitación temporal:** ¿En qué periodo se ejecuta?
- **Delimitación poblacional:** ¿A quién se dirige?
- **Delimitación tecnológica:** En proyectos de ingeniería, ¿qué restricciones imponen los componentes seleccionados?

Es igualmente importante distinguir entre **delimitaciones** (decisiones voluntarias del investigador para acotar el estudio) y **limitaciones** (restricciones involuntarias del entorno, los recursos o la tecnología).

#### Teoría aplicada al proyecto

Las delimitaciones específicas de este proyecto, derivadas del análisis técnico, son:

| Tipo | Delimitación |
|---|---|
| **Temática** | Monitoreo de consumo eléctrico residencial; no se abarca generación distribuida (paneles solares) ni balanceo de carga industrial. |
| **Espacial** | Vivienda unifamiliar con servicio monofásico (127V) en Toluca, Estado de México. |
| **Temporal** | Ciclo de desarrollo y validación durante el periodo académico vigente. |
| **Tecnológica** | Precisión limitada a corrientes > 0.2 A (~25 W) por la zona muerta del ADC del ESP32; requiere señal WiFi 2.4 GHz; excluye sistemas bifásicos (220 V). |
| **Económica** | Presupuesto de materiales acotado a ~$600 MXN por unidad. |

Las **limitaciones** técnicas incluyen la no linealidad del ADC del ESP32, la interferencia electromagnética de la caja metálica del tablero eléctrico y el conflicto ADC2/WiFi documentado por Espressif Systems (2022).

[⬆ Volver al inicio](#inicio)

---

## 4. Objetivos de la Investigación

<a name="4-objetivos-de-la-investigación"></a>

Los objetivos representan las metas concretas que el investigador se propone alcanzar. Son la traducción operativa del problema y la hipótesis en acciones verificables. Según Arias (2012), los objetivos responden a la pregunta *"¿Qué se pretende lograr?"* y deben redactarse iniciando con un **verbo en infinitivo** de la taxonomía de Bloom (conocer, analizar, diseñar, implementar, evaluar, etc.).

### Características de un buen objetivo

- **Claro:** Sin ambigüedades ni tecnicismos innecesarios.
- **Medible:** Debe poder determinarse si se cumplió o no al finalizar la investigación.
- **Alcanzable:** Factible con los recursos, el tiempo y la tecnología disponibles.
- **Relevante:** Directamente vinculado al problema planteado.
- **Temporal:** Acotado al periodo de la investigación.

Estos criterios corresponden al modelo **SMART** (Specific, Measurable, Achievable, Relevant, Time-bound) ampliamente utilizado en gestión de proyectos (Doran, 1981).

---

### 4.1 Objetivo General

<a name="41-objetivo-general"></a>

#### ¿Qué debe contener?

El objetivo general expresa el propósito central y global de la investigación. Debe estar alineado directamente con la pregunta de investigación y formular de manera sintética lo que se espera lograr al concluir el estudio. Solo debe haber **uno**.

#### Verbos recomendados para investigación aplicada-tecnológica

`Diseñar`, `Desarrollar`, `Implementar`, `Construir`, `Validar`, `Evaluar`.

#### Teoría aplicada al proyecto

> *Diseñar, implementar y validar un sistema de monitoreo eléctrico residencial de bajo costo y no intrusivo, basado en la plataforma ESP32 y sensores de corriente tipo clamp, capaz de medir potencia activa en tiempo real con un error inferior al 5% respecto a instrumentación de referencia.*

Este objetivo integra el *qué* (sistema de monitoreo), el *cómo* (ESP32, sensores clamp) y el *criterio de éxito* (error < 5%), cumpliendo con los requisitos de especificidad y medibilidad.

[⬆ Volver al inicio](#inicio)

---

### 4.2 Objetivos Específicos

<a name="42-objetivos-específicos"></a>

#### ¿Qué debe contener?

Los objetivos específicos desglosan el objetivo general en **pasos operativos secuenciales**. Cada objetivo específico debe ser una etapa verificable que, en conjunto, permita alcanzar el objetivo general. Hernández Sampieri et al. (2014) recomiendan entre 3 y 6 objetivos específicos.

#### Reglas de redacción

1. Cada objetivo inicia con un **verbo en infinitivo diferente** (evitar repetir).
2. Deben seguir un **orden lógico o cronológico**.
3. Cada uno debe ser **medible de forma independiente**.
4. No deben ser actividades operativas ("comprar componentes"), sino metas de conocimiento o producto ("diseñar el circuito de acondicionamiento de señal").

#### Teoría aplicada al proyecto

Para este tipo de investigación (aplicada-tecnológica con prototipo funcional), los objetivos específicos típicos siguen la secuencia de un ciclo de ingeniería:

1. **Analizar** los requerimientos funcionales y no funcionales del sistema de monitoreo con base en las condiciones del sector eléctrico residencial mexicano.
2. **Diseñar** la etapa de hardware: circuito de acondicionamiento de señal para los sensores SCT-013 y ZMPT101B, y sistema de alimentación conmutada integrado.
3. **Desarrollar** el firmware de adquisición de datos, procesamiento digital de señales (cálculo de $I_{RMS}$, $V_{RMS}$ y $P$) y transmisión inalámbrica.
4. **Implementar** la interfaz de usuario local (OLED) y remota (plataforma web/app) para la visualización de métricas.
5. **Validar** el desempeño del prototipo mediante pruebas comparativas contra instrumentación patrón en condiciones de laboratorio y campo.
6. **Evaluar** la viabilidad económica del dispositivo mediante análisis de la lista de materiales (BOM) frente a soluciones comerciales del mercado.

[⬆ Volver al inicio](#inicio)

---

## 5. Hipótesis

<a name="5-hipótesis"></a>

La hipótesis es una proposición tentativa que establece una relación entre variables y que se somete a verificación empírica. En investigaciones cuantitativas experimentales, la hipótesis es un componente obligatorio (Hernández Sampieri et al., 2014). Es la respuesta provisional a la pregunta de investigación.

### Tipos de hipótesis

| Tipo | Descripción | Ejemplo en el proyecto |
|---|---|---|
| **De investigación ($H_i$)** | Proposición afirmativa que se espera demostrar. | El prototipo basado en ESP32 mide potencia activa con un error ≤ 5% respecto al instrumento patrón. |
| **Nula ($H_0$)** | Negación de la hipótesis de investigación; es la que se busca rechazar estadísticamente. | No existe diferencia significativa entre las mediciones del prototipo y el instrumento patrón (o bien: el error supera el 5%). |
| **Alternativa ($H_a$)** | Ofrece una explicación diferente a $H_0$ y $H_i$. | La precisión del prototipo varía significativamente según el tipo de carga (resistiva vs. inductiva). |

---

### 5.1 Hipótesis General

<a name="51-hipótesis-general"></a>

#### ¿Qué debe contener?

Una sola proposición que vincule las variables principales y establezca un criterio cuantitativo de verificación. En investigación experimental, la hipótesis debe ser **falsificable** (Popper, 1959): debe existir un resultado posible que la niegue.

#### Teoría aplicada al proyecto

> $H_i$: *Es factible desarrollar un sistema de monitoreo eléctrico basado en IoT que, mediante hardware de código abierto y componentes genéricos optimizados, reduzca los costos de manufactura por debajo de los $600 MXN por unidad, manteniendo un error de medición inferior al 5% en cargas domésticas estándar.*

> $H_0$: *El sistema propuesto no alcanza la precisión requerida (error > 5%) o su costo de manufactura excede los $600 MXN, invalidando la viabilidad técnico-económica.*

---

### 5.2 Hipótesis Específicas u Operacionales

<a name="52-hipótesis-específicas-u-operacionales"></a>

#### ¿Qué debe contener?

Hipótesis derivadas que permiten descomponer la hipótesis general en afirmaciones verificables de forma independiente. Cada una debe corresponder a un objetivo específico y a una variable del estudio.

#### Teoría aplicada al proyecto

1. El sensor SCT-013-030 acondicionado con circuito de offset a 1.65 V produce una señal proporcional lineal ($R^2 > 0.98$) a la corriente real en el rango de 0.5 A a 30 A.
2. La fuente conmutada integrada tipo Hi-Link proporciona una alimentación estable de 5 V DC con un rizado inferior a 50 mV, sin introducir ruido significativo en las mediciones del ADC.
3. La medición simultánea de voltaje (ZMPT101B) y corriente (SCT-013) permite calcular la potencia activa con mayor precisión que la estimación basada únicamente en corriente y voltaje nominal asumido.
4. El costo total de materiales (BOM) no excede los $600 MXN, posicionando al dispositivo al menos un 60% por debajo del precio de mercado de soluciones comerciales equivalentes.

[⬆ Volver al inicio](#inicio)

---

## 6. Marco Teórico

<a name="6-marco-teórico"></a>

El marco teórico es la **fundamentación conceptual y científica** de la investigación. Su función es contextualizar el estudio dentro del cuerpo de conocimiento existente, proporcionar las bases para interpretar los resultados y demostrar que el investigador domina el campo. Según Hernández Sampieri et al. (2014), el marco teórico cumple seis funciones:

1. Prevenir errores cometidos en estudios anteriores.
2. Orientar el estudio, evitando desviaciones del tema central.
3. Centrar el problema de investigación e impedir divagaciones.
4. Documentar la necesidad de realizar el estudio.
5. Establecer hipótesis basadas en evidencia.
6. Proveer un marco de referencia para interpretar los resultados.

Para una investigación aplicada-tecnológica, el marco teórico se construye con una combinación de **teorías fundamentales** (electromagnetismo, procesamiento de señales) y **conocimiento técnico aplicado** (arquitectura de microcontroladores, protocolos IoT).

---

### 6.1 Antecedentes de la Investigación

<a name="61-antecedentes-de-la-investigación"></a>

#### ¿Qué debe contener?

Los antecedentes son una revisión cronológica y crítica de investigaciones previas directamente relacionadas con el tema. No es un listado de resúmenes; cada antecedente debe analizarse indicando:

- **Referencia completa** (autor, año, título).
- **Objetivo** del estudio referenciado.
- **Metodología** empleada.
- **Resultados principales.**
- **Relación con el proyecto actual:** ¿En qué se asemeja? ¿En qué difiere? ¿Qué vacío deja que esta investigación pretende cubrir?

#### Criterios de selección de antecedentes

- **Temporalidad:** Priorizar estudios de los últimos 5-10 años (2016-2026), salvo obras seminales clásicas.
- **Pertinencia:** Deben abordar al menos una variable en común con el proyecto (monitoreo eléctrico, IoT, ESP32, sensores no intrusivos, eficiencia energética residencial).
- **Calidad:** Preferir fuentes arbitradas (journals IEEE, Elsevier, Springer) sobre blogs o foros.
- **Cantidad:** Se recomiendan entre 5 y 15 antecedentes para una tesis de ingeniería a nivel licenciatura.

#### Teoría aplicada al proyecto

Los antecedentes para este proyecto deben incluir trabajos sobre: (a) sistemas de monitoreo de energía basados en microcontroladores como Arduino y ESP32, (b) técnicas de medición no intrusiva de carga (NILM), (c) implementaciones de IoT en Smart Grids residenciales, y (d) estudios de viabilidad económica de soluciones de medición de bajo costo. Se deben identificar las limitaciones de cada antecedente (por ejemplo: uso exclusivo de corriente sin medición de voltaje, falta de validación en campo, costos no optimizados) para justificar la contribución diferencial de este proyecto.

[⬆ Volver al inicio](#inicio)

---

### 6.2 Bases Teóricas

<a name="62-bases-teóricas"></a>

#### ¿Qué debe contener?

Las bases teóricas constituyen el fundamento científico y de ingeniería que sustenta el diseño del sistema. Cada concepto teórico citado debe vincularse explícitamente con una decisión de diseño o una etapa del proyecto. No se trata de copiar definiciones de libros, sino de construir un argumento teórico que justifique las decisiones técnicas.

#### Temas fundamentales para este tipo de investigación

**A. Electromagnetismo y Principios de Medición**
- **Ley de Faraday de la Inducción Electromagnética:** Fundamento del funcionamiento de los transformadores de corriente (CT). La fem inducida en el secundario es proporcional a la variación temporal del flujo magnético, lo que permite medir corriente sin contacto galvánico.
- **Corriente Eficaz ($I_{RMS}$):** Valor equivalente de corriente continua que disipa la misma potencia en una resistencia. Definida como:

$$I_{RMS} = \sqrt{\frac{1}{T} \int_{0}^{T} i(t)^2 \, dt}$$

- **Potencia Eléctrica en CA:** Diferenciación rigurosa entre potencia aparente ($S$), potencia activa ($P$) y potencia reactiva ($Q$), y su representación en el triángulo de potencias:

$$S = V_{RMS} \cdot I_{RMS}$$

$$P = V_{RMS} \cdot I_{RMS} \cdot \cos(\phi)$$

$$Q = V_{RMS} \cdot I_{RMS} \cdot \sin(\phi)$$

Donde $\phi$ es el ángulo de desfase entre voltaje y corriente (factor de potencia).

**B. Teoría de Muestreo y Procesamiento Digital de Señales (DSP)**
- **Teorema de Nyquist-Shannon:** Para reconstruir fielmente una señal analógica, la frecuencia de muestreo ($f_s$) debe ser al menos el doble de la frecuencia máxima de la señal ($f_{max}$):

$$f_s \geq 2 \cdot f_{max}$$

Para señales de la red eléctrica a 60 Hz (México), $f_s \geq 120$ Hz como mínimo, aunque en la práctica se usan tasas mucho mayores para capturar armónicos y mejorar la resolución del cálculo RMS.

- **Conversión Analógico-Digital (ADC):** Teoría de cuantización, resolución en bits (el ESP32 utiliza ADC de 12 bits, lo que ofrece $2^{12} = 4096$ niveles de cuantización), ruido de cuantización y su impacto en la relación señal a ruido (SNR).

**C. Sistemas Embebidos y Microcontroladores**
- Arquitectura del ESP32: doble núcleo Xtensa® LX6, frecuencia de reloj, periféricos integrados (ADC, DAC, SPI, I2C, UART), módulo WiFi 802.11 b/g/n y Bluetooth.
- Restricciones de tiempo real: concepto de *bare metal* vs. RTOS (FreeRTOS integrado en el ESP32), gestión de interrupciones para muestreo periódico.

**D. Internet de las Cosas (IoT)**
- Modelo de arquitectura IoT en capas: percepción (sensores), red (comunicación), aplicación (interfaz de usuario).
- Protocolos de comunicación relevantes: TCP/IP, HTTP, MQTT (Message Queuing Telemetry Transport), y su idoneidad para transmisión de datos desde dispositivos con recursos limitados.

**E. Fuentes de Alimentación Conmutadas (SMPS)**
- Principio de operación de un convertidor *buck* AC-DC: rectificación, regulación por conmutación de alta frecuencia, filtrado. Ventajas sobre fuentes lineales: eficiencia, compacidad y disipación térmica reducida.

[⬆ Volver al inicio](#inicio)

---

### 6.3 Estado del Arte

<a name="63-estado-del-arte"></a>

#### ¿Qué debe contener?

El estado del arte es una revisión actualizada de las **soluciones tecnológicas existentes** (tanto académicas como comerciales) que abordan el mismo problema o uno similar. A diferencia de los antecedentes (que se centran en investigaciones previas), el estado del arte incluye productos de mercado, patentes y tendencias tecnológicas vigentes.

#### Estructura recomendada

1. **Soluciones comerciales:** Análisis de productos disponibles en el mercado (Sense, Emporia Vue, Shelly EM, TP-Link Kasa), incluyendo sus especificaciones, precios y limitaciones de acceso para el mercado mexicano.
2. **Soluciones académicas/Open Source:** Proyectos como OpenEnergyMonitor (emonPi, emonTx), que representan la línea de hardware abierto para monitoreo de energía.
3. **Tabla comparativa:** Matriz que contraste las soluciones existentes con el prototipo propuesto en dimensiones como costo, precisión, tipo de instalación (intrusiva/no intrusiva), conectividad y funcionalidades.
4. **Identificación del nicho:** Conclusión que demuestre que ninguna solución existente satisface simultáneamente los requisitos de bajo costo, no intrusividad, medición de potencia activa real y accesibilidad para el contexto mexicano.

#### Teoría aplicada al proyecto

El estado del arte de este proyecto debe demostrar que, aunque existen soluciones de monitoreo energético (tanto comerciales como de código abierto), ninguna optimiza simultáneamente las tres dimensiones clave para el mercado residencial mexicano: (1) costo inferior a $600 MXN, (2) instalación completamente no intrusiva, y (3) medición de potencia activa real (no estimada con voltaje nominal). Esta "triple brecha" justifica la contribución técnica del proyecto.

[⬆ Volver al inicio](#inicio)

---

### 6.4 Marco Conceptual (Glosario Técnico)

<a name="64-marco-conceptual-glosario-técnico"></a>

#### ¿Qué debe contener?

El marco conceptual define los términos técnicos clave utilizados a lo largo de la investigación para garantizar una interpretación unívoca. Es especialmente relevante en proyectos interdisciplinarios (electrónica, telecomunicaciones, programación) donde un mismo término puede tener significados diferentes según el contexto.

#### Ejemplo de estructura

Cada término debe presentarse con:
- **Definición formal** (citada de una fuente reconocida).
- **Aplicación en el proyecto** (cómo se utiliza concretamente).

#### Términos imprescindibles para este proyecto

| Término | Definición breve |
|---|---|
| **IoT (Internet of Things)** | Red de objetos físicos con sensores y conectividad que permiten el intercambio de datos. |
| **NILM (Non-Intrusive Load Monitoring)** | Técnica de monitoreo de carga eléctrica sin alterar físicamente la instalación. |
| **SCT-013** | Transformador de corriente de núcleo partido para medición no intrusiva. |
| **ADC (Analog-to-Digital Converter)** | Dispositivo que convierte señales analógicas en valores digitales discretos. |
| **$I_{RMS}$** | Corriente eficaz; valor equivalente de CD que produce la misma disipación de potencia. |
| **SMPS (Switched-Mode Power Supply)** | Fuente de alimentación conmutada de alta eficiencia. |
| **Factor de Potencia ($\cos\phi$)** | Relación entre potencia activa y potencia aparente; mide la eficiencia del uso de la energía. |
| **Tarifa DAC** | Tarifa Doméstica de Alto Consumo de CFE que se aplica cuando se supera el límite subsidiado. |
| **MQTT** | Protocolo ligero de mensajería para dispositivos IoT con ancho de banda limitado. |
| **BOM (Bill of Materials)** | Lista detallada de componentes y costos necesarios para fabricar un producto. |

[⬆ Volver al inicio](#inicio)

---

### 6.5 Marco Legal y Normativo

<a name="65-marco-legal-y-normativo"></a>

#### ¿Qué debe contener?

Toda investigación que involucre sistemas eléctricos, dispositivos electrónicos o procesamiento de datos personales debe identificar el marco regulatorio aplicable. Esto demuestra que el proyecto se desarrolla dentro de la legalidad y cumple estándares de seguridad.

#### Normativas relevantes para este proyecto

| Norma / Ley | Ámbito | Relevancia |
|---|---|---|
| **NOM-001-SEDE-2012** | Instalaciones eléctricas (utilización) | Define los requisitos de seguridad para toda instalación eléctrica en México, incluyendo las limitaciones para intervención en tableros residenciales. |
| **NOM-003-SCFI-2014** | Seguridad de productos eléctricos | Establece los requisitos de seguridad que deben cumplir aparatos eléctricos de uso doméstico. |
| **NMX-J-098-ANCE** | Transformadores de instrumento | Aplica a los transformadores de corriente utilizados en medición eléctrica. |
| **IEC 62053-21** | Equipos de medida de energía eléctrica | Requisitos para medidores estáticos de energía activa (clases 1 y 2). |
| **Ley Federal de Protección de Datos Personales en Posesión de Particulares (LFPDPPP)** | Privacidad | Si el sistema almacena o transmite datos de consumo vinculados a un domicilio, aplican obligaciones de protección de datos. |
| **Ley de la Industria Eléctrica** | Regulación del sector eléctrico | Define las atribuciones de CFE y los derechos del usuario final respecto a la medición de consumo. |

#### Teoría aplicada al proyecto

Es importante aclarar que este dispositivo **no pretende sustituir al medidor fiscal** de CFE (el cual debe cumplir estándares de clase metrológica 0.2 o 0.5 según la IEC 62053). El prototipo se clasifica como un **instrumento informativo y educativo**, es decir, una herramienta de apoyo para el usuario que no tiene valor probatorio para la facturación ni para reclamaciones legales ante la empresa suministradora. Esta distinción es necesaria para definir correctamente el alcance legal del dispositivo.

[⬆ Volver al inicio](#inicio)

---

## 7. Marco Metodológico

<a name="7-marco-metodológico"></a>

El marco metodológico describe **cómo** se llevará a cabo la investigación. Es la sección que establece la estrategia operativa para responder la pregunta de investigación y verificar la hipótesis. Según Arias (2012), el marco metodológico comprende el conjunto de procedimientos, técnicas e instrumentos que se emplean para la recolección y análisis de datos.

En investigaciones de tipo experimental con prototipo físico, esta sección debe ser lo suficientemente detallada para que otro investigador pueda **replicar** el estudio.

---

### 7.1 Tipo y Diseño de Investigación

<a name="71-tipo-y-diseño-de-investigación"></a>

#### ¿Qué debe contener?

Se debe declarar formalmente la clasificación metodológica del proyecto, justificando cada categoría con argumentos vinculados al problema y los objetivos.

#### Clasificaciones aplicables

| Criterio | Clasificación | Justificación |
|---|---|---|
| **Finalidad** | Aplicada y Tecnológica | No busca generar teoría nueva, sino aplicar conocimiento existente para resolver un problema práctico. |
| **Enfoque de datos** | Cuantitativa | Se recolectarán datos numéricos (corriente, voltaje, potencia, error) y se analizarán estadísticamente. |
| **Alcance** | Correlacional y Explicativa | Se evalúa la correlación entre mediciones del prototipo y del instrumento patrón, y se explican los factores que afectan la precisión. |
| **Lugar de realización** | Mixta (Laboratorio + Campo) | Calibración controlada en laboratorio y validación en vivienda real. |
| **Manipulación de variables** | Experimental | Se manipulan cargas eléctricas (variable independiente) para observar la respuesta del sistema (variable dependiente). |
| **Temporalidad** | Transversal con elementos longitudinales | Las pruebas comparativas son transversales (un momento), pero el monitoreo en campo implica registro continuo durante un periodo. |

#### Diseño experimental específico

Para la validación del prototipo se utiliza un **diseño preexperimental de un solo grupo con pretest-postest** o, más adecuadamente, un **diseño de medidas repetidas** donde el mismo conjunto de cargas se mide simultáneamente con el prototipo y con el instrumento patrón. Este enfoque permite calcular la concordancia entre ambos métodos mediante el **análisis de Bland-Altman** y el **coeficiente de correlación intraclase (ICC)**.

[⬆ Volver al inicio](#inicio)

---

### 7.2 Operacionalización de Variables

<a name="72-operacionalización-de-variables"></a>

#### ¿Qué debe contener?

La operacionalización transforma los conceptos abstractos de la hipótesis en **variables medibles y observables**. Cada variable debe definirse en tres niveles (Hernández Sampieri et al., 2014):

1. **Definición conceptual:** ¿Qué significa teóricamente?
2. **Definición operacional:** ¿Cómo se mide en la práctica?
3. **Indicadores:** ¿Qué valores concretos se registran?

#### Tabla de operacionalización para el proyecto

| Variable | Tipo | Definición Operacional | Indicador | Instrumento | Escala |
|---|---|---|---|---|---|
| **Carga eléctrica aplicada** | Independiente | Potencia consumida por el dispositivo conectado al circuito de prueba. | Watts (W) | Multímetro TRMS de referencia | Razón |
| **Corriente eficaz ($I_{RMS}$)** | Dependiente | Valor RMS calculado por el firmware del ESP32 a partir de las muestras del ADC. | Amperios (A) | Prototipo (SCT-013 + ESP32) | Razón |
| **Voltaje eficaz ($V_{RMS}$)** | Dependiente | Valor RMS del voltaje de red calculado a partir del ZMPT101B. | Volts (V) | Prototipo (ZMPT101B + ESP32) | Razón |
| **Potencia activa ($P$)** | Dependiente | Producto promedio de las muestras instantáneas de voltaje y corriente. | Watts (W) | Prototipo | Razón |
| **Error porcentual ($E_{\%}$)** | Dependiente (calculada) | Diferencia porcentual entre la medición del prototipo y la referencia. | Porcentaje (%) | Cálculo matemático | Razón |
| **Costo de implementación** | Dependiente | Suma del costo de todos los componentes de la BOM. | MXN ($) | Cotización verificada | Razón |

[⬆ Volver al inicio](#inicio)

---

### 7.3 Población y Muestra

<a name="73-población-y-muestra"></a>

#### ¿Qué debe contener?

Aunque en investigaciones de ingeniería con prototipos el concepto de "población y muestra" difiere del enfoque de ciencias sociales, sigue siendo necesario definir:

- **Población de estudio:** El universo de elementos sobre los cuales se generalizan los resultados.
- **Muestra:** El subconjunto seleccionado para las pruebas.
- **Criterios de selección:** Inclusión y exclusión.

#### Teoría aplicada al proyecto

En este tipo de investigación experimental, la "población" no son personas sino **condiciones de carga eléctrica** y la "muestra" son los **puntos de medición seleccionados**.

| Concepto | Aplicación |
|---|---|
| **Población** | Conjunto de todas las posibles condiciones de carga eléctrica en una vivienda monofásica residencial (0 a 30 A). |
| **Muestra** | Conjunto de $n$ mediciones realizadas en puntos discretos de carga: 0.5 A, 1 A, 2 A, 5 A, 10 A, 15 A, 20 A, 25 A, 30 A (mínimo 10 niveles de carga con 30 repeticiones cada uno = 300 mediciones). |
| **Tipo de muestreo** | No probabilístico intencional (los niveles de carga se eligen deliberadamente para cubrir el rango operativo del sensor). |
| **Criterios de inclusión** | Cargas resistivas puras y cargas inductivas comunes (motores fraccionarios), conectadas a circuito monofásico 127 V. |
| **Criterios de exclusión** | Cargas trifásicas, cargas con corriente < 0.2 A (zona muerta del ADC), equipos con distorsión armónica extrema (soldadoras de arco). |

El tamaño de muestra se determina aplicando criterios de potencia estadística. Para pruebas de correlación con un nivel de significancia $\alpha = 0.05$ y una potencia deseada de $1 - \beta = 0.80$, el mínimo teórico es de 30 pares de observaciones por nivel de carga (Cohen, 1988).

[⬆ Volver al inicio](#inicio)

---

### 7.4 Técnicas e Instrumentos de Recolección de Datos

<a name="74-técnicas-e-instrumentos-de-recolección-de-datos"></a>

#### ¿Qué debe contener?

Se deben describir todos los instrumentos de medición, tanto del prototipo como del estándar de referencia ("patrón"), indicando sus especificaciones técnicas que permitan evaluar su idoneidad.

#### Clasificación de instrumentos

| Instrumento | Función | Especificaciones clave |
|---|---|---|
| **Prototipo (ESP32 + SCT-013 + ZMPT101B)** | Dispositivo bajo prueba (DUT) | ADC de 12 bits, rango 0-30 A, muestreo a ~1 kHz. |
| **Multímetro TRMS de referencia** | Instrumento patrón para comparación | Precisión ±0.5%, True RMS, certificado/calibrado. |
| **Osciloscopio digital** (deseable) | Verificación de formas de onda | Permite visualizar la señal del sensor y detectar distorsiones no capturadas por el firmware. |
| **Cargas conocidas** | Generación de condiciones experimentales controladas | Lámparas incandescentes (carga resistiva), ventiladores (carga inductiva), con potencia nominal verificada. |
| **Registro de datos (datalogger)** | Almacenamiento de series temporales | MicroSD integrada en el prototipo y terminal serial del ESP32 para exportación a CSV. |

#### Técnicas de recolección

1. **Observación directa estructurada:** Registro simultáneo de las lecturas del prototipo y del instrumento patrón bajo las mismas condiciones.
2. **Registro automatizado:** El firmware del ESP32 almacena muestras en la microSD con marca temporal (*timestamp*), eliminando errores de transcripción manual.
3. **Pruebas de barrido de carga:** Mediciones sucesivas incrementando la carga desde el mínimo detectable hasta el máximo del sensor, con pasos definidos.

[⬆ Volver al inicio](#inicio)

---

### 7.5 Procedimiento Experimental

<a name="75-procedimiento-experimental"></a>

#### ¿Qué debe contener?

Una descripción paso a paso del protocolo experimental, lo suficientemente detallada para permitir la **replicabilidad**. Según la norma ISO/IEC 17025 (requisitos para laboratorios de ensayo), todo procedimiento experimental debe especificar: condiciones ambientales, secuencia de operaciones, tiempos de estabilización y criterios de aceptación/rechazo.

#### Fases del procedimiento para este proyecto

**Fase 1: Calibración en Laboratorio (Condiciones Controladas)**

1. Energizar el prototipo y esperar un periodo de estabilización térmica (≥ 5 minutos).
2. Conectar una carga resistiva pura de valor conocido.
3. Registrar simultáneamente la lectura del prototipo y del multímetro patrón.
4. Repetir la medición 30 veces para cada nivel de carga.
5. Incrementar la carga al siguiente nivel y repetir.
6. Aplicar correcciones de calibración (factor de ajuste lineal).

**Fase 2: Validación con Cargas Mixtas (Laboratorio)**

7. Sustituir cargas resistivas por cargas inductivas (motores) y cargas no lineales (fuentes conmutadas de electrodomésticos).
8. Registrar mediciones de potencia activa y comparar con el patrón.
9. Evaluar el impacto del factor de potencia en la precisión.

**Fase 3: Pruebas de Campo (Vivienda Real)**

10. Instalar el prototipo en el tablero de distribución de una vivienda monofásica.
11. Monitorizar el consumo durante un periodo mínimo de 24-72 horas.
12. Comparar el consumo acumulado ($kWh$) registrado por el prototipo contra la lectura del medidor de CFE.
13. Documentar condiciones ambientales: temperatura, distancia al router WiFi, eventos de interrupción de red.

**Fase 4: Análisis de Robustez**

14. Provocar deliberadamente condiciones adversas: abrir la puerta del tablero metálico (atenuación WiFi), encender cargas de alto arranque (motores de refrigerador), simular cortes de energía.
15. Registrar el comportamiento del sistema ante cada escenario.

[⬆ Volver al inicio](#inicio)

---

### 7.6 Técnicas de Procesamiento y Análisis de Datos

<a name="76-técnicas-de-procesamiento-y-análisis-de-datos"></a>

#### ¿Qué debe contener?

Se deben especificar las herramientas de software y las técnicas estadísticas que se emplearán para procesar los datos brutos y convertirlos en información interpretable.

#### Herramientas de software

- **Microsoft Excel / Google Sheets:** Para organización inicial de datos en hojas de cálculo.
- **Python (con bibliotecas NumPy, Pandas, Matplotlib, SciPy):** Para análisis estadístico avanzado, generación de gráficos y automatización del procesamiento.
- **MATLAB / GNU Octave:** Alternativa para procesamiento numérico y análisis de señales (opcional).

#### Técnicas estadísticas

| Técnica | Propósito | Aplicación en el proyecto |
|---|---|---|
| **Estadística descriptiva** | Resumir los datos | Media ($\bar{x}$), desviación estándar ($\sigma$), rango, valores mínimo y máximo de cada serie de mediciones. |
| **Error Porcentual Absoluto Medio (MAPE)** | Cuantificar la diferencia global entre prototipo y patrón | $MAPE = \frac{1}{n} \sum_{i=1}^{n} \left| \frac{Patrón_i - Prototipo_i}{Patrón_i} \right| \times 100$ |
| **Coeficiente de correlación de Pearson ($r$)** | Medir la fuerza de la relación lineal entre mediciones del prototipo y las del patrón | Se espera $r > 0.99$. |
| **Coeficiente de determinación ($R^2$)** | Porcentaje de varianza explicada por el modelo lineal | Se espera $R^2 > 0.98$. |
| **Análisis de regresión lineal** | Obtener la ecuación de calibración | $y = mx + b$, donde $y$ es la lectura del prototipo y $x$ la del patrón. Si la calibración es perfecta, $m \approx 1$ y $b \approx 0$. |
| **Prueba t de Student para muestras pareadas** | Determinar si existe diferencia estadísticamente significativa entre ambos métodos de medición | $H_0$: La media de las diferencias es cero ($\bar{d} = 0$). |
| **Análisis de Bland-Altman** | Evaluar la concordancia entre dos métodos de medición | Gráfico de diferencias vs. promedios; los límites de concordancia indican el rango de error esperado. |
| **ANOVA de un factor** (opcional pero recomendado) | Comparar la precisión del prototipo entre diferentes tipos de carga | Factor: tipo de carga (resistiva, inductiva, no lineal). Variable respuesta: error porcentual. |

[⬆ Volver al inicio](#inicio)

---

### 7.7 Criterios de Validez y Confiabilidad

<a name="77-criterios-de-validez-y-confiabilidad"></a>

#### ¿Qué debe contener?

Todo instrumento de medición debe evaluarse en dos dimensiones (Hernández Sampieri et al., 2014):

- **Validez:** ¿El instrumento mide realmente lo que pretende medir?
- **Confiabilidad:** ¿Las mediciones son consistentes y reproducibles?

#### Tipos de validez aplicables

| Tipo de validez | Descripción | Aplicación al proyecto |
|---|---|---|
| **Validez de contenido** | Los indicadores cubren todos los aspectos del constructo. | El sistema mide las tres variables necesarias: corriente, voltaje y potencia activa, no se omite ninguna dimensión relevante. |
| **Validez de criterio (concurrente)** | Los resultados se comparan contra un estándar externo reconocido. | Las mediciones del prototipo se contrastan con un multímetro TRMS calibrado (criterio externo). |
| **Validez de constructo** | Los resultados son coherentes con la teoría subyacente. | Si al aumentar la carga, la corriente medida por el prototipo aumenta proporcionalmente, el constructo es válido (señal proporcional según la Ley de Faraday). |

#### Confiabilidad

La confiabilidad se evalúa mediante la **repetibilidad** (misma condición, mismo operador, mismo equipo, corto plazo) y la **reproducibilidad** (diferentes condiciones u operadores). Para instrumentos de medición, se utiliza el **Coeficiente de Variación (CV)**:

$$CV = \frac{\sigma}{\bar{x}} \times 100\%$$

Un $CV < 5\%$ indica alta confiabilidad para instrumentos de ingeniería (JCGM 100:2008).

[⬆ Volver al inicio](#inicio)

---

## 8. Diseño e Implementación del Sistema

<a name="8-diseño-e-implementación-del-sistema"></a>

Esta sección es **exclusiva de investigaciones aplicadas-tecnológicas** que producen un artefacto, prototipo o sistema funcional. En investigaciones puramente teóricas o descriptivas, esta sección no existe. Aquí se documenta el proceso de ingeniería que traduce los fundamentos teóricos del marco teórico en un producto tangible.

---

### 8.1 Arquitectura General del Sistema

<a name="81-arquitectura-general-del-sistema"></a>

#### ¿Qué debe contener?

Un diagrama de bloques de alto nivel que muestre los subsistemas principales y sus interrelaciones. Debe incluir:

- **Subsistema de sensado:** Sensores y etapa de acondicionamiento de señal.
- **Subsistema de procesamiento:** Microcontrolador y firmware.
- **Subsistema de comunicación:** WiFi, protocolos de red.
- **Subsistema de alimentación:** Fuente conmutada.
- **Subsistema de interfaz:** Pantalla OLED, plataforma web/app.
- **Subsistema de almacenamiento:** MicroSD para *data logging*.

#### Teoría aplicada al proyecto

Se recomienda utilizar el modelo de **arquitectura en capas** del IoT para estructurar la descripción:

1. **Capa de Percepción:** SCT-013 (corriente), ZMPT101B (voltaje), con circuitos de offset y acondicionamiento.
2. **Capa de Procesamiento (Edge):** ESP32 ejecutando algoritmos de cálculo RMS y potencia activa en tiempo real.
3. **Capa de Red:** Conectividad WiFi 802.11 b/g/n, protocolo MQTT o HTTP para transmisión de datos.
4. **Capa de Aplicación:** Dashboard web, interfaz OLED local, almacenamiento en nube o microSD.

[⬆ Volver al inicio](#inicio)

---

### 8.2 Diseño del Hardware

<a name="82-diseño-del-hardware"></a>

#### ¿Qué debe contener?

La documentación de hardware es el equivalente a los "planos" del proyecto. Debe permitir a cualquier ingeniero replicar el circuito. Se incluyen:

1. **Diagrama esquemático:** Circuito eléctrico completo con identificación de componentes, valores y conexiones. Herramientas recomendadas: KiCad, Eagle, Proteus, Fritzing.
2. **Selección y justificación de componentes:** Para cada componente clave, indicar por qué se eligió frente a alternativas (criterios: costo, disponibilidad, especificaciones técnicas, compatibilidad).
3. **Cálculos de diseño:** Valores de resistencias del divisor de tensión para el offset, selección del *burden resistor*, cálculos de la fuente.
4. **Diseño de PCB** (si aplica): Layout de la placa de circuito impreso, consideraciones de ruteo y separación de pistas de alta tensión.

#### Subsecciones típicas

- **Unidad de procesamiento (ESP32):** Especificaciones del SoC, pines utilizados (solo ADC1: GPIO 32-39), configuración de periféricos.
- **Etapa de sensado de corriente:** Circuito completo del SCT-013 con *burden resistor*, divisor de tensión de offset y capacitores de filtrado.
- **Etapa de sensado de voltaje:** Conexión del módulo ZMPT101B, circuito de acondicionamiento de señal.
- **Fuente de alimentación integrada:** Módulo SMPS AC-DC (Hi-Link o equivalente), protecciones contra sobretensión, fusibles.
- **Interfaz de usuario local:** Conexión I2C de la pantalla OLED SSD1306.
- **Almacenamiento local:** Conexión SPI del módulo microSD.

[⬆ Volver al inicio](#inicio)

---

### 8.3 Diseño del Firmware / Software

<a name="83-diseño-del-firmware--software"></a>

#### ¿Qué debe contener?

La documentación del software embebido debe ser igualmente rigurosa que la del hardware. Incluye:

1. **Entorno de desarrollo:** IDE utilizado (Arduino IDE, PlatformIO/VSCode), versión del framework, bibliotecas empleadas y sus versiones.
2. **Diagrama de flujo general:** Representación algorítmica del flujo principal del programa.
3. **Descripción de módulos/funciones:**
   - Módulo de adquisición de datos (lectura de ADC, cálculo de $I_{RMS}$, $V_{RMS}$, $P$).
   - Módulo de comunicación (WiFi, MQTT/HTTP).
   - Módulo de interfaz (OLED, Serial).
   - Módulo de almacenamiento (escritura en microSD).
   - Módulo de calibración (factores de escala, corrección de offset).
4. **Gestión de tareas concurrentes:** Uso de FreeRTOS para asignar tareas a los dos núcleos del ESP32 (Núcleo 0: comunicación; Núcleo 1: muestreo y cálculo).
5. **Pseudocódigo o fragmentos de código clave:** Para los algoritmos críticos (cálculo RMS, filtrado, cruce por cero).

#### Bibliotecas relevantes

| Biblioteca | Función |
|---|---|
| `EmonLib` | Cálculos de energía ($I_{RMS}$, potencia aparente). |
| `WiFi.h` | Gestión de la conexión WiFi del ESP32. |
| `PubSubClient` | Cliente MQTT para transmisión de datos IoT. |
| `Adafruit_SSD1306` | Control de la pantalla OLED. |
| `SD.h` / `SPI.h` | Lectura y escritura en tarjeta microSD. |
| `driver/adc.h` | Acceso directo al driver del ADC del ESP32 para configuración avanzada. |

[⬆ Volver al inicio](#inicio)

---

### 8.4 Integración y Ensamblaje

<a name="84-integración-y-ensamblaje"></a>

#### ¿Qué debe contener?

Documentación fotográfica y descriptiva del proceso de ensamblaje físico del prototipo:

- **Soldadura y montaje en PCB/protoboard:** Descripción del proceso de construcción.
- **Diseño del gabinete/carcasa:** Dimensiones, material (impresión 3D en PLA, caja comercial de ABS), ubicación de puertos y conectores.
- **Consideraciones de seguridad eléctrica:** Aislamiento de las zonas de alta tensión (línea AC), separación de pistas de baja y alta potencia, fusibles de protección.
- **Fotografías del prototipo terminado:** Vistas exterior e interior.

[⬆ Volver al inicio](#inicio)

---

### 8.5 Análisis de Costos (BOM)

<a name="85-análisis-de-costos-bom"></a>

#### ¿Qué debe contener?

La Lista de Materiales (Bill of Materials) detallada, con:

- **Descripción del componente** y referencia del fabricante.
- **Cantidad** por unidad de prototipo.
- **Costo unitario** (MXN) con la fuente de cotización.
- **Costo total por componente.**
- **Costo total del prototipo.**
- **Comparación porcentual** con el precio de soluciones comerciales equivalentes para demostrar la viabilidad económica.

El análisis de costos es un componente crucial en investigaciones aplicadas-tecnológicas porque uno de los objetivos es demostrar la **ventaja económica** del prototipo respecto a las alternativas existentes.

[⬆ Volver al inicio](#inicio)

---

## 9. Resultados y Discusión

<a name="9-resultados-y-discusión"></a>

Esta sección presenta los datos obtenidos del proceso experimental y su interpretación. Es donde la investigación **demuestra o refuta** la hipótesis planteada. Según la APA (2020), los resultados deben presentarse de forma objetiva, separando la descripción de los datos (resultados) de su interpretación y contextualización (discusión).

---

### 9.1 Presentación de Resultados

<a name="91-presentación-de-resultados"></a>

#### ¿Qué debe contener?

Los datos recopilados durante la fase experimental, organizados de forma clara y sistemática:

1. **Tablas de datos:** Mediciones del prototipo vs. instrumento patrón para cada nivel de carga. Cada tabla debe tener título, unidades, número de repeticiones y fuente.
2. **Gráficos:**
   - **Gráfico de dispersión (Scatter Plot):** Medición del prototipo (eje Y) vs. medición patrón (eje X), con línea de regresión y ecuación.
   - **Gráfico de error porcentual vs. carga:** Para identificar el rango de operación óptimo.
   - **Gráfico de Bland-Altman:** Diferencia entre métodos vs. promedio de ambos, con líneas de media y límites de concordancia (±1.96$\sigma$).
   - **Serie temporal:** Registro de consumo durante las pruebas de campo (24-72 horas).
3. **Valores calculados:** $R^2$, MAPE, desviación estándar, intervalos de confianza.

#### Reglas de presentación

- Los resultados se presentan **sin interpretación** en esta subsección.
- Cada tabla y figura debe ser **autoexplicativa** (entendible sin leer el texto circundante).
- Seguir las normas APA 7 para la elaboración de tablas y figuras (títulos en cursiva, notas al pie).

[⬆ Volver al inicio](#inicio)

---

### 9.2 Análisis Estadístico

<a name="92-análisis-estadístico"></a>

#### ¿Qué debe contener?

La aplicación de las técnicas estadísticas descritas en la sección 7.6 a los datos reales obtenidos:

1. **Prueba de normalidad** (Shapiro-Wilk o Kolmogorov-Smirnov) para verificar que los datos siguen una distribución normal antes de aplicar pruebas paramétricas.
2. **Prueba t de Student para muestras pareadas** con el valor $p$ resultante y el intervalo de confianza del 95%.
3. **Análisis de correlación y regresión** con los coeficientes $r$, $R^2$, y la ecuación de la recta de regresión.
4. **ANOVA** (si se compara el desempeño entre tipos de carga).
5. **Cálculo de incertidumbre de medición** según la Guía para la Expresión de la Incertidumbre de Medida (GUM, JCGM 100:2008).

Todos los resultados estadísticos deben reportarse con el formato estándar: estadístico, grados de libertad, valor $p$ y tamaño del efecto. Ejemplo: $t(29) = 1.85$, $p = 0.074$, $d = 0.34$.

[⬆ Volver al inicio](#inicio)

---

### 9.3 Discusión e Interpretación

<a name="93-discusión-e-interpretación"></a>

#### ¿Qué debe contener?

La discusión es la sección más analítica y argumentativa del documento. Aquí el investigador:

1. **Interpreta los resultados** a la luz de la hipótesis: ¿Se confirma o se rechaza?
2. **Explica los hallazgos inesperados:** ¿Por qué el error es mayor en cargas bajas? ¿Qué efecto tuvo el ruido de la fuente conmutada?
3. **Relaciona los resultados con las bases teóricas:** ¿Los datos son congruentes con la Ley de Faraday y la teoría de muestreo?
4. **Identifica fortalezas y debilidades del estudio.**
5. **Reconoce las limitaciones** que pudieron afectar los resultados.

#### Teoría aplicada al proyecto

En este proyecto, la discusión debe abordar:

- El incremento del error porcentual en cargas menores a 50 W, atribuible al ruido de cuantización del ADC de 12 bits del ESP32 (resolución limitada en la parte baja de la escala del SCT-013 de 30 A).
- El comportamiento del sistema ante cargas inductivas vs. resistivas y su relación con el factor de potencia.
- El impacto de las fluctuaciones de voltaje de la red (observadas en campo) en la precisión de la medición de potencia activa.
- La estabilidad de la conexión WiFi dentro/fuera del tablero metálico.
- La comparación entre el error obtenido y el criterio de aceptación establecido en la hipótesis (< 5%).

[⬆ Volver al inicio](#inicio)

---

### 9.4 Comparación con el Estado del Arte

<a name="94-comparación-con-el-estado-del-arte"></a>

#### ¿Qué debe contener?

Una tabla o análisis que posicione los resultados del prototipo frente a las soluciones revisadas en el estado del arte:

| Criterio | Prototipo propuesto | Solución comercial A | Solución académica B |
|---|---|---|---|
| Costo | ~$600 MXN | >$1,500 MXN | ~$800 MXN (importado) |
| Precisión (MAPE) | X.X% | ±1% (clase 1) | Y.Y% |
| Instalación | No intrusiva | Semi-intrusiva | No intrusiva |
| Medición de $P$ real | Sí (V × I) | Sí | No (estimada) |
| Conectividad | WiFi + microSD | WiFi/Zigbee | WiFi |

Esta comparación permite argumentar la **contribución diferencial** del proyecto y contextualizar los resultados dentro del panorama tecnológico actual.

[⬆ Volver al inicio](#inicio)

---

## 10. Conclusiones y Recomendaciones

<a name="10-conclusiones-y-recomendaciones"></a>

---

### 10.1 Conclusiones

<a name="101-conclusiones"></a>

#### ¿Qué debe contener?

Las conclusiones son una síntesis de los hallazgos principales, **directamente ligadas a los objetivos planteados**. Cada objetivo específico debe tener una conclusión correspondiente. Según Hernández Sampieri et al. (2014), las conclusiones:

- No introducen información nueva.
- No repiten los resultados textualmente, sino que los interpretan de forma global.
- Responden explícitamente a la pregunta de investigación.
- Declaran si la hipótesis fue **aceptada o rechazada** con base en la evidencia estadística.

#### Estructura recomendada

1. **Conclusión general:** ¿Se logró el objetivo general? ¿Se confirmó la hipótesis?
2. **Conclusiones específicas:** Una por cada objetivo específico, indicando el grado de cumplimiento.
3. **Contribución del trabajo:** ¿Qué aporta este proyecto al conocimiento o a la práctica?

[⬆ Volver al inicio](#inicio)

---

### 10.2 Recomendaciones

<a name="102-recomendaciones"></a>

#### ¿Qué debe contener?

Sugerencias prácticas derivadas de la experiencia del estudio, dirigidas a:

- **Futuros investigadores** que deseen replicar o ampliar el proyecto.
- **Usuarios potenciales** del dispositivo.
- **Instituciones educativas** que adopten este tipo de proyectos.

Las recomendaciones deben ser **concretas y accionables**, no genéricas. Ejemplo: *"Se recomienda utilizar un ADC externo de 16 bits (ADS1115) para mejorar la resolución en cargas menores a 50 W"* es preferible a *"Se recomienda mejorar la precisión"*.

[⬆ Volver al inicio](#inicio)

---

### 10.3 Trabajo Futuro

<a name="103-trabajo-futuro"></a>

#### ¿Qué debe contener?

Líneas de investigación o desarrollo que quedan abiertas tras la conclusión de este proyecto:

1. **Mejoras de hardware:** Integración de ADC externo de mayor resolución, sensor de corriente de menor rango para mejorar sensibilidad en cargas bajas, diseño de PCB profesional.
2. **Mejoras de software:** Implementación de algoritmos de desagregación de carga (NILM avanzado) mediante *Machine Learning* en el borde (*Edge Computing* con TensorFlow Lite).
3. **Escalabilidad:** Extensión del sistema a viviendas bifásicas (dos sensores de corriente) y comercios con servicio trifásico.
4. **Integración con Smart Grid:** Comunicación bidireccional con la red eléctrica para respuesta a la demanda (*Demand Response*).
5. **Validación a gran escala:** Producción de un lote piloto y pruebas con múltiples usuarios para evaluar la experiencia de uso y la adopción real.
6. **Certificación:** Proceso de evaluación bajo normas NOM para su potencial comercialización.

[⬆ Volver al inicio](#inicio)

---

## 11. Referencias Bibliográficas

<a name="11-referencias-bibliográficas"></a>

Las referencias bibliográficas deben incluir **todas y solo las fuentes citadas** en el cuerpo del documento. Se emplea el formato **APA 7ª edición** (American Psychological Association, 2020). A continuación se presentan las referencias relevantes para este proyecto, clasificadas por tipo de fuente para mayor claridad expositiva, aunque en el documento final deben aparecer en **orden alfabético** por apellido del primer autor.

---

### Libros y Manuales Metodológicos

American Psychological Association. (2020). *Publication manual of the American Psychological Association* (7th ed.). American Psychological Association. https://doi.org/10.1037/0000165-000

Arias, F. G. (2012). *El proyecto de investigación: Introducción a la metodología científica* (6ª ed.). Editorial Episteme.

Cohen, J. (1988). *Statistical power analysis for the behavioral sciences* (2nd ed.). Lawrence Erlbaum Associates.

Creswell, J. W., & Creswell, J. D. (2018). *Research design: Qualitative, quantitative, and mixed methods approaches* (5th ed.). SAGE Publications.

Doran, G. T. (1981). There's a S.M.A.R.T. way to write management's goals and objectives. *Management Review*, *70*(11), 35–36.

Hernández Sampieri, R., Fernández Collado, C., & Baptista Lucio, M. del P. (2014). *Metodología de la investigación* (6ª ed.). McGraw-Hill Education.

Kerlinger, F. N., & Lee, H. B. (2002). *Investigación del comportamiento: Métodos de investigación en ciencias sociales* (4ª ed.). McGraw-Hill.

Popper, K. R. (1959). *The logic of scientific discovery*. Hutchinson & Co.

### Artículos Científicos y Conferencias

Alkar, A. Z., & Buhur, U. (2005). An Internet based wireless home automation system for multifunctional devices. *IEEE Transactions on Consumer Electronics*, *51*(4), 1169–1174. https://doi.org/10.1109/TCE.2005.1561840

Liu, Y., Wang, X., & Jian, W. (2021). Design of Smart Home Energy Management System Based on ESP32. En *Proceedings of the International Conference on Electronic Information Technology* (pp. 112–117). IEEE. https://doi.org/10.1109/ICEIT51700.2021.9375653

### Documentos Técnicos y Hojas de Datos

Espressif Systems. (2022). *ESP32 Series Datasheet* (ver. 3.4). Espressif Systems. https://www.espressif.com/sites/default/files/documentation/esp32_datasheet_en.pdf

Joint Committee for Guides in Metrology [JCGM]. (2008). *Evaluation of measurement data — Guide to the expression of uncertainty in measurement* (JCGM 100:2008). Bureau International des Poids et Mesures. https://www.bipm.org/documents/20126/2071204/JCGM_100_2008_E.pdf

### Normas y Regulaciones

Comisión Federal de Electricidad [CFE]. (2024). *Tarifas domésticas de energía eléctrica*. CFE. https://app.cfe.mx/Aplicaciones/CCFE/Tarifas/TarifasCRECasa/Casa.aspx

Comisión Reguladora de Energía [CRE]. (2023). *Regulación tarifaria del sector eléctrico mexicano*. Gobierno de México.

International Electrotechnical Commission [IEC]. (2003). *IEC 62053-21: Electricity metering equipment — Particular requirements — Part 21: Static meters for active energy (classes 1 and 2)*. IEC.

International Organization for Standardization [ISO]. (1976). *ISO 214:1976 — Documentation — Abstracts for publications and documentation*. ISO.

International Organization for Standardization [ISO/IEC]. (2017). *ISO/IEC 17025:2017 — General requirements for the competence of testing and calibration laboratories*. ISO.

Norma Oficial Mexicana NOM-001-SEDE-2012. (2012). *Instalaciones Eléctricas (Utilización)*. Diario Oficial de la Federación, México.

Norma Oficial Mexicana NOM-003-SCFI-2014. (2014). *Productos eléctricos — Requisitos de seguridad*. Diario Oficial de la Federación, México.

### Fuentes Institucionales y Estadísticas

Instituto Nacional de Estadística y Geografía [INEGI]. (2018). *Encuesta Nacional sobre Consumo de Energéticos en Viviendas Particulares (ENCEVI) 2018*. INEGI. https://www.inegi.org.mx/programas/encevi/2018/

Secretaría de Energía [SENER]. (2023). *Balance Nacional de Energía 2022*. Gobierno de México.

[⬆ Volver al inicio](#inicio)

---

## 12. Anexos

<a name="12-anexos"></a>

Los anexos contienen material complementario que, por su extensión o naturaleza, no es conveniente incluir en el cuerpo principal del documento, pero que respalda o amplía la información presentada.

### Tipos de anexos recomendados para este proyecto

| Anexo | Contenido |
|---|---|
| **Anexo A: Diagrama esquemático completo** | Circuito eléctrico en formato imprimible (generado en KiCad, Eagle o Proteus). |
| **Anexo B: Código fuente del firmware** | Código completo del programa del ESP32, comentado línea a línea. |
| **Anexo C: Tablas de datos experimentales completas** | Todas las mediciones registradas durante las pruebas (formato tabular). |
| **Anexo D: Hojas de datos (*Datasheets*)** | ESP32, SCT-013-030, ZMPT101B, Hi-Link HLK-PM01, SSD1306. |
| **Anexo E: Fotografías del proceso de ensamblaje** | Secuencia fotográfica de la construcción del prototipo. |
| **Anexo F: Manual de usuario** | Instrucciones de instalación, configuración WiFi y uso de la interfaz. |
| **Anexo G: Certificados de calibración** | Del instrumento patrón (multímetro TRMS) utilizado como referencia. |
| **Anexo H: Cronograma de actividades (Diagrama de Gantt)** | Distribución temporal de las fases del proyecto. |
| **Anexo I: Matriz de consistencia** | Tabla que vincula problema → objetivos → hipótesis → variables → indicadores → instrumentos. |

### Sobre la Matriz de Consistencia

La **matriz de consistencia** es una herramienta de verificación interna que garantiza la coherencia lógica de toda la investigación. Cada fila de la matriz conecta un aspecto del problema con su correspondiente objetivo, hipótesis, variable e indicador. Si alguna celda queda vacía o contradice a otra, existe un defecto estructural en el planteamiento.

| Problema | Objetivo Específico | Hipótesis Operacional | Variable | Indicador | Instrumento |
|---|---|---|---|---|---|
| Falta de medición accesible de corriente | Diseñar etapa de sensado de corriente | El SCT-013 produce señal lineal ($R^2 > 0.98$) | $I_{RMS}$ | Amperios (A) | SCT-013 + ESP32 |
| Estimaciones imprecisas sin voltaje real | Integrar sensor de voltaje ZMPT101B | La medición de $P$ real es más precisa que la estimada | $P$ (Potencia Activa) | Watts (W) | ZMPT101B + ESP32 |
| Alto costo de soluciones comerciales | Optimizar BOM bajo $600 MXN | El costo no excede $600 MXN | Costo BOM | MXN ($) | Cotización |

[⬆ Volver al inicio](#inicio)

---

> **Nota final:** Este documento es una guía teórica sobre la estructura y el contenido esperado de cada sección de la investigación. La redacción definitiva de cada apartado debe realizarse conforme avance la ejecución del proyecto, incorporando los datos reales obtenidos y ajustando las decisiones metodológicas según las condiciones encontradas en laboratorio y campo.

[⬆ Volver al inicio](#inicio)
