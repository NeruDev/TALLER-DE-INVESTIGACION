<!--
===================================================================
METADATOS DEL DOCUMENTO (Referencia interna)
===================================================================
Título      : Hipótesis y Bosquejo del Método (Complemento Tema 2)
Proyecto    : Diseño e Implementación de un Sistema IoT de Bajo
              Costo para la Monitorización No Intrusiva de Consumo
              Eléctrico Residencial mediante Arquitectura ESP32
Autor       : Investigador (compilado con apoyo de IA)
Fecha       : 2026-04-21
Idioma      : es-MX
Fuente base : Proyecto completo.md (documento maestro vigente)
Guion       : TALLER 1/TAREAS/Diapositivas.md
Notas       : Se redacta en estilo técnico-formal y mantiene coherencia
              con hipótesis, metodología y métricas reportadas en el
              documento maestro. Algunas referencias metodológicas
              (Bland–Altman; Shapiro–Wilk; Tamayo y Tamayo) fueron
              verificadas/ubicadas mediante herramientas MCP de web.
===================================================================
-->

# Hipótesis y Bosquejo del Método (Complemento Tema 2)

## Contexto y propósito

Este documento desarrolla, con redacción técnica y formal, los apartados solicitados en el guion de **Complemento Tema 2** (hipótesis y bosquejo del método), empleando como fuente primaria el proyecto maestro **"Diseño e Implementación de un Sistema IoT de Bajo Costo para la Monitorización No Intrusiva de Consumo Eléctrico Residencial mediante Arquitectura ESP32"**.

El proyecto propone un prototipo de monitorización energética residencial (SME-IoT) basado en **ESP32**, sensor de corriente **SCT-013-030** (no intrusivo), sensor de voltaje **ZMPT101B** y operación híbrida **WiFi/microSD**. La validación del sistema se plantea como investigación **aplicada-tecnológica** con enfoque **cuantitativo**, alcance **correlacional-experimental** y diseño **mixto** (laboratorio y campo), utilizando métricas objetivas como $R^2$, MAPE y error porcentual.

---

## 1. Hipótesis

En investigación cuantitativa, una **hipótesis** es una proposición tentativa, **comprobable empíricamente**, que expresa una relación esperada entre variables medibles. En el marco de este proyecto, las hipótesis conectan explícitamente:

- Variables de desempeño metrológico del prototipo (p. ej., $I_{RMS}$, $V_{RMS}$, $P$, $E_{\%}$, MAPE, $R^2$).
- Variables de viabilidad económica (costo total de la lista de materiales, BOM, en MXN).
- Condiciones de operación del sistema eléctrico residencial (127 V/60 Hz monofásico, rango operativo del sensor y limitaciones del ADC).

### 1.1 Hipótesis general (investigación)

La hipótesis general (de investigación) del proyecto establece, en términos de factibilidad técnico-económica y métricas de desempeño, que:

$H_i$: Es factible desarrollar un sistema de monitoreo eléctrico residencial basado en IoT que, mediante el uso de hardware de código abierto y componentes genéricos optimizados (ESP32, SCT-013, ZMPT101B), reduzca los costos de manufactura por debajo de los \$600.00 MXN por unidad, manteniendo un error de medición de potencia activa inferior al 5% en cargas domésticas estándar superiores a 25 W.

Esta hipótesis integra variables **económicas** (costo) y **metrológicas** (error de potencia activa) con un umbral explícito, lo que permite validación mediante experimentación y análisis estadístico.

### 1.2 Hipótesis nula

La hipótesis nula se formula como la negación operacional de la hipótesis de investigación:

$H_0$: El sistema propuesto no alcanza la precisión requerida (error porcentual $> 5\%$) o su costo de manufactura excede los \$600.00 MXN por unidad, invalidando la viabilidad técnico-económica de la propuesta.

### 1.3 Hipótesis alternativa

En el enfoque clásico de contraste, puede formularse una hipótesis alternativa equivalente a la de investigación, expresada en sentido afirmativo (diferente de la nula):

$H_1$: El sistema propuesto logra un costo de manufactura ≤ \$600.00 MXN por unidad y alcanza un error porcentual de potencia activa ≤ 5% en cargas domésticas superiores a 25 W, cumpliendo la viabilidad técnico-económica definida.

En este proyecto, $H_1$ y $H_i$ son operacionalmente consistentes, ya que ambas especifican criterios de aceptación cuantitativos.

### 1.4 Hipótesis específicas (operacionales)

Las hipótesis específicas permiten descomponer la hipótesis general en componentes verificables:

