<!--
===================================================================
METADATOS DEL DOCUMENTO (Referencia interna para IA)
===================================================================
Título      : Marco Metodológico y Fundamentos de la Investigación
Subtítulo   : Diseño e Implementación de un Sistema IoT de Bajo
              Costo para la Monitorización No Intrusiva de Consumo
              Eléctrico Residencial mediante Arquitectura ESP32
Autor       : Investigador
Fecha       : 2026-03-17
Materia     : Taller de Investigación 1 — Tarea 2
Idioma      : es-MX
Fuente      : Proyecto completo.md (documento maestro vigente)
Flujo PDF   : Markdown → Joplin → PDF
Notas       : Las cifras monetarias usan \$ para evitar
              renderizado LaTeX. Sin índice ni anclas de
              navegación. Estilo revista de divulgación
              científica con elementos visuales.
===================================================================
-->

# Diseño e Implementación de un Sistema IoT de Bajo Costo para la Monitorización No Intrusiva de Consumo Eléctrico Residencial mediante Arquitectura ESP32

---

## Tipos de Investigación

> *¿Qué enfoques metodológicos guían este proyecto?*

La presente investigación se clasifica metodológicamente de acuerdo con múltiples criterios que definen tanto su naturaleza como su alcance. Esta clasificación permite situar el trabajo dentro de un marco epistemológico claro y justificar las decisiones de diseño adoptadas a lo largo del proceso investigativo.

### Según su finalidad: Investigación Aplicada y Tecnológica

El proyecto no busca formular nuevas leyes fundamentales del electromagnetismo ni de la teoría de señales, sino que aplica conocimientos teóricos consolidados para resolver una problemática práctica concreta. Los principios físicos que sustentan el sistema —la Ley de Faraday para la inducción electromagnética en transformadores de corriente, el teorema de Nyquist-Shannon para la digitalización de señales analógicas, y los protocolos TCP/IP para la comunicación inalámbrica— son conceptos ampliamente validados en la literatura científica (Hart, 2011; Oppenheim y Willsky, 2014).

El producto final de esta investigación es un prototipo tecnológico tangible: un dispositivo funcional capaz de medir potencia eléctrica en tiempo real. Esta orientación hacia la resolución de problemas prácticos mediante la transferencia de conocimiento teórico a aplicaciones concretas define el carácter aplicado del estudio (Hernández Sampieri et al., 2014).

### Según el enfoque de datos: Investigación Cuantitativa

La validación del sistema depende exclusivamente de variables numéricas medibles. Las magnitudes fundamentales incluyen corriente eficaz ($I_{RMS}$) expresada en amperios, voltaje eficaz ($V_{RMS}$) en volts, y potencia activa ($P$) en watts. Los indicadores de desempeño del prototipo —error porcentual ($E_{\%}$) y coeficiente de determinación ($R^2$)— son igualmente cuantitativos.

No se analizan percepciones subjetivas del usuario ni valoraciones cualitativas sobre la experiencia de uso. La investigación opera bajo el paradigma positivista, donde la realidad se mide objetivamente y los resultados se expresan en términos estadísticos verificables.

### Según su alcance: Investigación Correlacional y Explicativa

El estudio opera en dos niveles de profundidad complementarios. En el **nivel correlacional**, se evalúa la relación estadística entre las mediciones del prototipo y las de un instrumento patrón certificado. El objetivo es demostrar una correlación lineal positiva fuerte ($r \approx 1$), lo que validaría la capacidad del dispositivo para reproducir las lecturas de referencia.

En el **nivel explicativo**, se investigan las causas de las desviaciones observadas entre ambas mediciones. Factores como el ruido inherente del convertidor analógico-digital (ADC) del ESP32, la resolución limitada de los sensores, y el efecto de la carga del *burden resistor* sobre la linealidad del transformador de corriente, son analizados sistemáticamente para comprender —no solo describir— el comportamiento del sistema (Espressif Systems, 2022).

