<!--
===================================================================
METADATOS DEL DOCUMENTO (Referencia interna para IA)
===================================================================
Título      : Definición del Proyecto y Planteamiento del Problema
Subtítulo   : Diseño e Implementación de un Sistema IoT de Bajo
              Costo para la Monitorización No Intrusiva de Consumo
              Eléctrico Residencial mediante Arquitectura ESP32
Autor       : Investigador
Fecha       : 2026-03-03
Materia     : Taller de Investigación 1 — Tarea 1
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

## Definición del Proyecto

El proyecto **SME-IoT** (*Sistema de Monitoreo Eléctrico – Internet of Things*) propone el desarrollo de un prototipo funcional de medición inteligente capaz de cuantificar en tiempo real la potencia activa consumida en una vivienda, empleando exclusivamente componentes electrónicos genéricos de bajo costo disponibles en el mercado nacional mexicano.

**Datos clave del prototipo:**

| Característica | Valor |
|---|---|
| Microcontrolador | ESP32 (doble núcleo, WiFi integrado) |
| Sensor de corriente | SCT-013-030 (no intrusivo, tipo *clamp*) |
| Sensor de voltaje | ZMPT101B (aislamiento galvánico) |
| Costo total de materiales | ~\$600.00 MXN por unidad |
| Precisión objetivo | Error < 5% en cargas > 25 W |
| Conectividad | WiFi 2.4 GHz nativo |
| Almacenamiento local | Tarjeta microSD con marca temporal |

## Justificación

> *¿Por qué este proyecto?*

La justificación se articula en cinco ejes, siguiendo los criterios de evaluación propuestos por Hernández Sampieri, Fernández Collado y Baptista Lucio (2014):

- **Conveniencia.** El dispositivo proporciona al usuario residencial retroalimentación instantánea sobre su consumo eléctrico, a diferencia de los medidores fiscales de la Comisión Federal de Electricidad (CFE), cuya única interfaz de información es el recibo bimestral acumulado (CFE, 2024).

- **Relevancia social.** Los principales beneficiarios son las familias de clase media y media-baja en México, particularmente aquellas en riesgo de incurrir en la Tarifa Doméstica de Alto Consumo (DAC). Reducir el costo de adquisición a ~\$600.00 MXN —frente a los >\$1,500.00 MXN de alternativas comerciales de importación— democratiza el acceso a tecnología de medición inteligente para un segmento de la población que históricamente ha carecido de ella.

- **Implicaciones prácticas.** El diseño no intrusivo, basado en un sensor de corriente de núcleo partido que se instala alrededor del conductor sin desconectarlo, elimina riesgos de manipulación del cableado eléctrico. La fuente conmutada AC-DC integrada permite una instalación autónoma sin adaptadores externos ni puertos USB.

- **Valor teórico.** La investigación valida la aplicabilidad de principios consolidados en una plataforma de hardware con restricciones severas de costo:
  - Ley de Faraday → inducción electromagnética en el SCT-013 (Hart, 2011)
  - Teorema de Nyquist-Shannon → frecuencias de muestreo del ADC (Oppenheim y Willsky, 2014)
  - Algoritmos de procesamiento digital de señales → cálculo de potencia activa real

- **Utilidad metodológica.** Se propone un protocolo de calibración replicable para sensores tipo *clamp* con ADC de resolución limitada (12 bits), documentado de forma abierta y transferible a contextos académicos e industriales de bajo presupuesto.

## Pertinencia global

El proyecto se inscribe en la agenda de sostenibilidad energética de las Naciones Unidas (2015), articulado con dos Objetivos de Desarrollo Sostenible:

- **ODS 7** — Energía asequible y no contaminante
- **ODS 12** — Producción y consumo responsables

Al mismo tiempo, responde a una necesidad concreta y documentada del contexto socioeconómico mexicano: la ausencia de herramientas accesibles de diagnóstico energético para el usuario residencial.

---

## Planteamiento del Problema

### Descripción del problema

> *¿Cuál es el problema?*

El problema central radica en la **desconexión estructural** entre el consumo físico de energía eléctrica en viviendas residenciales mexicanas y la conciencia que el usuario posee sobre dicho consumo. Sin herramientas de diagnóstico accesibles, resulta imposible para una familia:

- Identificar electrodomésticos ineficientes
- Detectar consumos fantasma en modo *standby*
- Correlacionar hábitos de uso con el costo reflejado en la facturación de la CFE

Esta opacidad informativa convierte al usuario en un agente pasivo de su propio gasto energético, incapaz de intervenir de forma racional sobre las variables que determinan el monto de su recibo eléctrico.

### Formulación del problema específico

Los hogares mexicanos con servicio eléctrico monofásico carecen de un instrumento de medición de potencia activa real que cumpla **simultáneamente** los siguientes requisitos:

