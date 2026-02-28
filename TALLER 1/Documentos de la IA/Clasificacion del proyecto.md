<!--
===================================================================
METADATOS DEL DOCUMENTO
===================================================================
Proyecto    : Diseño e Implementación de un Sistema IoT de Bajo
              Costo para la Monitorización No Intrusiva de Consumo
              Eléctrico Residencial mediante Arquitectura ESP32
Área        : Ingeniería Electrónica / Investigación Académica
-------------------------------------------------------------------
Archivo     : TALLER 1/Documentos de la IA/Clasificacion del
              proyecto.md
Tipo        : Clasificación metodológica de la investigación
Descripción : Define la tipología formal del proyecto según
              estándares académicos: investigación aplicada y
              tecnológica, enfoque cuantitativo, alcance
              correlacional-experimental, diseño mixto
              (laboratorio + campo). Incluye justificación
              de cada clasificación con ejemplos concretos
              del prototipo ESP32.
Autor       : Generado por IA
Creado      : 2026-02-25
Últ. mod.   : 2026-02-28 (reorganización a carpeta Documentos
              de la IA)
Etapa       : Taller de Investigación 1 – Diseño metodológico
Estado      : INTEGRADO – La clasificación fue adoptada en el
              Marco Metodológico de "Proyecto completo.md"
              (sección 6)
Notas       : La redacción del párrafo-resumen final de este
              archivo fue usada casi textualmente en el
              documento compilado. La terminología aquí
              establecida es la definitiva.
===================================================================
-->

Para la redacción formal de la metodología en tu tesis o reporte técnico, el proyecto debe ser clasificado bajo los estándares de investigación en ingeniería. Considerando que se trata del desarrollo de un dispositivo físico (hardware) con validación de desempeño, la clasificación pertinente y su justificación son las siguientes:

### Clasificación Metodológica del Proyecto

#### 1. Por su Finalidad: **Investigación Aplicada y Tecnológica**

* **Definición:** Este tipo de investigación busca la utilización de conocimientos teóricos preexistentes para la solución de problemas prácticos y la satisfacción de necesidades concretas.
* **Justificación en el contexto del proyecto:**
El proyecto no busca formular nuevas leyes fundamentales del electromagnetismo (investigación básica), sino aplicar teorías consolidadas —como la Ley de Faraday para el sensor SCT-013, la teoría de muestreo de Nyquist para el ADC del ESP32 y los protocolos TCP/IP— para resolver una problemática tangible: la falta de visibilidad del consumo energético en los hogares mexicanos. El resultado final es un producto tecnológico tangible (el prototipo) con una aplicación directa en el entorno residencial.

#### 2. Por el Enfoque de Datos: **Investigación Cuantitativa**

* **Definición:** Se basa en la recolección y el análisis de datos numéricos para probar hipótesis y rastrear patrones mediante técnicas estadísticas y matemáticas.
* **Justificación en el contexto del proyecto:**
La validación del sistema depende enteramente de variables medibles y cuantificables. No se analizan "percepciones" del usuario, sino magnitudes físicas objetivas:
* Corriente Eficaz ($I_{RMS}$ en Amperios).
* Potencia Aparente ($S$ en Volti-Amperios).
* Error Porcentual ($E_{\%}$) comparado con un patrón de referencia.
El éxito del proyecto se determina mediante análisis estadístico (cálculo de desviación estándar, error absoluto medio y correlación lineal $R^2$) de los datos obtenidos por el sensor.



#### 3. Por su Alcance: **Correlacional y Explicativa**

* **Definición:** Busca medir el grado de relación entre variables y determinar las causas de los fenómenos físicos observados.
* **Justificación en el contexto del proyecto:**
* **Nivel Correlacional:** El estudio evalúa la relación entre la lectura del prototipo propuesto (Variable A) y la lectura de un instrumento de medición certificado o "patrón" (Variable B). Se busca demostrar que existe una correlación lineal positiva fuerte (cercana a 1) entre ambas mediciones.
* **Nivel Explicativo:** El proyecto busca explicar cómo factores como el ruido en la fuente conmutada, la resolución del ADC del ESP32 o la carga del *burden resistor* afectan la precisión de la medida, estableciendo relaciones causa-efecto en el desempeño del dispositivo.



#### 4. Por el Lugar de Realización: **Mixta (De Laboratorio y De Campo)**

* **Definición:** Combina el control riguroso de variables en un entorno aislado con la validación en el entorno real donde operará el sistema.
* **Justificación en el contexto del proyecto:**
* **Fase de Laboratorio:** Se realizará la calibración inicial del sensor SCT-013 y el ajuste de la fuente conmutada en un entorno controlado, utilizando cargas conocidas (resistencias de potencia, lámparas incandescentes) para aislar variables como el ruido eléctrico externo.
* **Fase de Campo:** Se instalará el dispositivo en un tablero de distribución residencial real (en Toluca). Aquí, el sistema se someterá a variables no controladas como fluctuaciones de la red de CFE, armónicos generados por electrodomésticos modernos y variaciones de temperatura ambiente, validando su robustez en condiciones operativas reales.



#### 5. Por la Manipulación de Variables: **Experimental**

* **Definición:** El investigador manipula intencionalmente una o más variables independientes (causas) para analizar las consecuencias en una o más variables dependientes (efectos).
* **Justificación en el contexto del proyecto:**
Para validar el dispositivo, se diseñará un experimento donde se manipulará deliberadamente la **Carga Eléctrica** (Variable Independiente: encender/apagar dispositivos de diferentes potencias) para observar la respuesta del **Algoritmo de Medición** en el microcontrolador (Variable Dependiente). Se controlarán variables intervinientes como el voltaje de alimentación (mediante la fuente conmutada regulada) para asegurar la validez interna del experimento.

---

### Resumen para el Protocolo (Insertar en Documento)

> *"La presente investigación se define como de tipo **aplicada y tecnológica** con un enfoque **cuantitativo**. Posee un alcance **correlacional y experimental**, dado que se manipulan variables de carga eléctrica para validar la precisión del prototipo frente a un estándar de referencia. El diseño es **mixto**, iniciando con una fase de calibración en laboratorio controlado y culminando con pruebas de campo en una instalación residencial, permitiendo evaluar el desempeño del sistema IoT bajo condiciones estocásticas de consumo real."*