### Según el lugar de realización: Investigación Mixta (Laboratorio y Campo)

El diseño metodológico integra dos entornos de validación con características distintas:

- **Fase de laboratorio.** Las pruebas de calibración del sensor SCT-013 y el ajuste de la fuente conmutada se realizan con cargas conocidas bajo condiciones controladas. El entorno de laboratorio permite aislar variables intervinientes y establecer la curva de calibración del sistema.

- **Fase de campo.** Una vez calibrado, el prototipo se instala en una vivienda residencial real en la zona metropolitana de Toluca, Estado de México. En esta fase, el sistema queda expuesto a variables no controladas: fluctuaciones de voltaje de la red pública, armónicos generados por cargas no lineales, y variaciones de temperatura ambiente.

Esta combinación de entornos garantiza tanto la validez interna (laboratorio) como la validez externa (campo) de los resultados obtenidos.

### Según la manipulación de variables: Investigación Experimental

Se manipula deliberadamente la carga eléctrica conectada al circuito de prueba (variable independiente) para observar la respuesta del algoritmo de medición implementado en el ESP32 (variable dependiente). Las variables intervinientes, como el voltaje de alimentación del microcontrolador y la temperatura ambiente, se controlan o documentan durante el experimento.

El diseño experimental permite establecer relaciones causales entre las variaciones de carga y las lecturas del prototipo, superando las limitaciones de los estudios puramente observacionales.

**Síntesis metodológica:**

| Criterio | Clasificación |
|---|---|
| Finalidad | Aplicada y Tecnológica |
| Enfoque de datos | Cuantitativa |
| Alcance | Correlacional y Explicativa |
| Lugar de realización | Mixta (Laboratorio y Campo) |
| Manipulación de variables | Experimental |

---

## Técnicas de Recolección de Información

> *¿Cómo se obtienen los datos para validar el sistema?*

La recolección de datos constituye una etapa crítica del proceso experimental. Las técnicas e instrumentos seleccionados determinan la calidad de la información obtenida y, por tanto, la validez de las conclusiones derivadas del estudio. A continuación se describen los instrumentos de medición y las técnicas empleadas para la captura sistemática de datos.

### Instrumentos de Medición

La investigación emplea una combinación de instrumentos que permite comparar las mediciones del prototipo con valores de referencia calibrados:

| Instrumento | Función | Especificaciones |
|---|---|---|
| Prototipo SME-IoT | Dispositivo bajo prueba | ADC de 12 bits; muestreo ~1 kHz; rango 0-30 A |
| Multímetro TRMS | Instrumento patrón | Precisión ±0.5%; medición *True RMS* |
| Cargas conocidas | Generación de condiciones controladas | Resistivas (lámparas) e inductivas (motores) |
| Módulo microSD | Almacenamiento local | Registro con marca temporal; capacidad 4 GB |
| Monitor serial UART | Depuración en tiempo real | Exportación directa a formato CSV |

El **prototipo SME-IoT** integra el microcontrolador ESP32, el sensor de corriente SCT-013-030 y el sensor de voltaje ZMPT101B. La configuración del ADC utiliza exclusivamente pines del bloque ADC1 (GPIOs 32-39) para evitar el conflicto documentado con el módulo WiFi (Espressif Systems, 2022).

El **multímetro TRMS** de referencia proporciona las lecturas de comparación. Su capacidad de medir el valor eficaz verdadero (*True RMS*) garantiza que las comparaciones sean válidas incluso con formas de onda distorsionadas por armónicos.

### Técnicas de Recolección

Las técnicas empleadas combinan observación sistemática con registro automatizado:

**1. Observación directa estructurada.** El investigador registra simultáneamente las lecturas del prototipo y del instrumento patrón bajo condiciones idénticas de carga. Se utiliza un formato de registro estandarizado que documenta la fecha, hora, nivel de carga aplicado, y los valores de corriente, voltaje y potencia reportados por ambos instrumentos.

