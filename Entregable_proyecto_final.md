# Diseño e Implementación de un Sistema IoT de Bajo Costo para la Monitorización No Intrusiva de Consumo Eléctrico Residencial mediante Arquitectura ESP32

## 1. Antecedentes del problema

La gestión de la demanda energética es fundamental en la transición hacia redes eléctricas inteligentes (*Smart Grids*). A nivel global, los Objetivos de Desarrollo Sostenible (ODS 7 y 12) subrayan la necesidad de mejorar la eficiencia energética residencial. En México, el esquema tarifario de la Comisión Federal de Electricidad (CFE) estructura el costo en categorías escalonadas (tarifas 1 a 1F), penalizando el alto consumo mediante la tarifa DAC (Doméstica de Alto Consumo), la cual elimina el subsidio gubernamental. Sin embargo, los medidores convencionales electromecánicos o digitales estándar funcionan como dispositivos de registro acumulativo sin capacidad de retroalimentación instantánea, limitando la capacidad del usuario para corregir hábitos de consumo en tiempo real.

Históricamente, el monitoreo no intrusivo de carga (NILM) ha evolucionado desde métodos analógicos hasta arquitecturas basadas en Internet de las Cosas (IoT). Plataformas de hardware abierto como OpenEnergyMonitor han demostrado la viabilidad de usar sensores de corriente de núcleo partido y la biblioteca `EmonLib`, pero sus costos de adquisición e importación (>$2,000 MXN) siguen siendo elevados para el mercado nacional.

## 2. Planteamiento del problema

El problema central radica en la desconexión entre el consumo físico de energía y la conciencia del usuario. La falta de herramientas de diagnóstico accesibles impide la detección de consumos fantasma o ineficiencias en electrodomésticos. Las causas son multifactoriales: opacidad de la medición fiscal, barreras económicas (costo de equipos comerciales como Sense o Shelly EM >$1,500 MXN), complejidad de instalación y la invisibilidad inherente del recurso eléctrico. Además, las fluctuaciones de voltaje en la red mexicana distorsionan las estimaciones basadas exclusivamente en medición de corriente.

Pregunta de investigación: ¿Es factible desarrollar e implementar un sistema de monitoreo eléctrico residencial IoT que, mediante la medición simultánea de voltaje y corriente con sensores no intrusivos y un microcontrolador ESP32, reduzca el costo de adquisición en un 60% respecto a analizadores de red comerciales, garantizando una precisión superior al 95% en el cálculo de potencia activa real y permitiendo la detección de anomalías en el suministro?

## 3. Objetivo general

Diseñar, implementar y validar un sistema de monitoreo de consumo eléctrico residencial de bajo costo y no intrusivo, basado en el microcontrolador ESP32 y sensores de corriente tipo *clamp* (SCT-013) y de voltaje (ZMPT101B), capaz de calcular la potencia activa en tiempo real con un error inferior al 5% respecto a instrumentación de referencia, y de transmitir los datos de manera inalámbrica mediante conectividad WiFi.

## 4. Objetivos específicos

4.1 Analizar los requerimientos funcionales y no funcionales del sistema bajo las condiciones de la infraestructura eléctrica mexicana y las restricciones técnicas de los componentes.
4.2 Diseñar la etapa de hardware del sistema, incluyendo el circuito de acondicionamiento de señal para los sensores SCT-013, ZMPT101B, y el sistema de alimentación conmutada AC-DC integrado.
4.3 Desarrollar el firmware de adquisición de datos y procesamiento digital de señales —cálculo de corriente eficaz ($I_{RMS}$), voltaje eficaz ($V_{RMS}$) y potencia activa ($P$)— sobre la arquitectura de doble núcleo del ESP32.
4.4 Implementar la interfaz de usuario local (pantalla OLED SSD1306) y el módulo de almacenamiento local (tarjeta microSD) para la visualización y registro histórico.
4.5 Validar el desempeño del prototipo mediante pruebas comparativas contra instrumentación patrón (multímetro TRMS calibrado) en laboratorio y campo.
4.6 Evaluar la viabilidad económica del dispositivo mediante el análisis de la lista de materiales (BOM) y la comparación de costos frente al mercado.

## 5. Justificación

