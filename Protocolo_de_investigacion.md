# Protocolo de investigación

**Proyecto:** Diseño e Implementación de un Sistema IoT de Bajo Costo para la Monitorización No Intrusiva de Consumo Eléctrico Residencial mediante Arquitectura ESP32.  
**Periodo de ejecución:** 2 de febrero de 2026 al 29 de mayo de 2026.

---

## 1. Antecedentes del problema

En México, el consumo eléctrico residencial suele evaluarse a partir de lecturas acumuladas de facturación, sin retroalimentación operativa en tiempo real para el usuario final. Esta condición dificulta identificar cargas ineficientes, consumos en espera y patrones horarios de alto impacto económico.

La literatura técnica en monitoreo no intrusivo de cargas (NILM) ha demostrado que la medición simultánea de corriente y voltaje, junto con procesamiento digital de señales, permite estimar potencia activa con precisión útil para gestión doméstica. En paralelo, el crecimiento de plataformas de bajo costo como ESP32 habilita arquitecturas de instrumentación accesibles para uso residencial.

El problema, por tanto, no es la inexistencia de tecnología de medición, sino su baja accesibilidad económica y de instalación en el contexto doméstico nacional. El presente protocolo se enfoca en cerrar esa brecha mediante un sistema IoT no intrusivo, replicable y de costo contenido.

---

## 2. Planteamiento del problema

Existe una desconexión entre el consumo eléctrico real de los hogares y la capacidad de decisión del usuario para corregirlo oportunamente. La ausencia de medición continua y comprensible durante el periodo de facturación produce:

- sobrecostos por hábitos no optimizados;
- baja detección de consumos anómalos o fantasma;
- mayor probabilidad de escalar a esquemas tarifarios de mayor costo;
- menor cultura de eficiencia energética en el hogar.

Aunque existen soluciones comerciales, una parte importante de ellas presenta barreras de adopción: costo elevado, requerimientos de instalación intrusiva y dependencia de ecosistemas cerrados. Se requiere, en consecuencia, una alternativa de bajo costo, segura y técnicamente validada para medición residencial informativa.

---

## 3. Objetivos de la investigación

### Objetivo general

Diseñar, implementar y validar un sistema IoT no intrusivo para monitorización de consumo eléctrico residencial, basado en ESP32, SCT-013-030 y ZMPT101B, capaz de estimar potencia activa con error menor al 5% respecto a un instrumento de referencia TRMS en condiciones de carga doméstica.

### Objetivos específicos

1. Definir requerimientos funcionales y metrológicos del sistema para entorno residencial monofásico.
2. Diseñar la arquitectura electrónica de adquisición y acondicionamiento de señales de corriente y voltaje.
3. Desarrollar firmware de muestreo, cálculo eléctrico y transmisión de datos.
4. Implementar visualización y persistencia local de información (interfaz local y registro de datos).
5. Ejecutar calibración y validación comparativa con instrumento patrón.
6. Evaluar viabilidad económica del prototipo frente a alternativas comerciales.

---

## 4. Justificación e impacto

### Impacto social

Aporta una herramienta de diagnóstico energético accesible para hogares que no cuentan con sistemas de medición avanzada.

### Impacto tecnológico

Demuestra la integración de sensores no intrusivos, procesamiento de señales y conectividad IoT en una plataforma abierta y de bajo costo.

### Impacto ético

El sistema tiene propósito informativo y educativo; no reemplaza instrumentos de facturación oficial ni altera infraestructura de medición fiscal.

### Impacto económico

Reduce la barrera de entrada para monitoreo energético doméstico, con potencial de ahorro por decisiones de consumo informadas.

### Impacto ambiental

Favorece prácticas de uso eficiente de energía en vivienda, con efecto indirecto en reducción de demanda y emisiones asociadas.

### Viabilidad

- **Técnica:** componentes disponibles y arquitectura factible de implementación.
- **Operativa:** metodología dividida en fases de laboratorio y campo.
- **Económica:** costo de materiales dentro de umbral de bajo presupuesto.

---

## 5. Marco teórico (referentes)

El marco teórico se organiza en cuatro ejes:

1. **Fundamentos eléctricos:** valor eficaz (RMS), potencia activa, factor de potencia y relación entre magnitudes instantáneas.
2. **Instrumentación y sensado:** principio de operación de transformadores de corriente no intrusivos y sensores de voltaje AC.
3. **Procesamiento digital de señales:** muestreo, cuantización, filtrado y cálculo discreto de métricas eléctricas.
4. **Arquitectura IoT embebida:** capacidades y limitaciones de ESP32 para adquisición analógica, cómputo local y transmisión inalámbrica.