**2. Registro automatizado.** El firmware del ESP32 almacena las muestras procesadas en una tarjeta microSD con marca temporal (*timestamp*). Esta automatización elimina los errores de transcripción manual y permite la captura de datos a intervalos regulares durante periodos prolongados. El formato de almacenamiento (CSV) facilita el procesamiento posterior mediante software estadístico.

**3. Barrido de carga escalonado.** Las mediciones se realizan incrementando progresivamente la carga desde el mínimo detectable (0.5 A) hasta el máximo del sensor (30 A). Los niveles predefinidos —0.5 A, 1 A, 2 A, 5 A, 10 A, 15 A, 20 A, 25 A y 30 A— garantizan la cobertura del rango operativo completo. Se realizan un mínimo de 30 repeticiones en cada nivel, generando al menos 270 pares de observaciones para el análisis estadístico.

### Población y Muestra

En investigaciones experimentales de ingeniería con prototipos, el concepto de población se desplaza del ámbito de los sujetos humanos al de las condiciones de medición:

| Concepto | Definición |
|---|---|
| Población | Todas las posibles condiciones de carga eléctrica en vivienda monofásica (0-30 A) |
| Muestra | Mediciones en niveles discretos de carga seleccionados intencionalmente |
| Tipo de muestreo | No probabilístico intencional |

Los **criterios de inclusión** abarcan cargas resistivas puras (lámparas incandescentes, resistencias de potencia) y cargas inductivas comunes (motores fraccionarios, ventiladores), conectadas a circuito monofásico de 127 V / 60 Hz.

Los **criterios de exclusión** comprenden cargas trifásicas, cargas con corriente inferior a 0.2 A (zona muerta del ADC), y equipos con distorsión armónica extrema como soldadoras de arco o variadores de frecuencia industriales.

---

## Planteamiento del Problema

> *¿Cuál es el problema central que aborda esta investigación?*

### Descripción del Problema

El problema central radica en la **desconexión estructural** entre el consumo físico de energía eléctrica en viviendas residenciales mexicanas y la conciencia que el usuario posee sobre dicho consumo. Sin herramientas de diagnóstico accesibles, resulta imposible para una familia identificar electrodomésticos ineficientes, detectar consumos fantasma en modo *standby*, o correlacionar hábitos de uso con el costo reflejado en la facturación de la Comisión Federal de Electricidad (CFE).

Esta opacidad informativa convierte al usuario en un agente pasivo de su propio gasto energético, incapaz de intervenir de forma racional sobre las variables que determinan el monto de su recibo eléctrico (CFE, 2024).

### Formulación del Problema Específico

Los hogares mexicanos con servicio eléctrico monofásico carecen de un instrumento de medición de potencia activa real que cumpla **simultáneamente** los siguientes requisitos:

1. **Asequible** — costo inferior a \$600.00 MXN
2. **Preciso** — error porcentual inferior al 5% para cargas superiores a 25 W
3. **Seguro** — instalación no intrusiva, sin manipulación de cableado
4. **Informativo en tiempo real** — datos locales y remotos de forma instantánea

Las alternativas existentes presentan barreras significativas:

| Solución | Limitación principal | Costo aprox. (MXN) |
|---|---|---|
| Emporia Vue | Importación, plataforma propietaria | >\$1,800 |
| Shelly EM | Importación, semi-intrusivo | >\$1,500 |
| OpenEnergyMonitor emonTx | Sin WiFi nativo, componentes importados | >\$2,000 |
| Medidor CFE | Sin datos en tiempo real al usuario | N/A |

### Causas del Problema

Las causas son de naturaleza multifactorial y convergen en un ciclo de desinformación energética:

**Opacidad de la medición fiscal.** Los medidores de la CFE no ofrecen interfaces de datos instantáneos dentro de la vivienda. Toda información llega con un retraso de semanas o meses que invalida cualquier corrección de hábitos en tiempo real (CFE, 2024).

