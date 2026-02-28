<!--
===================================================================
METADATOS DEL DOCUMENTO
===================================================================
Proyecto    : Diseño e Implementación de un Sistema IoT de Bajo
              Costo para la Monitorización No Intrusiva de Consumo
              Eléctrico Residencial mediante Arquitectura ESP32
Área        : Ingeniería Electrónica / Investigación Académica
-------------------------------------------------------------------
Archivo     : TALLER 1/Version humana.md
Tipo        : Borrador original del autor (perspectiva humana)
Descripción : Respuestas iniciales e intuitivas del investigador
              a las preguntas fundamentales del proyecto
              (problema, objetivos, delimitaciones), redactadas
              SIN asistencia de IA ni investigación bibliográfica
              previa. Representa el punto de partida conceptual
              y la visión personal del autor antes de cualquier
              refinamiento técnico.
Autor       : Investigador (humano) – sin asistencia externa
Creado      : 2026-02-25
Últ. mod.   : 2026-02-25
Etapa       : Taller de Investigación 1 – Ideación inicial
Estado      : SUPERADO – Conservado como referencia histórica
Notas       : Algunos planteamientos aquí han sido refinados o
              descartados en versiones posteriores. Ejemplo:
              el objetivo de "diseñar una estrategia de
              mercadotecnia" fue eliminado por quedar fuera
              del alcance académico. Las delimitaciones fueron
              expandidas significativamente en documentos
              posteriores. NO usar este archivo como fuente de
              datos técnicos actuales.
===================================================================
-->

Planteamiento del problema

- ¿Cual es el problema?
R = Falta de transparencia en el consumo electrico por parte de la CFE 
- ¿Cuales son sus causas?
R = Mediciones unilaterales por parte de la empresa
- ¿Que efecto genera?
R = Gasto economico directo sin certezas sobre los gastos reportados  
- ¿En que condiciones se presenta?
R = En el domicilio, con bajo presupuesto, en ionstalaciones sencillas
- ¿Cual es la probabilidad de solucionarlo?
R = Alta
- ¿Como se relaciona con otros similares?
R = Con el consumo de energia de cada aparato

Objetivos 

Principal:
- Registrar en un microcontrolador ESP32 las lecturas del consumo electrico domestico

Secundarios:
- Desarrollar un prototipo funcional con sensores
- Realizar mediciones reales para calibrar el modelo estadistico del dispositivo electronico
- Diseñar una estrategia de mercadotecnia para vender el producto 

Delimitaciones del proyecto

1. Limitado a lineas electricas de baja tension domesticas
2. Medicion aproximada basada en modelos estadisticos
3. Funcionamiento optimo dependiente de consiciones de instalacion