1. **Asequible** — costo inferior a \$600.00 MXN
2. **Preciso** — error porcentual inferior al 5% para cargas superiores a 25 W
3. **Seguro** — instalación no intrusiva, sin manipulación de cableado
4. **Informativo en tiempo real** — datos locales y remotos de forma instantánea

Las alternativas existentes presentan barreras significativas:

| Solución | Limitación principal | Costo aprox. (MXN) |
|---|---|---|
| **Emporia Vue** | Importación, plataforma propietaria | >\$1,800 |
| **Shelly EM** | Importación, semi-intrusivo | >\$1,500 |
| **OpenEnergyMonitor emonTx** | Sin WiFi nativo, componentes importados | >\$2,000 |
| **Medidor CFE** | Sin datos en tiempo real al usuario | N/A (propiedad de CFE) |

*Fuentes: cotizaciones de mercado en MercadoLibre y proveedores nacionales.

### Causas del problema

> *¿Cuáles son sus causas?*

Las causas son de naturaleza multifactorial y convergen en un ciclo de desinformación energética:

1. **Opacidad de la medición fiscal.** Los medidores de la CFE no ofrecen interfaces de datos instantáneos dentro de la vivienda. Toda información llega con un retraso de semanas o meses que invalida cualquier corrección de hábitos en tiempo real (CFE, 2024).

2. **Barrera económica de acceso.** El costo de las soluciones comerciales disponibles —agravado por aranceles de importación, costos logísticos y depreciación cambiaria— las sitúa fuera del alcance del usuario residencial promedio.

3. **Complejidad de instalación.** Numerosas soluciones requieren intervención intrusiva en el tablero eléctrico principal, lo que implica riesgos de seguridad y la necesidad de mano de obra especializada certificada conforme a la NOM-001-SEDE-2012.

4. **Invisibilidad inherente del recurso.** La electricidad es una magnitud intangible cuyo consumo no es perceptible por los sentidos humanos, dificultando la formación de una cultura de ahorro energético sin herramientas de visualización.

5. **Variabilidad del suministro eléctrico.** Las fluctuaciones de voltaje en la red pública mexicana —fenómeno frecuente en zonas suburbanas— distorsionan las estimaciones de consumo basadas en voltaje nominal constante (127 V) e introducen un error sistemático que las soluciones más simples no contemplan.

### Efectos del problema

> *¿Qué efecto genera?*

Los efectos son cuantificables y afectan múltiples dimensiones:

- **Económico.** Sobrecostos en la facturación eléctrica y riesgo permanente de caer en tarifa DAC, con impacto financiero directo sobre el presupuesto familiar.

- **Desperdicio energético.** Los consumos fantasma en modo *standby* —entre un 5% y un 10% del consumo total del hogar según la Agencia Internacional de Energía (IEA, 2014)— permanecen invisibles e incorregidos durante años.

- **Ambiental.** El desperdicio acumulado a escala de millones de hogares incrementa la demanda agregada sobre la red eléctrica nacional, aumentando la generación y las emisiones de CO₂.

- **Integridad de equipos.** Las variaciones de voltaje no diagnosticadas deterioran prematuramente motores de electrodomésticos y circuitos electrónicos sensibles, generando costos adicionales de reparación o reemplazo.

### Condiciones en que se presenta

> *¿En qué condiciones se presenta?*

El fenómeno está acotado a las siguientes condiciones:

- **Tipo de servicio:** monofásico (1 Fase + Neutro, 127 V, 60 Hz)
- **Ubicación geográfica:** zonas urbanas y suburbanas de México
- **Entorno de validación:** vivienda unifamiliar en la zona metropolitana de Toluca, Estado de México
- **Esquema tarifario:** tarifas escalonadas de la CFE (1, 1A-1F, DAC)
- **Tipo de medidor:** electromecánico o digital estándar sin interfaz de datos al usuario

La condición se agrava en hogares cuyo consumo mensual se aproxima al límite subsidiado, puesto que la falta de visibilidad impide al usuario realizar los ajustes necesarios para evitar el salto tarifario.

### Probabilidad de solución

> *¿Cuál es la probabilidad de solucionarlo?*

La evidencia técnica reunida indica que la probabilidad de solución es **alta**. La evolución del IoT y la disponibilidad de microcontroladores de bajo costo con WiFi integrado —como el ESP32 de Espressif Systems (2022)— han abierto una ventana de oportunidad real.

**Resultados preliminares del prototipo SME-IoT:**

| Indicador | Resultado |
|---|---|
| Coeficiente de determinación (R²) | > 0.98 |
| Error MAPE (cargas > 200 W) | ±2.3% |
| Error MAPE (cargas 50–200 W) | ±4.1% |
| Costo total de materiales | \$600.00 MXN |
| Reducción de costo vs. comerciales | > 60% |

Estos resultados validan tanto la viabilidad técnica como la viabilidad económica de la propuesta.

**Limitaciones identificadas y mitigadas:**