**Barrera económica de acceso.** El costo de las soluciones comerciales disponibles —agravado por aranceles de importación, costos logísticos y depreciación cambiaria— las sitúa fuera del alcance del usuario residencial promedio.

**Complejidad de instalación.** Numerosas soluciones requieren intervención intrusiva en el tablero eléctrico principal, lo que implica riesgos de seguridad y la necesidad de mano de obra especializada conforme a la NOM-001-SEDE-2012.

**Invisibilidad inherente del recurso.** La electricidad es una magnitud intangible cuyo consumo no es perceptible por los sentidos humanos, dificultando la formación de una cultura de ahorro energético sin herramientas de visualización.

**Variabilidad del suministro eléctrico.** Las fluctuaciones de voltaje en la red pública mexicana —fenómeno frecuente en zonas suburbanas— distorsionan las estimaciones de consumo basadas en voltaje nominal constante e introducen un error sistemático.

### Efectos del Problema

Los efectos son cuantificables y afectan múltiples dimensiones:

- **Económico.** Sobrecostos en la facturación eléctrica y riesgo permanente de caer en tarifa DAC, con impacto financiero directo sobre el presupuesto familiar.

- **Desperdicio energético.** Los consumos fantasma en modo *standby* —entre un 5% y un 10% del consumo total del hogar según la Agencia Internacional de Energía (IEA, 2014)— permanecen invisibles e incorregidos durante años.

- **Ambiental.** El desperdicio acumulado a escala de millones de hogares incrementa la demanda agregada sobre la red eléctrica nacional, aumentando la generación y las emisiones de CO2.

- **Integridad de equipos.** Las variaciones de voltaje no diagnosticadas deterioran prematuramente motores de electrodomésticos y circuitos electrónicos sensibles.

---

## Objetivos de la Investigación

> *¿Qué se busca lograr con este proyecto?*

### Objetivo General

Diseñar, implementar y validar un sistema de monitoreo de consumo eléctrico residencial de bajo costo y no intrusivo, basado en el microcontrolador ESP32 y sensores de corriente tipo *clamp* (SCT-013) y de voltaje (ZMPT101B), capaz de calcular la potencia activa en tiempo real con un error inferior al 5% respecto a instrumentación de referencia, y de transmitir los datos de manera inalámbrica mediante conectividad WiFi.

### Objetivos Específicos

1. **Analizar** los requerimientos funcionales y no funcionales del sistema de monitoreo con base en las condiciones de la infraestructura eléctrica residencial mexicana y las restricciones técnicas de los componentes seleccionados.

2. **Diseñar** la etapa de hardware del sistema, incluyendo el circuito de acondicionamiento de señal para los sensores SCT-013 y ZMPT101B, y el sistema de alimentación conmutada AC-DC integrado.

3. **Desarrollar** el firmware de adquisición de datos, procesamiento digital de señales —cálculo de corriente eficaz ($I_{RMS}$), voltaje eficaz ($V_{RMS}$) y potencia activa ($P$)— y transmisión inalámbrica, sobre la arquitectura de doble núcleo del ESP32.

4. **Implementar** la interfaz de usuario local (pantalla OLED SSD1306 vía protocolo I2C) y el módulo de almacenamiento local (tarjeta microSD) para la visualización de métricas en tiempo real y el registro histórico de datos.

5. **Validar** el desempeño del prototipo mediante pruebas comparativas contra instrumentación patrón (multímetro TRMS calibrado) en condiciones controladas de laboratorio y en una instalación residencial real.

6. **Evaluar** la viabilidad económica del dispositivo mediante el análisis de la lista de materiales (BOM) y la comparación porcentual de costos frente a soluciones comerciales del mercado.

---

## Justificación

> *¿Por qué es relevante esta investigación?*

La justificación del proyecto se articula en cinco ejes, siguiendo los criterios de evaluación propuestos por Hernández Sampieri, Fernández Collado y Baptista Lucio (2014):

### Conveniencia

