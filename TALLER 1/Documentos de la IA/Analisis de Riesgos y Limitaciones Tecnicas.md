<!--
===================================================================
METADATOS DEL DOCUMENTO
===================================================================
Proyecto    : Diseño e Implementación de un Sistema IoT de Bajo
              Costo para la Monitorización No Intrusiva de Consumo
              Eléctrico Residencial mediante Arquitectura ESP32
Área        : Ingeniería Electrónica / Investigación Académica
-------------------------------------------------------------------
Archivo     : TALLER 1/Documentos de la IA/Analisis de Riesgos
              y Limitaciones Tecnicas.md
Tipo        : Análisis técnico – Riesgos y limitaciones de diseño
Descripción : Identificación detallada de restricciones técnicas
              del hardware: no-linealidad del ADC del ESP32,
              conflicto WiFi/ADC2, efecto jaula de Faraday en
              tableros metálicos, limitación a servicio
              monofásico (127 V), zona muerta en cargas <0.2 A,
              y estrategia de respaldo con microSD. Define las
              delimitaciones técnicas que acotaron el alcance
              del proyecto.
Autor       : Generado por IA
Creado      : 2026-02-25
Últ. mod.   : 2026-02-28 (reorganización a carpeta Documentos
              de la IA)
Etapa       : Taller de Investigación 1 – Análisis de viabilidad
Estado      : INTEGRADO – Contenido absorbido por la sección 8
              de "Proyecto completo.md"
Notas       : Las delimitaciones aquí definidas (monofásico,
              >0.2 A, WiFi 2.4 GHz, intervención menor para
              toma L/N) fueron adoptadas textualmente en el
              documento compilado. Consultar este archivo solo
              como referencia de detalle expandido.
===================================================================
-->

# Análisis de Riesgos y Limitaciones Técnicas

Este documento detalla los desafíos técnicos y las limitaciones físicas inherentes al diseño actual del monitor de energía. Considerar estos aspectos es crucial para definir correctamente el alcance del proyecto y evitar problemas durante la fase de implementación.

## 1. Limitaciones del Microcontrolador (ESP32)

### A. No Linealidad del ADC
*   **El Problema:** Los convertidores analógico-digitales (ADC) del ESP32 no son perfectamente lineales, especialmente en los extremos de la escala (cerca de 0V y cerca de 3.3V). Además, son propensos a tener más ruido eléctrico que un Arduino Uno (AVR).
*   **Impacto:** Las lecturas de corrientes muy bajas (ej. un cargador de celular o el modo *standby* de una TV) podrían ser imprecisas o leerse como cero.
*   **Solución en Alcance:** Se debe declarar que el dispositivo tiene una "Zona Muerta" o corriente mínima de arranque (ej. < 0.2 Amperios no se garantiza precisión).

### B. Conflicto WiFi vs. ADC2
*   **El Problema:** El ESP32 tiene dos bloques de ADC (ADC1 y ADC2). Sin embargo, **el ADC2 no se puede utilizar cuando el módulo WiFi está activo**.
*   **Impacto:** Si conectas los sensores a pines del ADC2 (GPIOs 0, 2, 4, 12-15, 25-27), el dispositivo dejará de medir cuando intente enviar datos a internet.
*   **Requerimiento:** Es obligatorio diseñar el circuito usando **exclusivamente pines del ADC1** (GPIOs 32-39).

## 2. Limitaciones de Instalación Física

### A. La "Jaula de Faraday"
*   **El Problema:** La mayoría de los centros de carga (tableros) en México son cajas metálicas empotradas en la pared. El metal bloquea las señales de radiofrecuencia.
*   **Impacto:** El ESP32 podría no tener señal WiFi si se instala dentro del tablero con la tapa cerrada.
*   **Consideración de Diseño:** El alcance del proyecto debe contemplar el uso de una antena externa o aclarar que el dispositivo debe instalarse en una caja plástica externa adyacente al tablero (tipo registro), no dentro del metal.

### B. La Contradicción de "No Intrusivo"
*   **El Problema:** El sensor de corriente (SCT-013) debe colocarse en el centro de carga, pero el dispositivo necesita alimentación y referencia de voltaje.
*   **Solución de Diseño:** Se implementará un cable con clavija estándar (NEMA 5-15P) para conectar el dispositivo a cualquier tomacorriente convencional cercano al tablero.
*   **Redefinición del Alcance:** El sistema mantiene su estatus de **"No Intrusivo"** en cuanto a la instalación eléctrica fija (no requiere cortar cables ni desarmar el tablero principal para alimentarse), aunque requiere la disponibilidad de un enchufe doméstico cerca del punto de medición.

## 3. Limitaciones del Sistema Eléctrico Mexicano

### A. Instalaciones Bifásicas (220V)
*   **El Problema:** Muchas casas medianas/grandes en México tienen acometida bifásica (dos fases de 110V + Neutro) para soportar aires acondicionados o secadoras.
*   **Limitación:** Tu diseño actual tiene **un solo sensor de corriente y un solo sensor de voltaje**.
*   **Alcance:** El proyecto debe limitarse explícitamente a **"Viviendas con servicio Monofásico (1 Fase + Neutro)"**. Si se instala en una casa bifásica, solo medirá la mitad del consumo real.

### B. Ruido en la Línea
*   **El Problema:** La red eléctrica presenta fluctuaciones y deformaciones de onda. El sensor ZMPT101B tiene un ancho de banda limitado.
*   **Alcance de Medición:** El dispositivo podrá detectar **variaciones de amplitud** (subidas y bajadas de voltaje) y distorsión armónica básica, pero **no está diseñado para medir ruido de alta frecuencia (EMI)** ni transitorios de microsegundos, debido a las limitaciones de frecuencia de muestreo del ESP32.

## 4. Limitaciones de Seguridad de Datos

### A. Dependencia de la Red
*   **El Problema:** ¿Qué pasa si se va el internet?
*   **Solución:** Se incorpora un módulo de tarjeta **microSD** para almacenamiento local (*Data Logging*).
*   **Capacidad:** Una tarjeta de 4GB es suficiente para almacenar más de 5 años de registros con intervalos de 1 minuto (aprox. 50MB por año), cubriendo sobradamente el ciclo de facturación bimestral de CFE.
*   **Alcance:** El sistema opera de forma híbrida: transmisión en tiempo real si hay WiFi, y respaldo histórico local en SD garantizado.

---

## Resumen de Ajustes al Planteamiento del Problema

Para que el proyecto sea académicamente sólido, se deben agregar estas acotaciones a la sección de "Delimitaciones":

1.  **Tipo de Servicio:** Exclusivo para servicio monofásico residencial (127V).
2.  **Rango de Operación:** Precisión garantizada solo para corrientes > 0.2A (aprox 25W).
3.  **Conectividad:** Requiere señal WiFi de 2.4GHz estable en el punto de instalación.
4.  **Instalación:** Requiere intervención física menor para toma de voltaje (L y N).