Este enfoque permite sustentar tanto el diseño del prototipo como los criterios de validación estadística y metrológica.

---

## 6. Hipótesis o supuestos

### Hipótesis general

El sistema IoT propuesto puede cumplir simultáneamente con un costo de implementación de bajo presupuesto y un error de potencia activa inferior al 5% frente a instrumento TRMS, para cargas residenciales dentro del rango operativo definido.

### Hipótesis nula

El prototipo no cumple de manera simultánea los criterios de costo objetivo y precisión metrológica establecidos.

### Hipótesis específicas

1. La relación entre corriente real y lectura acondicionada del SCT-013-030 mantiene linealidad adecuada en el rango de trabajo.
2. La adquisición simultánea de voltaje y corriente mejora la estimación de potencia activa frente a aproximaciones con voltaje nominal constante.
3. La fuente de alimentación y el diseño de acondicionamiento no introducen ruido que comprometa la precisión objetivo.
4. El costo total de materiales mantiene ventaja económica frente a opciones comerciales comparables.

---

## 7. Bosquejo del método

### 7.1 Universo y muestra

- **Universo:** condiciones de consumo residencial monofásico en el rango operativo del sistema.
- **Muestra:** niveles de carga representativos (resistivos e inductivos) con repeticiones por nivel y comparación directa entre prototipo e instrumento patrón.

### 7.2 Tipo de estudio

- Investigación aplicada y tecnológica.
- Enfoque cuantitativo.
- Alcance correlacional y explicativo.
- Diseño experimental mixto (laboratorio + campo).

### 7.3 Diseño y prueba del instrumento

- Instrumento principal: prototipo de medición IoT.
- Instrumento de referencia: multímetro TRMS calibrado.
- Piloto inicial para verificar estabilidad, saturación ADC, coherencia de registro e integridad de datos.

### 7.4 Recolección de información

- **Fase laboratorio:** calibración, ajuste de parámetros y pruebas controladas por niveles de carga.
- **Fase campo:** monitoreo en vivienda, adquisición temporal continua y contraste con medición de referencia.

### 7.5 Procesamiento y análisis

- Validación de integridad y depuración de datos.
- Cálculo de error porcentual y MAPE.
- Correlación y regresión lineal entre prototipo y patrón.
- Evaluación de concordancia mediante análisis gráfico especializado.

### 7.6 Presentación de resultados

- Dispersión Prototipo vs Patrón con línea de ajuste.
- Curvas de error por nivel de carga.
- Gráficas de concordancia.
- Series temporales de potencia y energía acumulada.

---

## 8. Cronograma

| Fase | Actividad | Inicio | Fin | Entregable |
|---|---|---:|---:|---|
| F1 | Integración documental del protocolo y planeación técnica | 2026-02-02 | 2026-02-13 | Protocolo base validado |
| F2 | Diseño detallado de hardware y firmware | 2026-02-16 | 2026-03-06 | Diseño técnico cerrado |
| F3 | Adquisición de insumos y armado de prototipo | 2026-03-09 | 2026-03-20 | Prototipo funcional v1 |
| F4 | Calibración y prueba piloto | 2026-03-23 | 2026-04-03 | Parámetros de calibración |
| F5 | Pruebas formales de laboratorio | 2026-04-06 | 2026-04-24 | Base de datos experimental |
| F6 | Trabajo de campo y registro continuo | 2026-04-27 | 2026-05-08 | Datos de operación real |
| F7 | Procesamiento, análisis y visualización | 2026-05-11 | 2026-05-22 | Resultados y gráficas |
| F8 | Redacción final y cierre | 2026-05-25 | 2026-05-29 | Entrega final de protocolo y anexos |

---

## 9. Presupuesto y financiamiento

> Estimación en MXN con precios de referencia verificados en línea en abril de 2026.

### 9.1 Consumibles y componentes del prototipo (1 unidad)

