# Protocolo de investigación

**Proyecto:** Diseño e Implementación de un Sistema IoT de Bajo Costo para la Monitorización No Intrusiva de Consumo Eléctrico Residencial mediante Arquitectura ESP32.  
**Documento base:** `Hipotesis_y_presentacion.md` y `Proyecto completo.md`.  
**Periodo del proyecto:** del **2 de febrero de 2026** al **29 de mayo de 2026**.

---

## Control de coherencia y orden

Este protocolo se estructuró en el **mismo orden solicitado (1–10)** y se alinea con:

- Planteamiento, objetivos, justificación, marco teórico y metodología del documento maestro.
- Hipótesis y bosquejo metodológico del documento complementario.

Además, se integraron **fuentes externas actuales** para:

1. Actualizar costos de insumos/componentes.
2. Sustentar mano de obra con referencia laboral estándar en México.

---

## 1. Antecedentes del problema

La gestión del consumo eléctrico residencial en México mantiene una brecha de información: el usuario final no recibe retroalimentación instantánea útil para corregir hábitos de consumo durante el periodo de facturación. El proyecto responde a esa brecha mediante un sistema IoT no intrusivo de bajo costo con ESP32, SCT-013-030 y ZMPT101B, orientado al cálculo de potencia activa real y monitoreo local/remoto.

**Base principal a consultar/redactar:**
- `Proyecto completo.md` → Introducción, contextualización, antecedentes y estado del arte.

---

## 2. Planteamiento del problema

Existe una desconexión entre consumo real y decisiones del usuario por falta de instrumentos asequibles que ofrezcan medición en tiempo real con precisión suficiente y sin intervención intrusiva del cableado principal. Esto impacta en sobrecostos, riesgo de escalamiento tarifario y menor cultura de eficiencia energética.

**Base principal a consultar/redactar:**
- `Proyecto completo.md` → sección de planteamiento del problema.

---

## 3. Objetivos de la investigación: general y específicos

### Objetivo general
Diseñar, implementar y validar un sistema de monitoreo eléctrico residencial IoT, no intrusivo y de bajo costo, basado en ESP32 + SCT-013 + ZMPT101B, con error de potencia activa menor al 5% respecto a instrumento de referencia.

### Objetivos específicos
1. Definir requerimientos técnicos bajo condiciones residenciales en México.
2. Diseñar hardware de adquisición y acondicionamiento de señal.
3. Implementar firmware de adquisición, cálculo eléctrico y transmisión.
4. Integrar visualización/registro (OLED/microSD).
5. Validar con protocolo laboratorio + campo contra instrumento patrón TRMS.
6. Evaluar viabilidad económica de BOM frente a alternativas comerciales.

**Base principal a consultar/redactar:**
- `Proyecto completo.md` → objetivos general y específicos.

---

## 4. Justificación: Impacto social, tecnológico, ético, económico y ambiental. Viabilidad de la investigación

### Impacto social
Facilita la toma de decisiones de ahorro energético en hogares con acceso limitado a soluciones comerciales.

### Impacto tecnológico
Valida integración de sensores no intrusivos y procesamiento digital de señales en plataforma de bajo costo.

### Impacto ético
Se plantea como sistema informativo de usuario, sin alterar ni sustituir medición fiscal oficial.

### Impacto económico
Disminuye barrera de entrada respecto a soluciones comerciales importadas.

### Impacto ambiental
Promueve reducción de consumo eléctrico evitable y, por tanto, potencial reducción indirecta de emisiones asociadas al uso residencial.

### Viabilidad
- **Técnica:** arquitectura y métricas de desempeño ya definidas.
- **Operativa:** fases claras de laboratorio y campo.
- **Económica:** presupuesto acotado y verificable.

**Base principal a consultar/redactar:**
- `Proyecto completo.md` → justificación y viabilidad.

---

## 5. Diseño del marco teórico (referentes teóricos)

Se propone integrar cuatro bloques:

1. **Fundamentos eléctricos y de medición:** ley de Faraday, RMS, potencia activa, factor de potencia.
2. **Procesamiento digital de señales:** muestreo, discretización ADC, cálculo de magnitudes eléctricas en tiempo discreto.
3. **IoT y arquitectura embebida:** capacidades/limitaciones del ESP32 (ADC, WiFi, doble núcleo).
4. **Marco contextual y normativo:** monitoreo residencial, rol de CFE, límites del instrumento informativo no fiscal.

**Base principal a consultar/redactar:**
- `Proyecto completo.md` → marco teórico (antecedentes, bases teóricas, estado del arte, marco conceptual y normativo).

---

## 6. Formulación de hipótesis o supuestos (si corresponde)

### Hipótesis general
El sistema IoT propuesto puede mantener costo objetivo de fabricación y precisión de medición de potencia activa en el umbral definido para cargas domésticas relevantes.

### Hipótesis nula
El prototipo no cumple simultáneamente con costo objetivo y precisión metrológica mínima.

### Hipótesis específicas (operacionales)
- Linealidad del SCT-013-030 en rango definido.
- Estabilidad de alimentación con rizado bajo.
- Mejora de cálculo de potencia activa con medición simultánea de voltaje y corriente.
- Viabilidad económica frente a referencia comercial.

**Base principal a consultar/redactar:**
- `Hipotesis_y_presentacion.md` → hipótesis general/nula/alternativa/específicas.
- `Proyecto completo.md` → hipótesis consolidadas.

---

## 7. Bosquejo del método

### 7.1 Determinación del universo y obtención de la muestra
- **Universo:** condiciones de carga residencial monofásica dentro del rango operativo del prototipo.
- **Muestra:** niveles de carga/corriente representativos (resistivas e inductivas), con repeticiones por nivel y comparación prototipo vs patrón.

### 7.2 Determinación del tipo de estudio (Tipo de investigación)
- Aplicada y tecnológica.
- Enfoque cuantitativo.
- Alcance correlacional-explicativo.
- Diseño mixto (laboratorio + campo).
- Carácter experimental.

### 7.3 Selección, diseño y prueba del instrumento de recolección de la información
- Instrumento principal: prototipo SME-IoT.
- Referencia: multímetro TRMS calibrado.
- Prueba piloto para validar estabilidad, saturación ADC, integridad de registro y consistencia metrológica.

### 7.4 Plan de recolección de la información para el trabajo de campo
- Fase laboratorio: calibración y ajuste de factores.
- Fase campo: instalación en vivienda, registro continuo temporal y comparación con referencia.

### 7.5 Plan de procesamiento y análisis de información
- Limpieza e integridad de datos.
- Cálculo de métricas: MAPE, error porcentual, correlación, regresión lineal y pruebas de concordancia.

### 7.6 Plan de presentación gráfica de los resultados
- Dispersión Prototipo vs Patrón + regresión.
- Curvas de error por nivel de carga.
- Bland–Altman para concordancia.
- Series temporales de potencia y energía acumulada.

**Base principal a consultar/redactar:**
- `Hipotesis_y_presentacion.md` → bosquejo metodológico detallado.
- `Proyecto completo.md` → marco metodológico y procedimiento experimental.

---

## 8. Cronograma

Cronograma alineado al periodo real del proyecto (**02-feb-2026 a 29-may-2026**).

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

## 9. Presupuesto y/o financiamiento (si corresponde)

> Estimación en MXN con precios consultados en línea (abril 2026).  
> Se separa en **consumibles**, **herramienta/equipo**, y **mano de obra estándar** para proyectos tecnológicos académicos similares.

### 9.1 Consumibles y componentes del prototipo (1 unidad)

| Concepto | Cantidad | Costo unitario (MXN) | Subtotal (MXN) | Fuente |
|---|---:|---:|---:|---|
| ESP32 DevKit V1 | 1 | 130.00 | 130.00 | Pigra |
| Sensor SCT-013-030 | 1 | 130.00 | 130.00 | SANDOROBOTICS |
| Sensor ZMPT101B | 1 | 48.50 | 48.50 | Geek Factory |
| Fuente AC-DC HLK-PM01 (5V) | 1 | 89.00 | 89.00 | Tecneu |
| Módulo microSD (interfaz) | 1 | 23.23 | 23.23 | ElectroCrea |
| Consumibles menores (cables, conectores, soldadura, termorretráctil, tornillería) | 1 lote | 120.00 | 120.00 | Estimación técnica de integración |
| **Total consumibles/componentes** |  |  | **540.73** |  |