La investigación es conveniente porque proporciona una herramienta de diagnóstico instantáneo frente a la opacidad de la medición fiscal bimestral de CFE. Tiene relevancia social al democratizar el acceso a tecnología de eficiencia energética para familias mexicanas, reduciendo el costo de inversión a ~$600 MXN. Desde una implicación práctica, permite identificar patrones de uso ineficiente sin riesgos de instalación intrusiva. Aporta valor teórico al validar la aplicabilidad de la Ley de Faraday y el teorema de Nyquist-Shannon en una plataforma de hardware con restricciones severas de costo y resolución (ADC de 12 bits).

## 6. Marco Teórico

6.1 Electromagnetismo: El sensor SCT-013 opera bajo la Ley de Faraday de la Inducción Electromagnética ($\varepsilon = -d\Phi_B/dt$), donde el núcleo ferromagnético concentra el flujo del conductor primario para inducir una corriente proporcional en el secundario.
6.2 Procesamiento Digital: Se aplica el teorema de Nyquist-Shannon ($f_s \geq 2 f_{max}$) para garantizar que el muestreo (~1 kHz) sea suficiente para capturar la señal de 60 Hz. Los valores eficaces se calculan mediante sumatorias finitas en el dominio digital.
6.3 Potencia Eléctrica: La potencia activa (P) resulta del promedio del producto punto a punto de las muestras instantáneas: $P = \frac{1}{N} \sum v[n] \cdot i[n]$. Este método incorpora implícitamente el factor de potencia ($\cos\phi$).
6.4 Arquitectura ESP32: El SoC Xtensa® LX6 de doble núcleo permite la asignación dedicada: el Núcleo 1 para adquisición de alta prioridad y el Núcleo 0 para comunicación WiFi y protocolos IoT (MQTT/HTTP).
6.5 Fuentes Conmutadas (SMPS): Se emplea un módulo convertidor *buck* de alta frecuencia (Hi-Link) que ofrece eficiencia >70% y aislamiento galvánico en un volumen reducido.

## 7. Hipótesis

7.1 Hipótesis de investigación ($H_i$): Es factible desarrollar un sistema de monitoreo eléctrico residencial basado en IoT que, mediante el uso de hardware de código abierto y componentes genéricos optimizados (ESP32, SCT-013, ZMPT101B), reduzca los costos de manufactura por debajo de los $600.00 MXN por unidad, manteniendo un error de medición de potencia activa inferior al 5% en cargas domésticas estándar superiores a 25 W.
7.2 Hipótesis nula ($H_0$): El sistema propuesto no alcanza la precisión requerida (error porcentual $> 5\%$) o su costo de manufactura excede los $600.00 MXN por unidad, invalidando la viabilidad técnico-económica de la propuesta.
7.3 Hipótesis alternativa ($H_1$): El sistema propuesto logra un costo de manufactura ≤ $600.00 MXN por unidad y alcanza un error porcentual de potencia activa ≤ 5% en cargas domésticas superiores a 25 W.
7.4 Hipótesis específicas:
- El sensor SCT-013 acondicionado con un offset a 1.65 V mantiene una relación lineal con la corriente real con $R^2 > 0.98$ en el rango de 0.5 A a 30 A.
- La fuente integrada tipo Hi-Link presenta un rizado menor a 50 mVpp sin introducir ruido significativo en las mediciones del ADC del ESP32.
- La medición simultánea de voltaje y corriente instantánea permite calcular la potencia activa con mayor precisión que las estimaciones basadas en voltaje nominal constante de 127 V.
- La lista de materiales (BOM) no excede los $600.00 MXN, logrando una reducción de costo de al menos 60% respecto a soluciones comerciales comparables.

## 8. Diseño metodológico

8.1 Universo: El conjunto de todas las posibles condiciones de carga eléctrica en viviendas monofásicas residenciales dentro del rango de operación del sensor de corriente (0 a 30 A).
8.2 Tamaño de la muestra: Se establecieron 270 pares de observaciones distribuidas en 9 niveles de carga (0.5 A, 1 A, 2 A, 5 A, 10 A, 15 A, 20 A, 25 A y 30 A) con 30 repeticiones por nivel. El muestreo es no probabilístico intencional.
8.3 Tipos de investigación: Aplicada y tecnológica por su finalidad; cuantitativa por el enfoque de datos; correlacional-explicativa por su alcance; y experimental por la manipulación de la variable independiente (carga).
8.4 Tipo de instrumento a utilizar para la recolección de la información: El instrumento principal es el Prototipo SME-IoT (ESP32, SCT-013, ZMPT101B) validado contra un multímetro TRMS calibrado. La recolección emplea observación estructurada y registro automatizado en tarjeta microSD y monitor serial (CSV).
8.5 Encuesta: Se realizó una consulta técnica preliminar a 10 usuarios de tarifa doméstica para identificar el umbral de inversión aceptable, fijándolo en un rango de $500 a $700 MXN.