| Limitación | Estrategia de mitigación |
|---|---|
| Zona muerta del ADC (< 0.2 A) | Declaración formal de rango mínimo; polinomio de corrección |
| Conflicto ADC2/WiFi en el ESP32 | Uso exclusivo de pines del bloque ADC1 (GPIO 32-39) |
| Atenuación WiFi por tablero metálico | Instalación en caja plástica externa adyacente al tablero |
| Pérdida de conectividad WiFi | Almacenamiento local en microSD como respaldo automático |

*Fuente: Espressif Systems (2022), ESP32 Series Datasheet*

### Relación con investigaciones similares

> *¿Cómo se relaciona con otros similares?*

El problema se vincula con una línea de investigación consolidada a nivel internacional:

- **Ramadan et al. (2024)** propusieron un sistema de gestión energética residencial basado en la integración de técnicas NILM con infraestructura IoT, demostrando la viabilidad de la desagregación de cargas individuales a partir de una sola medición agregada. Su enfoque valida la convergencia entre monitoreo no intrusivo y comunicación en red; no obstante, emplea hardware de gama industrial y no aborda la restricción de costo que caracteriza al mercado mexicano.

- **OpenEnergyMonitor** (Lea y Hudson, 2012–presente) constituye el antecedente más significativo en hardware libre para monitoreo de energía. Su plataforma emonTx implementó medición no intrusiva con sensores SCT-013 y la biblioteca *EmonLib*. No obstante, su dependencia de componentes importados y la ausencia de WiFi nativo en el ATmega328P limitan su accesibilidad en México.

- **Kaselimi et al. (2022)** presentaron una revisión exhaustiva de los métodos y desafíos del monitoreo no intrusivo de carga (NILM), trazando la evolución desde las firmas de potencia hasta las arquitecturas modernas basadas en aprendizaje profundo e IoT, e identificando las brechas pendientes en confiabilidad y despliegue residencial.

- **Soluciones comerciales** (Emporia Vue, Shelly EM) demuestran la factibilidad técnica del monitoreo residencial con sensores tipo *clamp* y conectividad WiFi, pero su modelo de negocio propietario y precios de importación las posicionan fuera del alcance del mercado objetivo de esta investigación.

**El nicho del prototipo SME-IoT** se diferencia al integrar en una sola unidad:

1. Arquitectura de hardware abierta (ESP32)
2. Costo reducido (~\$600 MXN, componentes nacionales)
3. Medición de potencia activa real (voltaje + corriente simultáneos)
4. Conectividad WiFi nativa
5. Almacenamiento local para operación híbrida

Todo ello diseñado específicamente para las condiciones técnicas y socioeconómicas del mercado residencial mexicano.

---

## Referencias

Comisión Federal de Electricidad. (2024). *Tarifas domésticas de energía eléctrica*. CFE. https://app.cfe.mx/Aplicaciones/CCFE/Tarifas/TarifasCRECasa/Casa.aspx

Espressif Systems. (2022). *ESP32 Series Datasheet* (ver. 3.4). https://www.espressif.com/documentation/esp32_datasheet_en.pdf

Hart, D. W. (2011). *Power Electronics*. McGraw-Hill Education.

Hernández Sampieri, R., Fernández Collado, C., y Baptista Lucio, M. del P. (2014). *Metodología de la investigación* (6.ª ed.). McGraw-Hill Education.

International Energy Agency. (2014). *More Data, Less Energy: Making Network Standby More Efficient in Billions of Connected Devices*. IEA. https://www.iea.org/reports/more-data-less-energy

Kaselimi, M., Protopapadakis, E., Voulodimos, A., Doulamis, N. y Doulamis, A. (2022). Towards Trustworthy Energy Disaggregation: A Review of Challenges, Methods, and Perspectives for Non-Intrusive Load Monitoring. *Sensors*, *22*(15), 5872. https://doi.org/10.3390/s22155872

Naciones Unidas. (2015). *Transformar nuestro mundo: La Agenda 2030 para el Desarrollo Sostenible*. Asamblea General de las Naciones Unidas. https://sdgs.un.org/2030agenda

Norma Oficial Mexicana NOM-001-SEDE-2012. (2012). *Instalaciones Eléctricas (Utilización)*. Diario Oficial de la Federación, México.

OpenEnergyMonitor. (2012–presente). *EmonTx — Open-source energy monitoring*. https://openenergymonitor.org

Oppenheim, A. V., y Willsky, A. S. (2014). *Signals and Systems* (2nd ed.). Pearson Education.

Ramadan, R., Huang, Q., Zalhaf, A. S., Bamisile, O., Li, J., Mansour, D.-E. A., Lin, X. y Yehia, D. M. (2024). Energy Management in Residential Microgrid Based on Non-Intrusive Load Monitoring and Internet of Things. *Smart Cities*, *7*(4), 1907–1935. https://doi.org/10.3390/smartcities7040075
