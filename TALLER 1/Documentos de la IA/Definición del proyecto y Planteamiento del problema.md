# Definición del Proyecto y Planteamiento del Problema

## 1. Definición del Proyecto

### Nombre del Proyecto
**Diseño e Implementación de un Sistema IoT de Bajo Costo para la Monitorización No Intrusiva de Consumo Eléctrico Residencial mediante Arquitectura ESP32.**

### Justificación (¿Por qué este proyecto?)
La gestión eficiente de la energía eléctrica en el sector residencial de México enfrenta una barrera crítica: la falta de información. Los usuarios desconocen su patrón de consumo en tiempo real, recibiendo retroalimentación únicamente a través del recibo bimestral de la CFE, el cual actúa como una "caja negra". Esto frecuentemente resulta en sorpresas económicas y la caída en la tarifa **DAC (Doméstica de Alto Consumo)**, donde se pierde el subsidio gubernamental y el costo por kWh se dispara.

Este proyecto se justifica por la necesidad de democratizar el acceso a la tecnología de medición inteligente (*Smart Metering*). Las soluciones comerciales existentes son costosas (superando frecuentemente los \$1,500 MXN) o complejas de instalar. Al desarrollar un dispositivo de **arquitectura abierta, bajo costo (aprox. \$550 MXN) y no intrusivo**, se empodera al usuario con datos para tomar decisiones, corregir hábitos de consumo y reducir su huella de carbono, alineándose con las tendencias globales de *Smart Grids* y eficiencia energética.

---

## 2. Planteamiento del Problema

### Afinar y estructurar la idea
El problema central radica en la desconexión entre el consumo físico de energía y la conciencia del usuario sobre dicho consumo. Sin herramientas de diagnóstico accesibles, es imposible para una familia identificar "vampiros energéticos" o electrodomésticos ineficientes antes de que llegue la factura.

Aunque la tecnología para monitorear esto existe (IoT, sensores de corriente), existe una brecha tecnológica y económica: las herramientas de gestión energética son percibidas como un lujo. El desafío técnico y de ingeniería es crear un dispositivo que sea seguro (sin cortar cables/no intrusivo), y que supere las limitaciones de los estimadores económicos actuales, integrando la **medición real de voltaje** para eliminar errores por fluctuaciones de la red y ofrecer un análisis de calidad de energía, todo ello manteniendo la viabilidad económica para la clase media.

### Formulación del Problema Específico
¿Es factible desarrollar e implementar un sistema de monitoreo eléctrico residencial IoT que, mediante la medición simultánea de voltaje y corriente, reduzca el costo de adquisición en un 60% respecto a analizadores de red comerciales, garantizando una precisión superior al 95% en el cálculo de potencia real y permitiendo la detección de anomalías en el suministro (picos y caídas de tensión)?

---

## 3. Análisis del Problema (Cuestionario Guía)

### ¿Cuál es el problema?
La carencia de dispositivos accesibles y de fácil instalación que permitan a los usuarios residenciales monitorear su consumo eléctrico en tiempo real, lo que impide la gestión eficiente de la energía y el control de gastos.

### ¿Cuáles son sus causas?
1.  **Tecnología de medición fiscal limitada:** Los medidores de CFE son acumulativos y no ofrecen interfaces de datos instantáneos al usuario dentro del hogar.
2.  **Barreras económicas:** Los monitores de energía comerciales (ej. Sense, Emporia) tienen precios elevados de importación.
3.  **Complejidad técnica:** Muchas soluciones requieren intervención física peligrosa en el cableado principal (instalación intrusiva).
4.  **Invisibilidad del recurso:** La electricidad es intangible, lo que dificulta crear una cultura de ahorro sin ayudas visuales.
5.  **Variabilidad del Suministro:** Las fluctuaciones de voltaje en la red pública (comunes en México) distorsionan las estimaciones de consumo simples y ponen en riesgo los electrodomésticos.

### ¿Qué efecto genera?
1.  **Sobrecostos:** Pagos elevados en la facturación eléctrica y riesgo de entrar en tarifa DAC.
2.  **Desperdicio energético:** Uso ineficiente de electrodomésticos y presencia de consumos fantasma (*standby*) no detectados.
3.  **Impacto ambiental:** Mayor demanda a la red eléctrica, lo que implica mayor generación y emisiones de CO2.
4.  **Deterioro de Equipos:** Daños prematuros en motores (refrigeradores, bombas) y electrónica sensible debido a variaciones de voltaje no detectadas.

### ¿En qué condiciones se presenta?
El problema es omnipresente en viviendas de clase media y baja en México que cuentan con suministro básico (127V), donde la infraestructura eléctrica es estándar y no existen sistemas de domótica instalados previamente. Se agrava en periodos de alto consumo estacional o cuando se añaden nuevas cargas al hogar sin control.

### ¿Cuál es la probabilidad de solucionarlo?
**Alta.**
*   **Técnicamente:** La tecnología seleccionada (ESP32 + SCT-013) es madura y probada. El método de medición de $I_{RMS}$ es un estándar en ingeniería.
*   **Económicamente:** El presupuesto preliminar de materiales ($550 MXN) valida la hipótesis de bajo costo.
*   **Operativamente:** Al usar sensores de núcleo partido (clamp), se elimina el riesgo de manipulación de cables de alta tensión, haciendo la solución viable para usuarios no expertos.

### ¿Cómo se relaciona con otros similares?
Este proyecto se vincula directamente con:
*   **Smart Grids (Redes Inteligentes):** Representa el componente del "lado del usuario" (HAN - Home Area Network).
*   **Domótica (Home Automation):** Se integra en el ecosistema de casas inteligentes, similar a enchufes inteligentes pero a nivel de acometida general.
*   **Sustentabilidad:** Es un prerrequisito para la adopción de energías renovables (paneles solares), ya que el primer paso es conocer y optimizar el consumo actual.

A diferencia de los medidores fiscales (que buscan exactitud legal para cobro), este proyecto se relaciona con la **instrumentación educativa y preventiva**.