1. **Linealidad del sensado de corriente:** el SCT-013-030, con acondicionamiento (offset a 1.65 V), mantiene relación lineal con la corriente real con $R^2 > 0.98$ (0.5 A a 30 A).
2. **Estabilidad de la fuente conmutada:** la fuente integrada tipo Hi-Link presenta rizado menor a 50 mVpp, sin introducir ruido significativo al ADC.
3. **Cálculo de potencia activa real:** la medición simultánea de $v[n]$ e $i[n]$ permite calcular $P$ por promedio del producto instantáneo, mejorando la precisión frente a aproximaciones con voltaje nominal constante.
4. **Viabilidad económica:** la BOM no excede \$600.00 MXN, con reducción de costo de al menos 60% respecto a alternativas comerciales comparables.

La comprobación de estas hipótesis se vincula con el procedimiento experimental, las técnicas de análisis y la presentación gráfica definidas en el marco metodológico.

---

## 2. Bosquejo del método (plan estructurado de investigación)

El **bosquejo del método** es el plan que define cómo se obtendrán, registrarán y analizarán los datos para evaluar las hipótesis. En este proyecto, el método se diseña para asegurar:

- **Validez interna** en la calibración (laboratorio, cargas controladas).
- **Validez externa** en operación real (campo, vivienda residencial).
- Repetibilidad, trazabilidad y comparación con un **instrumento patrón** (multímetro TRMS calibrado).

### 2.1 Tipo y diseño de investigación

La clasificación metodológica del estudio es la siguiente:

| Criterio | Clasificación | Justificación técnica |
|---|---|---|
| Finalidad | Aplicada y tecnológica | Se aplica teoría consolidada (Faraday, Nyquist-Shannon, DSP) a un prototipo funcional. |
| Enfoque de datos | Cuantitativa | Se analizan magnitudes numéricas: $I_{RMS}$, $V_{RMS}$, $P$, MAPE, $R^2$, costo. |
| Alcance | Correlacional y explicativa | Se busca correlación prototipo vs patrón y se explican desviaciones (ruido ADC, rango sensor). |
| Lugar | Mixta (laboratorio y campo) | Calibración controlada + validación en vivienda real. |
| Manipulación | Experimental | Se manipula la carga (independiente) y se observa la respuesta metrológica (dependiente). |

---

## 3. Universo (población) y muestra

### 3.1 Universo (población de estudio)

En un estudio de ingeniería experimental con prototipos, el universo no se define por sujetos humanos, sino por el conjunto de **condiciones de medición** posibles. Para este proyecto, la población corresponde al conjunto de condiciones de carga eléctrica que pueden presentarse en una vivienda residencial monofásica, dentro del rango de operación del sensor de corriente (0 a 30 A).

### 3.2 Muestra

La muestra se define como un conjunto finito y controlado de condiciones experimentales (niveles discretos de corriente/carga) seleccionadas deliberadamente para cubrir el rango operativo del sistema:

- Niveles: 0.5 A, 1 A, 2 A, 5 A, 10 A, 15 A, 20 A, 25 A y 30 A.
- Repeticiones: mínimo de 30 mediciones por nivel.
- Tamaño mínimo: 270 pares de observaciones (prototipo vs patrón).
- Muestreo: **no probabilístico intencional** (selección por cobertura del rango y relevancia metrológica).

**Criterios de inclusión:** cargas resistivas puras (lámparas incandescentes, resistencias) y cargas inductivas comunes (motores fraccionarios, ventiladores), en circuito monofásico 127 V/60 Hz.

**Criterios de exclusión:** corrientes inferiores a 0.2 A (zona muerta del ADC), cargas trifásicas y equipos con distorsión armónica extrema fuera del alcance del prototipo.

---

## 4. Instrumento (técnicas e instrumentos de recolección)

Un **instrumento** es el medio técnico mediante el cual se capturan datos de las variables de interés. En este proyecto, el instrumento principal es un sistema de medición eléctrica, no un cuestionario; por tanto, **no aplica una escala Likert**, ya que no se evalúan percepciones subjetivas.

### 4.1 Instrumentos y su función

| Instrumento | Función | Especificaciones relevantes |
|---|---|---|
| Prototipo SME-IoT (ESP32 + SCT-013 + ZMPT101B) | Dispositivo bajo prueba (DUT) | ADC 12 bits; muestreo ~1 kHz; sensores en ADC1; cálculo $I_{RMS}$, $V_{RMS}$ y $P$. |
| Multímetro TRMS calibrado | Instrumento patrón | Precisión típica ±0.5%; True RMS; referencia de comparación. |
| Cargas conocidas | Condiciones controladas | Resistivas (60 W, 100 W, 200 W) e inductivas/no lineales típicas. |
| microSD + registro temporal | Persistencia y trazabilidad | Registro con *timestamp* para continuidad de datos. |
| UART/monitor serial | Exportación y depuración | Salida a CSV para análisis en software externo. |

