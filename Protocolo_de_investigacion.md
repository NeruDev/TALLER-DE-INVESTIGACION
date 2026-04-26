# Protocolo de investigación: Monitoreo IoT Residencial

**Investigador:** Jesus Uriel Uribe Diaz  
**Institución:** Instituto Tecnológico de Toluca  
**Proyecto:** Diseño e Implementación de un Sistema IoT de Bajo Costo para la Monitorización No Intrusiva de Consumo Eléctrico Residencial mediante Arquitectura ESP32.  
**Periodo de ejecución:** 2 de febrero de 2026 al 29 de mayo de 2026.  
**Ubicación del estudio:** Tenango del Valle, Estado de México.

---

## 1. Antecedentes del problema

Si vemos cómo está la situación de la luz en México, me doy cuenta de que la mayoría de las familias solo sabemos cuánto gastamos cuando llega el recibo cada dos meses. No hay una forma real de saber qué está pasando día a día. Esto es un problema porque, sin esos datos, es imposible saber qué aparato está fallando o si tenemos hábitos que nos están costando dinero de más.

Estuve revisando la literatura técnica sobre el monitoreo no intrusivo (NILM) y la verdad es que la teoría es clara: si mides corriente y voltaje al mismo tiempo, puedes sacar la potencia activa con mucha precisión. Por eso, decidí usar el ESP32. Me parece que es la mejor plataforma para armar un sistema que sea barato pero que de verdad sirva para una casa normal en nuestra zona, cerrando esa brecha entre lo que cuesta la tecnología y lo que la gente realmente puede pagar.

---

## 2. Planteamiento del problema

Hay una desconexión total entre lo que consumimos y lo que podemos decidir para ahorrar. En las pruebas que he hecho y lo que he observado en casas de **Tenango del Valle**, veo que no tener datos al momento causa muchos problemas: pagamos de más por no optimizar el uso de los aparatos, no nos damos cuenta de los consumos "fantasma" de equipos viejos y siempre está el miedo de que la CFE nos suba a la tarifa DAC sin avisar.

Las opciones que venden por ahí son carísimas, a veces pasan de los $1,500 pesos, y además te obligan a usar sus aplicaciones cerradas. Por eso me puse el reto de hacer una alternativa de bajo costo. Mi idea es que el hardware no pase de los **$600 MXN** y que sea lo suficientemente seguro para que cualquier persona lo tenga en su casa sin riesgos.

### Pregunta de investigación

¿Es posible para mí desarrollar un sistema IoT que use el ESP32, que sea preciso (error < 5%) y que cueste menos de $600 pesos, probándolo directamente en viviendas de Tenango del Valle?

---

## 3. Objetivos de la investigación

### Objetivo general

Desarrollar un sistema IoT de monitorización no intrusiva para la gestión del consumo eléctrico residencial, basado en la arquitectura ESP32 y sensado simultáneo de parámetros eléctricos, con el fin de validar su precisión y viabilidad económica en el municipio de Tenango del Valle.

### Objetivos específicos

1. Analizar qué es lo que realmente necesita un sistema de estos para aguantar las condiciones de la red eléctrica en las casas de México.
2. Diseñar el circuito y la etapa para acondicionar las señales de los sensores de corriente y voltaje para que el ESP32 las lea bien.
3. Escribir el código para que el microcontrolador haga los cálculos de potencia activa y se conecte al WiFi sin trabarse.
4. Meterle una pantalla OLED y un lector de tarjetas microSD para que el usuario vea sus datos y estos se guarden aunque se vaya el internet.
5. Hacer pruebas comparando mi prototipo contra un multímetro profesional (TRMS) para ver qué tanto error tengo realmente.
6. Revisar cuánto me gasté al final y comparar ese costo contra lo que cuestan los equipos comerciales para ver si de verdad es una opción viable.

---

## 4. Justificación e impacto