## 9. Cronograma

| Actividad | Mes 1 | Mes 2 | Mes 3 | Mes 4 |
| :--- | :---: | :---: | :---: | :---: |
| Revisión bibliográfica y normativa | X | | | |
| Diseño de hardware y acondicionamiento | X | X | | |
| Desarrollo de firmware y algoritmos PDS | | X | X | |
| Pruebas de laboratorio y calibración | | | X | |
| Pruebas de campo en Toluca | | | X | X |
| Redacción de reporte y conclusiones | | | | X |

## 10. Presupuesto y financiamiento

10.1 Presupuesto detallado (MXN):
- ESP32 DevKit V1: $130.00
- SCT-013-030 (Clamp): $185.00
- Módulo ZMPT101B: $50.00
- Fuente Hi-Link HLK-PM01: $75.00
- Pantalla OLED SSD1306: $65.00
- Componentes pasivos y gabinete: $95.00
Total: $600.00
10.2 Financiamiento: El proyecto es autofinanciado por el investigador para el desarrollo del prototipo académico inicial.

## 11. Análisis de Riesgos y Limitaciones Técnicas

11.1 Limitaciones del Microcontrolador: El ADC del ESP32 presenta no linealidad y el bloque ADC2 tiene conflicto con el WiFi. Se mitiga usando exclusivamente el bloque ADC1 y aplicando corrección por software.
11.2 Instalación Física: Los tableros metálicos actúan como jaulas de Faraday. Se requiere instalación en caja plástica externa. La zona muerta del ADC limita la precisión para corrientes <0.2 A.
11.3 Sistema Eléctrico: El diseño es para servicio monofásico exclusivo (127 V / 60 Hz). El sistema no está diseñado para medir ruido electromagnético de alta frecuencia o transitorios de microsegundos.

## 12. Resultados Preliminares y Discusión

12.1 Pruebas de Linealidad: Se obtuvo un coeficiente $R^2 > 0.98$ en el rango operativo medio, validando la proporcionalidad de los sensores.
12.2 Análisis de Error: El error porcentual absoluto medio (MAPE) es de $\pm 2.3\%$ para cargas >200 W. En cargas <50 W el error sube a $\pm 8.5\%$ debido al ruido de cuantización del ADC.
12.3 Viabilidad Económica: El costo de la BOM se confirmó en $600.00 MXN, logrando una reducción del 60-70% frente a soluciones comerciales.

## 13. Fuentes de información

Arias, F. G. (2012). *El proyecto de investigación: Introducción a la metodología científica* (6ª ed.). Editorial Episteme.
Bland, J. M., & Altman, D. G. (1986). Statistical methods for assessing agreement between two methods of clinical measurement. *The Lancet*, *1*(8476), 307–310.
Comisión Federal de Electricidad. (2024). *Tarifas domésticas de energía eléctrica*. CFE.
Creswell, J. W. (2018). *Research design: Qualitative, quantitative, and mixed methods approaches* (5th ed.). SAGE.
Espressif Systems. (2022). *ESP32 Series Datasheet* (ver. 3.4).
Hart, D. W. (2011). *Power electronics*. McGraw-Hill Education.
Hernández Sampieri, R. (2014). *Metodología de la investigación* (6ª ed.). McGraw-Hill Education.
Kaselimi, M., et al. (2022). Towards Trustworthy Energy Disaggregation. *Sensors*, *22*(15), 5872.
Naciones Unidas. (2015). *Agenda 2030 para el Desarrollo Sostenible*.
Norma Oficial Mexicana NOM-001-SEDE-2012. *Instalaciones Eléctricas (Utilización)*.
Shapiro, S. S., & Wilk, M. B. (1965). An analysis of variance test for normality (complete samples). *Biometrika*, *52*(3–4), 591–611.
Tamayo y Tamayo, M. (2009). *El proceso de la investigación científica* (5. ed.). Limusa.

## 14. Anexos

Anexo A: Diagrama esquemático del circuito de acondicionamiento de señal.
Anexo B: Código fuente del algoritmo de cálculo True RMS y Potencia Activa.
Anexo C: Reporte de calibración y curvas de error porcentual (MAPE).
Anexo D: Prueba piloto: Protocolo de verificación de integridad de datos.
Anexo E: Técnicas de procesamiento y análisis estadístico (Bland-Altman y Regresión).