---

## 5. Prueba piloto

La **prueba piloto** es una aplicación previa y acotada del procedimiento, cuyo objetivo es detectar fallas del instrumento, errores de configuración y problemas de registro antes de la campaña experimental completa.

En este proyecto, una prueba piloto técnicamente adecuada consiste en:

- Seleccionar 2–3 niveles de carga (p. ej., 0.5 A, 5 A, 15 A).
- Verificar estabilización térmica mínima (≥5 min) y ausencia de saturación del ADC.
- Confirmar consistencia de lectura del prototipo frente al patrón en repetidas lecturas.
- Verificar que el registro en microSD/UART sea íntegro (sin valores faltantes, con formato consistente).
- Validar que el cálculo de potencia activa mediante muestras instantáneas produzca valores coherentes para cargas resistivas (factor de potencia cercano a 1) y que se observe variación esperada en cargas inductivas.

---

## 6. Recolección de datos

La **recolección** corresponde a la obtención sistemática de datos en condiciones definidas. En este proyecto se emplean:

1. **Observación estructurada:** registro simultáneo de lecturas del prototipo y del instrumento patrón bajo condiciones idénticas.
2. **Registro automatizado:** almacenamiento de métricas procesadas con marca temporal (microSD) y/o exportación por UART a CSV.
3. **Barrido escalonado de carga:** mediciones sucesivas incrementando progresivamente la carga, con puntos predefinidos y repeticiones.

El procedimiento completo incluye cuatro fases: calibración en laboratorio, validación con cargas mixtas, pruebas de campo (24–72 h) y análisis de robustez ante condiciones adversas (atenuación WiFi, transitorios, cortes).

---

## 7. Procesamiento de datos

El **procesamiento** consiste en preparar los datos para el análisis, garantizando consistencia y reduciendo errores sistemáticos de registro. Las acciones mínimas recomendadas incluyen:

- Consolidación de datos (CSV) provenientes de UART/microSD.
- Validación de integridad: detección de registros incompletos, duplicados o fuera de rango.
- Normalización de unidades y formatos (A, V, W, kWh; marcas temporales).
- Organización tabular por nivel de carga y condición (resistiva/inductiva).

Las herramientas propuestas en el proyecto incluyen Python (NumPy, Pandas, Matplotlib, SciPy) y Excel como apoyo tabular.

---

## 8. Análisis de datos

El **análisis** busca responder, con evidencia cuantitativa, si los criterios de las hipótesis se cumplen. En este proyecto se emplean técnicas estadísticas y metrológicas apropiadas para comparar métodos de medición:

### 8.1 Métricas y pruebas

- Estadística descriptiva: media ($\bar{x}$), desviación estándar ($\sigma$), rango y coeficiente de variación.
- Error Porcentual Absoluto Medio (MAPE):

$$
MAPE = \frac{1}{n} \sum_{i=1}^{n} \left| \frac{Patr\acute{o}n_i - Prototipo_i}{Patr\acute{o}n_i} \right| \times 100
$$

Criterio de aceptación: $MAPE < 5\%$ (en el rango objetivo >25 W).

- Correlación de Pearson ($r$): se espera $r > 0.99$.
- Coeficiente de determinación ($R^2$): se espera $R^2 > 0.98$.
- Regresión lineal: obtención de ecuación de calibración $y = mx + b$ (ideal: $m\approx 1$, $b\approx 0$).
- Prueba t de Student pareada: contraste de igualdad de medias de diferencias ($H_0$: $\bar{d}=0$) cuando corresponda.
- Bland–Altman: evaluación de concordancia (diferencias vs promedios) y límites de concordancia $\pm 1.96\sigma$.

### 8.2 Coherencia con resultados preliminares

El documento maestro reporta resultados preliminares compatibles con los criterios de aceptación para cargas medias/altas (p. ej., $R^2 > 0.98$ y MAPE aproximado de ±2.3% para cargas >200 W), así como una degradación esperada en el rango de cargas muy bajas (<50 W) atribuible a resolución y ruido del ADC.

---

## 9. Presentación gráfica de resultados

La **presentación gráfica** traduce los resultados numéricos a evidencia visual clara. Para este proyecto, la entrega mínima recomendada incluye:

- **Gráfico de dispersión** Prototipo vs Patrón (corriente, voltaje y potencia) con recta de regresión y reporte de $R^2$.
- **Bland–Altman** para potencia activa: diferencias vs promedios, con media de diferencias y límites de concordancia.
- **Curva de error** (MAPE o $E_{\%}$) por nivel de carga, destacando el umbral >25 W.
- **Series temporales** de $P$ y energía acumulada (kWh) en pruebas de campo.
- Tablas resumen por condición (resistiva/inductiva) y por fase (laboratorio/campo).