### Impacto tecnológico
Quiero demostrar que se pueden integrar sensores no intrusivos en una plataforma abierta como el ESP32. Además, me interesa validar cómo calibrar estos sensores cuando usas convertidores (ADC) que no tienen tanta resolución, algo que es muy común en proyectos de bajo presupuesto.

### Impacto económico
Básicamente, quiero bajar la barrera de entrada. Si logro que el aparato cueste un 60% menos que lo que hay en el mercado, mucha más gente va a poder monitorear su energía.

### Impacto ambiental
Si la gente ve cuánto gasta, va a empezar a apagar cosas. Eso ayuda a gastar menos luz y, al final, eso reduce la demanda eléctrica y las emisiones de CO2. Es un beneficio indirecto pero real.

---

## 5. Diseño del marco teórico

Para que esto funcione, me estoy apoyando en estos puntos:
1. **Electricidad:** Entender bien qué es el valor RMS y la potencia activa. Si no calculo esto bien desde la base, los datos no le van a servir al usuario.
2. **Instrumentación:** Voy a usar sensores de "núcleo partido" para la corriente. Me parecen lo mejor porque se instalan como un clip, sin tocar los cables vivos. Para el voltaje, usaré un transformador pequeño con aislamiento por seguridad.
3. **Procesamiento de señales:** Tengo que programar el muestreo y el filtrado digital. Si el código no está bien hecho, el ruido de la red me va a arruinar las lecturas.
4. **IoT:** Elegí el ESP32 porque tiene doble núcleo y WiFi. Es mucho más capaz que un Arduino y me permite procesar datos en un núcleo mientras el otro maneja la red.

---

## 6. Hipótesis

### Mi hipótesis
Pienso que si calibro bien el sistema y optimizo el código, voy a lograr que el error sea menor al 5% y que el costo total no pase de los $600 pesos.

### Supuestos técnicos
1. Creo que el sensor SCT-013 va a responder de forma lineal en el rango de consumo que tiene una casa normal.
2. Estoy convencido de que medir el voltaje real (en lugar de solo suponer que hay 127V) es la clave para que la potencia activa salga exacta.

---

## 7. Metodología (Cómo lo voy a hacer)

### 7.1 Localización y Muestra
Voy a hacer las pruebas en el municipio de **Tenango del Valle**. Elegí una casa unifamiliar de ahí porque tiene la instalación típica monofásica que me interesa estudiar. Me parece que es el entorno ideal para validar que el equipo funciona en el "mundo real".

### 7.2 Mi enfoque
- **Investigación Aplicada:** Voy a usar la electrónica para resolver un problema que veo diario.
- **Cuantitativo:** Todo se basa en números y comparaciones. Si mi prototipo dice 10A y el multímetro profesional dice 10.1A, entonces voy por buen camino.
- **Experimental:** Voy a construir el aparato y lo voy a probar con diferentes cargas para ver cómo se comporta.

### 7.3 Pasos del experimento
1. **Integración:** Primero voy a soldar todo y a programar el ESP32. Aquí es donde voy a ver si mi diseño de hardware realmente funciona.
2. **Calibración:** Usaré cargas conocidas para ajustar los "factores" en el código. Es un proceso de prueba y error hasta que los datos coincidan.
3. **Validación en campo:** Me voy a llevar el equipo a la casa en Tenango y lo voy a dejar midiendo de 24 a 72 horas seguidas. Quiero ver cómo se porta con el uso real de una familia.

---

## 8. Cronograma (Fases de mi trabajo)

| Fase | Qué voy a hacer | Inicio | Fin |
|---|---|---:|---:|
| F1 | Investigar antecedentes y armar el planteamiento técnico. | 02-Feb | 13-Feb |
| F2 | Definir objetivos y ver cómo impacta el proyecto. | 16-Feb | 06-Mar |
| F3 | Armar el marco teórico y ver qué más hay en el mercado. | 09-Mar | 20-Mar |
| F4 | Poner mis hipótesis y definir mis variables. | 23-Mar | 03-Abr |
| F5 | Diseñar toda la metodología y los pasos del experimento. | 06-Abr | 24-Abr |
| F6 | Juntar todo el protocolo, checar el presupuesto y las referencias. | 27-Abr | 29-May |