El dispositivo proporciona al usuario residencial retroalimentación instantánea sobre su consumo eléctrico, a diferencia de los medidores fiscales de la CFE, cuya única interfaz de información es el recibo bimestral acumulado. Esta inmediatez en la retroalimentación es un requisito indispensable para la modificación efectiva de hábitos de consumo (CFE, 2024).

### Relevancia Social

Los principales beneficiarios son las familias de clase media y media-baja en México, particularmente aquellas en riesgo de incurrir en la Tarifa Doméstica de Alto Consumo (DAC). Reducir el costo de adquisición a ~\$600.00 MXN —frente a los >\$1,500.00 MXN de alternativas comerciales de importación— democratiza el acceso a tecnología de medición inteligente para un segmento de la población que históricamente ha carecido de ella.

### Implicaciones Prácticas

El diseño no intrusivo, basado en un sensor de corriente de núcleo partido que se instala alrededor del conductor sin desconectarlo, elimina riesgos de manipulación del cableado eléctrico. La fuente conmutada AC-DC integrada permite una instalación autónoma sin adaptadores externos ni puertos USB, simplificando el proceso de instalación para usuarios sin conocimientos técnicos especializados.

### Valor Teórico

La investigación valida la aplicabilidad de principios consolidados en una plataforma de hardware con restricciones severas de costo:

- **Ley de Faraday** — inducción electromagnética en el transformador de corriente SCT-013 (Hart, 2011)
- **Teorema de Nyquist-Shannon** — frecuencias de muestreo del ADC para evitar aliasing (Oppenheim y Willsky, 2014)
- **Algoritmos de procesamiento digital de señales** — cálculo de potencia activa mediante el promedio del producto instantáneo de muestras de voltaje y corriente

### Utilidad Metodológica

Se propone un protocolo de calibración replicable para sensores tipo *clamp* con ADC de resolución limitada (12 bits), documentado de forma abierta y transferible a contextos académicos e industriales de bajo presupuesto. Este protocolo puede ser adoptado por futuros investigadores o desarrolladores que enfrenten restricciones similares de hardware.

### Pertinencia Global

El proyecto se inscribe en la agenda de sostenibilidad energética de las Naciones Unidas (2015), articulado con dos Objetivos de Desarrollo Sostenible:

- **ODS 7** — Energía asequible y no contaminante
- **ODS 12** — Producción y consumo responsables

Al mismo tiempo, responde a una necesidad concreta y documentada del contexto socioeconómico mexicano: la ausencia de herramientas accesibles de diagnóstico energético para el usuario residencial.

---

## Referencias

Comisión Federal de Electricidad. (2024). *Tarifas domésticas de energía eléctrica*. CFE. https://app.cfe.mx/Aplicaciones/CCFE/Tarifas/TarifasCRECasa/Casa.aspx

Espressif Systems. (2022). *ESP32 Series Datasheet* (ver. 3.4). https://www.espressif.com/documentation/esp32_datasheet_en.pdf

Hart, D. W. (2011). *Power Electronics*. McGraw-Hill Education.

Hernández Sampieri, R., Fernández Collado, C., y Baptista Lucio, M. del P. (2014). *Metodología de la investigación* (6.a ed.). McGraw-Hill Education.

International Energy Agency. (2014). *More Data, Less Energy: Making Network Standby More Efficient in Billions of Connected Devices*. IEA. https://www.iea.org/reports/more-data-less-energy

Naciones Unidas. (2015). *Transformar nuestro mundo: La Agenda 2030 para el Desarrollo Sostenible*. Asamblea General de las Naciones Unidas. https://sdgs.un.org/2030agenda

Norma Oficial Mexicana NOM-001-SEDE-2012. (2012). *Instalaciones Eléctricas (Utilización)*. Diario Oficial de la Federación, México.

Oppenheim, A. V., y Willsky, A. S. (2014). *Signals and Systems* (2nd ed.). Pearson Education.