---

## 10. Conclusiones (síntesis)

- Las hipótesis del proyecto son **comprobables** porque fijan umbrales cuantitativos (costo, error, $R^2$, MAPE) y definen claramente qué se considera éxito técnico.
- El bosquejo metodológico establece un proceso de validación con instrumentación patrón, repetición suficiente y análisis estadístico apropiado para comparación de métodos.
- La combinación de fases (laboratorio y campo) permite evaluar el desempeño bajo condiciones controladas y reales, incluyendo limitaciones técnicas declaradas (ADC, conectividad, instalación).
- Los datos procesados y analizados permiten emitir decisiones fundamentadas sobre la viabilidad del prototipo como instrumento informativo no fiscal, coherente con el marco legal y normativo descrito en el documento maestro.

---

## 11. Referencias (formato APA 7)

American Psychological Association. (2020). *Publication manual of the American Psychological Association* (7th ed.). American Psychological Association. https://apastyle.apa.org/

Bland, J. M., & Altman, D. G. (1986). Statistical methods for assessing agreement between two methods of clinical measurement. *The Lancet*, *1*(8476), 307–310. https://pubmed.ncbi.nlm.nih.gov/2868172/

Comisión Federal de Electricidad. (2024). *Tarifas domésticas de energía eléctrica*. CFE. https://app.cfe.mx/Aplicaciones/CCFE/Tarifas/TarifasCRECasa/Casa.aspx

Creswell, J. W., & Creswell, J. D. (2018). *Research design: Qualitative, quantitative, and mixed methods approaches* (5th ed.). SAGE Publications.

Espressif Systems. (2022). *ESP32 Series Datasheet* (ver. 3.4). Espressif Systems. https://www.espressif.com/documentation/esp32_datasheet_en.pdf

Hart, D. W. (2011). *Power electronics*. McGraw-Hill Education.

Hart, G. W. (1992). Nonintrusive appliance load monitoring. *Proceedings of the IEEE*, *80*(12), 1870–1891.

Hernández Sampieri, R., Fernández Collado, C., & Baptista Lucio, M. del P. (2014). *Metodología de la investigación* (6ª ed.). McGraw-Hill Education.

Kaselimi, M., Protopapadakis, E., Voulodimos, A., Doulamis, N. & Doulamis, A. (2022). Towards Trustworthy Energy Disaggregation: A Review of Challenges, Methods, and Perspectives for Non-Intrusive Load Monitoring. *Sensors*, *22*(15), 5872. https://doi.org/10.3390/s22155872

Naciones Unidas. (2015). *Transformar nuestro mundo: La Agenda 2030 para el Desarrollo Sostenible*. Asamblea General de las Naciones Unidas. https://sdgs.un.org/2030agenda

OASIS. (2019). *MQTT Version 5.0* (OASIS Standard). OASIS Open. https://docs.oasis-open.org/mqtt/mqtt/v5.0/mqtt-v5.0.html

Oppenheim, A. V., & Willsky, A. S. (2014). *Signals and systems* (2nd ed.). Pearson Education.

Shapiro, S. S., & Wilk, M. B. (1965). An analysis of variance test for normality (complete samples). *Biometrika*, *52*(3–4), 591–611. https://doi.org/10.1093/biomet/52.3-4.591

Tamayo y Tamayo, M. (2009). *El proceso de la investigación científica: Incluye evaluación y administración de proyectos de investigación* (5. ed.). Limusa.

---

## Anexo A. Orden sugerida para ampliación/verificación de fuentes con MCP (para agente)

Si se requiere fortalecer o auditar las referencias (edición exacta, páginas, URL/DOI estables), priorizar el siguiente flujo usando herramientas MCP de web:

1. Consultar las páginas oficiales (DOI/publisher) y repositorios bibliográficos abiertos (p. ej., PubMed, Open Library) para confirmar: autores, año, título, revista/editorial, volumen/edición y páginas.
2. Para Bland–Altman, obtener la ficha completa desde PubMed y, si se necesita, seguir el enlace al editor (Elsevier/Lancet) para el identificador PII.
3. Para Shapiro–Wilk, validar metadatos en Oxford Academic (Biometrika) y el DOI.
4. Para Tamayo y Tamayo, confirmar edición y editorial en Open Library y, si se requiere, contrastar con un catálogo institucional (biblioteca universitaria) para concordancia.
5. Normalizar todas las entradas al estilo APA 7 y asegurar consistencia entre citas en texto y lista final.