---

## 9. Presupuesto (Lo que voy a gastar)

Esto es lo que calculo que me voy a gastar en materiales:

| Concepto | Especificación técnica | Costo (MXN) |
|---|---|---|
| **ESP32 DevKit V1** | El microcontrolador principal. | $130.00 |
| **Sensor SCT-013-030** | El clip para medir la corriente. | $130.00 |
| **Sensor ZMPT101B** | Para medir el voltaje de forma segura. | $48.50 |
| **Fuente HLK-PM01** | Para alimentar todo desde el enchufe. | $89.00 |
| **Módulo MicroSD** | Para que no se pierdan los datos. | $18.90 |
| **Varios** | Cables, conectores, caja y soldadura. | $183.60 |
| **Total** | | **$600.00** |

---

## 10. Glosario y Referencias

### 10.1 Glosario técnico (A mi manera)

- **ADC:** Es la parte del chip que convierte la señal de los sensores en números que el código puede entender.
- **ESP32:** El cerebro del proyecto. Lo elegí porque es barato y tiene mucha potencia para manejar el WiFi.
- **NILM:** Es la técnica de medir todo desde un solo punto sin tener que andar cortando cables por toda la casa.
- **RMS:** Es el valor eficaz. Es lo que realmente importa para calcular cuánta luz estamos gastando.
- **TRMS:** Es una característica de los multímetros buenos para medir señales que no son una onda perfecta.
- **ZMPT101B:** Es el sensor que voy a usar para el voltaje; es clave para calcular la potencia activa real.

### 10.2 Referencias (Formato APA 7)

1. American Psychological Association. (2020). *Publication manual of the American Psychological Association* (7th ed.). https://apastyle.apa.org/
2. Comisión Federal de Electricidad. (2024). *Tarifas domésticas de energía eléctrica*. https://app.cfe.mx/Aplicaciones/CCFE/Tarifas/TarifasCRECasa/Casa.aspx
3. Data México, Secretaría de Economía. (2025). *Ingenieros Electrónicos: salarios y fuerza laboral*. https://www.economia.gob.mx/datamexico/es/profile/occupation/ingenieros-electronicos
4. Espressif Systems. (2022). *ESP32 Series Datasheet*. https://www.espressif.com/documentation/esp32_datasheet_en.pdf
5. Hart, G. W. (1992). Nonintrusive appliance load monitoring. *Proceedings of the IEEE, 80*(12), 1870–1891.
6. Kaselimi, M., Protopapadakis, E., Voulodimos, A., Doulamis, N., & Doulamis, A. (2022). Toward trustworthy energy disaggregation: A review of challenges, methods and perspectives for non-intrusive load monitoring. *Sensors, 22*(15), 5872. https://doi.org/10.3390/s22155872
7. Bland, J. M., & Altman, D. G. (1986). Statistical methods for assessing agreement between two methods of clinical measurement. *The Lancet, 1*(8476), 307–310.
8. Shapiro, S. S., & Wilk, M. B. (1965). An analysis of variance test for normality (complete samples). *Biometrika, 52*(3–4), 591–611.
9. Pigra. (2026). *ESP32D DEVKIT V1*. https://pigra.com.mx/electronica/73-esp32d.html
10. SANDOROBOTICS. (2026). *Sensor de Corriente No Invasivo 30A, SCT013*. https://sandorobotics.com.mx/producto/hr0214-118a/
11. Geek Factory. (2026). *Módulo Sensor de Voltaje AC Monofásico ZMPT101B*. https://www.geekfactory.mx/producto/sensor-voltaje-ac-zmpt101b/
12. Tecneu. (2026). *Convertidor AC-DC Fuente 5V HLK-PM01*. https://www.tecneu.com/products/convertidor-ac-dc-fuente-5v-hlk-pm01
13. ElectroCrea. (2026). *Módulo Micro SD*. https://electrocrea.com/products/modulo-microsd
