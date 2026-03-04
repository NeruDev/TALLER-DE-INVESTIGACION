<!--
===================================================================
METADATOS DEL DOCUMENTO (Referencia interna para IA)
===================================================================
Título      : Contexto de la Tarea
Descripción : Directivas de formato y estilo para los documentos
              de la carpeta TAREAS
Fecha       : 2026-03-03
===================================================================
-->

# Directivas de Formato para la Carpeta TAREAS

Los documentos contenidos en esta carpeta deben cumplir las siguientes directivas de formato y estilo, las cuales garantizan coherencia editorial y compatibilidad con el flujo de renderizado a PDF mediante Joplin.

## Estilo de Redacción

- **Registro académico formal.** La redacción debe emplear tercera persona o formas impersonales. Se evitan coloquialismos, contracciones y lenguaje subjetivo no sustentado.
- **Prosa continua, sin estilo enciclopédico.** Los documentos no deben incluir índices con hipervínculos internos, anclas de navegación (`<a name="...">`), enlaces de retorno al inicio (`⬆ Volver al inicio`) ni cualquier elemento orientado a la navegación dentro del documento (estilo Wikipedia). La estructura se transmite mediante encabezados jerárquicos y párrafos ordenados lógicamente.
- **Subdivisión de párrafos.** Para reducir la carga visual de texto plano, los bloques de contenido extensos deben subdividirse en párrafos cortos (3-6 oraciones máximo). Cada idea o argumento diferenciado merece su propio párrafo.
- **Secciones marcadas con encabezados.** Utilizar encabezados Markdown (`##`, `###`) para marcar cada sección temática del documento, pero sin generar controles de navegación, índices ni anclas.
- **Orden y cohesión argumentativa.** Cada sección debe fluir como parte de un argumento integrado, con transiciones explícitas entre ideas.

## Metadatos

Los metadatos de cada documento se incluyen como **comentarios HTML** al inicio del archivo, de modo que resulten invisibles al renderizar el Markdown en Joplin o al exportar a PDF. Su propósito es exclusivamente de referencia interna para la IA y para el control de versiones del repositorio.

Formato requerido:

```html
<!--
===================================================================
METADATOS DEL DOCUMENTO (Referencia interna para IA)
===================================================================
Título      : Título del documento
Subtítulo   : Subtítulo o nombre del proyecto
Autor       : Investigador
Fecha       : AAAA-MM-DD
Materia     : Taller de Investigación 1 — Tarea N
Idioma      : es-MX
Fuente      : Proyecto completo.md (documento maestro vigente)
Flujo PDF   : Markdown → Joplin → PDF
Notas       : Notas adicionales relevantes
===================================================================
-->
```

No se utilizan bloques YAML frontmatter (`---`), ya que Joplin no los procesa como metadatos de renderizado y aparecerían como texto visible en el PDF exportado.

## Formato de Texto

- **Encabezados:** Jerarquía `#` (nivel 1) para títulos principales, `##` (nivel 2) para secciones y `###` (nivel 3) para subsecciones. No utilizar más de tres niveles de profundidad.
- **Énfasis:** Cursiva (`*texto*`) para términos en inglés, nombres de software y títulos de obras. Negrita (`**texto**`) solo para definiciones clave dentro de párrafos extensos, con uso moderado.
- **Ecuaciones:** Emplear sintaxis LaTeX con `$...$` para ecuaciones en línea y `$$...$$` para ecuaciones en bloque. Toda variable debe definirse en el texto la primera vez que aparece.
- **Cifras monetarias:** Se utiliza `\$` (signo de pesos escapado con barra invertida) para evitar que Joplin interprete el símbolo como delimitador de ecuación LaTeX. Formato resultante: `\$600.00 MXN`, `\$1,500.00 MXN`. El separador de miles es la coma y los decimales se expresan con punto, seguidos de la abreviatura de la moneda.
- **Porcentajes:** Se expresan con el símbolo `%` precedido de un espacio normal.
- **Referencias:** Estilo APA 7.ª edición, citadas en texto como (Apellido, Año) y listadas al final del documento cuando la tarea lo requiera.

## Renderizado a PDF

El flujo de conversión es:

```
Markdown → Joplin → PDF
```

Joplin exporta a PDF directamente desde su vista de renderizado. Los metadatos del documento están en comentarios HTML y no aparecen en el resultado final. El formato visual (tipografía, márgenes, etc.) es controlado por la configuración interna de Joplin y, opcionalmente, por CSS personalizado cargado en la aplicación.

## Fuente de Verdad

El documento maestro del proyecto es `Proyecto completo.md`, ubicado en la raíz del repositorio. Cualquier dato, cifra o decisión de diseño que aparezca en los documentos de la carpeta TAREAS debe ser consistente con la versión vigente de dicho documento. En caso de discrepancia, prevalece siempre la información contenida en `Proyecto completo.md`.

## Directivas Específicas — TAREA 1.md

El archivo `TAREA 1.md` cubre la **definición del proyecto** y el **planteamiento del problema**. Además de las directivas generales anteriores, aplica las siguientes convenciones de presentación visual:

### Estilo de divulgación científica

El documento adopta un estilo de **revista de divulgación científica** que combina rigor académico con presentación visual atractiva. Los recursos empleados incluyen:

- **Nombre del proyecto como título principal.** El encabezado `#` corresponde al nombre completo del prototipo (por ejemplo, *SME-IoT: Sistema de Monitoreo Eléctrico Residencial basado en IoT*), no al nombre de la tarea.
- **Preguntas clave en blockquote.** Las preguntas orientadoras de cada sección se presentan con formato `> *¿Cuál es el problema?*` (blockquote + cursiva), para destacarlas visualmente del texto explicativo.
- **Tablas de comparación y especificaciones.** Se emplean tablas Markdown para presentar especificaciones del prototipo, comparaciones con alternativas comerciales, y matrices de riesgo-mitigación.
- **Listas numeradas y con viñetas.** Las características diferenciantes, los ejes de justificación y las enumeraciones de causas se presentan en listas, no embebidas en párrafos extensos.
- **Negrita en términos clave.** Los nombres de autores citados en el cuerpo del texto se resaltan en negrita dentro de las listas de antecedentes (por ejemplo, `- **Ramadan et al. (2024)**`).

### Referencias

Las referencias de `TAREA 1.md` son un subconjunto de las contenidas en `Proyecto completo.md`. Todas las URL y DOI deben corresponder a fuentes **accesibles en línea** (artículos *open access*, sitios institucionales, documentos públicos). Los libros y normas físicas se citan sin URL. El formato es APA 7.ª edición con la conjunción **"y"** (español) en lugar de "&".