| Concepto | Cantidad | Costo unitario (MXN) | Subtotal (MXN) | Fuente |
|---|---:|---:|---:|---|
| ESP32 DevKit V1 | 1 | 130.00 | 130.00 | Pigra |
| Sensor SCT-013-030 | 1 | 130.00 | 130.00 | SANDOROBOTICS |
| Sensor ZMPT101B | 1 | 48.50 | 48.50 | Geek Factory |
| Fuente AC-DC HLK-PM01 (5V) | 1 | 89.00 | 89.00 | Tecneu |
| Módulo microSD (interfaz) | 1 | 18.90 | 18.90 | ElectroCrea |
| Consumibles menores (cables, conectores, soldadura, termorretráctil, tornillería) | 1 lote | 120.00 | 120.00 | Estimación técnica |
| **Total consumibles/componentes** |  |  | **536.40** |  |

### 9.2 Herramienta/equipo de apoyo de validación

| Concepto | Criterio de costeo | Monto (MXN) |
|---|---|---:|
| Multímetro TRMS calibrado (amortización) | Prorrateo por uso académico durante el periodo del proyecto | 450.00 |
| Herramienta de taller y EPP (amortización) | Prorrateo por uso en 4 meses de ejecución | 300.00 |
| **Subtotal herramienta/equipo** |  | **750.00** |

### 9.3 Mano de obra de referencia

Para estimación de costo estándar se considera dedicación parcial en 4 meses, con base en salarios promedio reportados por Data México:

- Ingeniería electrónica: **$8,840 MXN/mes** (referencia 2025-T1).
- Electricistas y linieros: **$7,160 MXN/mes** (referencia 2025-T1).

Cálculo:

- Ingeniería electrónica (50% dedicación): 8,840 × 4 × 0.50 = **17,680.00 MXN**.
- Técnico electricista (20% dedicación): 7,160 × 4 × 0.20 = **5,728.00 MXN**.

**Subtotal mano de obra:** **23,408.00 MXN**.

### 9.4 Resumen financiero

| Rubro | Total (MXN) |
|---|---:|
| Consumibles/componentes | 536.40 |
| Herramienta/equipo (amortización) | 750.00 |
| Mano de obra (referencial) | 23,408.00 |
| **Total general estimado** | **24,694.40** |

### 9.5 Esquema de financiamiento propuesto

- Aportación directa del investigador para componentes y consumibles.
- Uso de infraestructura institucional para pruebas.
- Mano de obra considerada como valorización de proyecto académico-tecnológico.

---

## 10. Fuentes consultadas

### 10.1 Referencias documentales del proyecto

- Documento de investigación integral del proyecto (versión compilada vigente).
- Documento de hipótesis y bosquejo metodológico (complemento técnico).

### 10.2 Referencias externas (actualización técnica y económica)

1. Comisión Federal de Electricidad. (2026). *Tarifas domésticas de energía eléctrica*. https://app.cfe.mx/Aplicaciones/CCFE/Tarifas/TarifasCRECasa/Casa.aspx
2. Data México, Secretaría de Economía. (2025). *Ingenieros Electrónicos: salarios y fuerza laboral*. https://www.economia.gob.mx/datamexico/es/profile/occupation/ingenieros-electronicos
3. Data México, Secretaría de Economía. (2025). *Electricistas y Linieros: salarios y fuerza laboral*. https://www.economia.gob.mx/datamexico/es/profile/occupation/electricistas-y-linieros
4. Espressif Systems. (2022). *ESP32 Series Datasheet*. https://www.espressif.com/documentation/esp32_datasheet_en.pdf
5. Pigra. (2026). *ESP32D DEVKIT V1*. https://pigra.com.mx/electronica/73-esp32d.html
6. SANDOROBOTICS. (2026). *Sensor de Corriente No Invasivo 30A, SCT013*. https://sandorobotics.com.mx/producto/hr0214-118a/
7. Geek Factory. (2026). *Módulo Sensor de Voltaje AC Monofásico ZMPT101B*. https://www.geekfactory.mx/producto/sensor-voltaje-ac-zmpt101b/
8. Tecneu. (2026). *Convertidor AC-DC Fuente 5V HLK-PM01*. https://www.tecneu.com/products/convertidor-ac-dc-fuente-5v-hlk-pm01
9. ElectroCrea. (2026). *Módulo Micro SD*. https://electrocrea.com/products/modulo-microsd
10. Kaselimi, M., Protopapadakis, E., Voulodimos, A., Doulamis, N., & Doulamis, A. (2022). Toward trustworthy energy disaggregation: A review of challenges, methods and perspectives for non-intrusive load monitoring. *Sensors, 22*(15), 5872. https://doi.org/10.3390/s22155872
11. Hart, G. W. (1992). Nonintrusive appliance load monitoring. *Proceedings of the IEEE, 80*(12), 1870–1891.