### 9.2 Herramienta/equipo de apoyo de validación

| Concepto | Criterio de costeo | Monto (MXN) |
|---|---|---:|
| Multímetro TRMS calibrado (amortización para el proyecto) | Prorrateo de uso académico del instrumento en el periodo | 450.00 |
| Herramienta de taller (cautín, estación, pinzas, EPP, etc.) | Prorrateo por uso durante 4 meses | 300.00 |
| **Subtotal herramienta/equipo** |  | **750.00** |

### 9.3 Mano de obra (estándar de referencia)

Para evitar sobreestimación, se usa esquema de dedicación parcial con base en referencias salariales oficiales (Data México / Secretaría de Economía):

- **Ingeniero electrónico:** salario promedio mensual de referencia **$8,840 MXN**.
- **Electricista/liniero de apoyo:** salario promedio mensual de referencia **$7,160 MXN**.

Cálculo para 4 meses de proyecto:

- Ingeniero electrónico (50% dedicación): 8,840 × 4 × 0.50 = **17,680.00 MXN**
- Técnico electricista (20% dedicación): 7,160 × 4 × 0.20 = **5,728.00 MXN**

**Subtotal mano de obra:** **23,408.00 MXN**

### 9.4 Resumen financiero del protocolo

| Rubro | Total (MXN) |
|---|---:|
| Consumibles/componentes | 540.73 |
| Herramienta/equipo (amortización) | 750.00 |
| Mano de obra | 23,408.00 |
| **Total general estimado** | **24,698.73** |

### 9.5 Financiamiento

Se propone financiamiento mixto:
- Aportación del investigador para consumibles/componentes.
- Uso de infraestructura de laboratorio institucional (herramienta/equipo).
- Mano de obra valorizada como costo estándar de proyecto (no necesariamente flujo de caja directo).

---

## 10. Fuentes consultadas

### 10.1 Fuentes base internas (obligatorias)

1. `Proyecto completo.md` (documento maestro vigente).
2. `Hipotesis_y_presentacion.md` (hipótesis y método).

### 10.2 Fuentes externas para actualización de cifras y contexto

1. Pigra. *ESP32D DEVKIT V1* (precio de referencia en MXN). https://pigra.com.mx/electronica/73-esp32d.html
2. SANDOROBOTICS. *Sensor de Corriente No Invasivo 30A, SCT013*. https://sandorobotics.com.mx/producto/hr0214-118a/
3. Geek Factory. *Módulo Sensor de Voltaje AC Monofásico ZMPT101B*. https://www.geekfactory.mx/categoria-de-producto/modulos/mod-acondicionamiento/
4. Tecneu. *Convertidor AC-DC Fuente 5V HLK-PM01*. https://www.tecneu.com/products/convertidor-ac-dc-fuente-5v-hlk-pm01
5. ElectroCrea. *Módulo Micro SD*. https://electrocrea.com/products/modulo-microsd
6. Data México (Secretaría de Economía). *Ingenieros Electrónicos: salarios y fuerza laboral*. https://www.economia.gob.mx/datamexico/es/profile/occupation/ingenieros-electronicos
7. Data México (Secretaría de Economía). *Electricistas y Linieros: salarios y fuerza laboral*. https://www.economia.gob.mx/datamexico/es/profile/occupation/electricistas-y-linieros
8. CFE. *Tarifas domésticas (consulta oficial)*. https://app.cfe.mx/Aplicaciones/CCFE/Tarifas/TarifasCRECasa/Casa.aspx

---

## Nota de uso para redacción final

Si se requiere versión final “lista para entrega”, este archivo ya contiene:

- Orden completo 1–10 solicitado.
- Criterios de coherencia con documentos base.
- Cronograma fechado exactamente al periodo real del proyecto.
- Presupuesto con separación de consumibles, herramienta y mano de obra estándar.
- Fuentes trazables para actualización de cifras.
