# Puelche — Incertidumbres Tecnológicas

**Propósito.** Este documento identifica las principales *incertidumbres tecnológicas* del proyecto Puelche: aspectos del sistema cuyo resultado no puede garantizarse de antemano a partir del conocimiento actual, las herramientas existentes o la experiencia previa, y que por lo tanto requieren experimentación para resolverse. Estos son los riesgos genuinos de I+D que distinguen al proyecto de la ingeniería de rutina, y los que el trabajo de validación (desde la Fase 2 en adelante) está diseñado para reducir.

Las incertidumbres se describen primero siguiendo el flujo de procesamiento del sistema (desde la ingesta de documentos hasta la evaluación y la optimización). Luego se **reordenan según la importancia percibida del riesgo** para el proyecto al final del documento.

---

## Incertidumbres Identificadas

### U1. Extracción de documentos y reconstrucción estructural a partir de fuentes heterogéneas y de baja calidad
Los archivos de licitación llegan como HTML, PDF nativos, MS Word y documentos escaneados o basados en imágenes de calidad dispar, con tablas complejas, diseños mixtos y estructura inconsistente. Es incierto si el pipeline de OCR y análisis con reconocimiento de diseño (*layout-aware*) puede recuperar de forma confiable el texto *y* las relaciones estructurales (secciones, tablas, anexos) necesarias aguas abajo, preservando referencias trazables a la fuente. Todo lo que hace el sistema depende de que esta reconstrucción sea fiel.

### U2. Extracción y formalización automática de reglas de admisibilidad y criterios de evaluación desde los documentos de licitación
La premisa central de Puelche es que las condiciones de admisibilidad y los criterios de puntuación se leen *dinámicamente* desde las bases de cada licitación, en lugar de estar codificados de forma rígida. Estas reglas se expresan de manera inconsistente entre licitaciones —en prosa, tablas y referencias cruzadas—, por lo que es incierto si el sistema puede extraerlas y formalizarlas en reglas y esquemas de puntuación explícitos y utilizables por la máquina, de forma genérica entre distintos tipos de licitación. Este es el diferenciador central frente a los sistemas rígidos basados en plantillas y la fuente más profunda de riesgo técnico.

### U3. Recuperación confiable de evidencia y anclaje (*grounding*) dentro de propuestas extensas y no estructuradas
Para cada criterio, los subagentes deben localizar la evidencia relevante dispersa en propuestas extensas y de organización variable (currículos, diplomas, contratos, facturas, anexos) y citarla con precisión. Es incierto si la recuperación será *completa* (encontrar toda la evidencia relevante) y si las salidas pueden anclarse a la fuente correcta sin citas alucinadas o mal vinculadas —un requisito que es a la vez técnico y legalmente esencial para la trazabilidad.

### U4. Concordancia de la evaluación agéntica con el juicio experto humano (fiabilidad inter-evaluador)
El KPI comprometido es la concordancia entre las evaluaciones de Puelche y las evaluaciones de expertos humanos (Kappa de Cohen / Kappa Ponderado Cuadrático / F1 en el rango 0,70–0,90). Es incierto si un sistema agéntico puede alcanzar este nivel de concordancia en criterios cualitativos y en parte subjetivos (por ejemplo, calidad de la metodología, idoneidad del equipo), donde incluso los evaluadores humanos difieren entre sí. Esto constituye, en la práctica, la puerta de decisión (*go/no-go*) del proyecto hacia el modo sombra (*shadow mode*).

### U5. Confiabilidad, repetibilidad y controlabilidad de la orquestación multiagente
La arquitectura encadena un agente planificador, subagentes especializados e invocaciones de herramientas/habilidades. Los pipelines multiagente acumulan errores a lo largo de los pasos, y la estocasticidad de los LLM amenaza la repetibilidad. Es incierto si la invocación de herramientas, la descomposición de tareas y la coordinación de agentes pueden hacerse lo suficientemente confiables y repetibles —bajo configuraciones congeladas— para producir salidas consistentes y auditables, aptas para un contexto administrativo/legal.

### U6. Efectividad y generalización del marco de optimización de bucle externo (*outer loop*)
La propuesta introduce un bucle de optimización externo que refina el *harness* agéntico (biblioteca de habilidades, política supervisora, sustrato de representación) contra casos evaluados por humanos. Se trata de un método novedoso y en gran medida no probado. Es incierto si producirá una mejora medible y *generalizable*, en lugar de un sobreajuste (*overfitting*) a un pequeño conjunto de casos históricos, y si las ganancias se transfieren a licitaciones no vistas.

### U7. Generalización entre tipos de licitación y cobertura de criterios de evaluación bajo escasez de datos
El proyecto se compromete a operacionalizar ~20 tipos de criterios en diversos contextos de contratación, pero el volumen de casos históricos con verdad de referencia (*ground truth*) humana confiable es limitado. Es incierto si el sistema generalizará entre tipos de licitación y alcanzará la cobertura objetivo cumpliendo a la vez los umbrales de fiabilidad, dado lo escasos que son los ejemplos etiquetados por tipo de criterio.

### U8. Costo operacional y latencia a escala institucional
Las metas comprometidas son < ~2 horas y < ~US$5 por propuesta. El razonamiento multiagente sobre documentos extensos puede consumir grandes cantidades de tokens y tiempo. Es incierto si estas metas de eficiencia pueden cumplirse simultáneamente con la exactitud requerida, especialmente a medida que crecen la cobertura y el volumen documental.

### U9. Sesgo algorítmico, equidad y dependencia de una verdad de referencia humana ruidosa
Dos incertidumbres entrelazadas: (a) si la evaluación basada en LLM introduce sesgo sistemático o discriminación en un contexto legalmente sensible, y (b) si las evaluaciones humanas históricas utilizadas como verdad de referencia son en sí mismas lo suficientemente consistentes para validar contra ellas —bases de referencia ruidosas o inconsistentes pueden tanto subestimar como enmascarar el desempeño real del sistema.

---

## Priorización por Importancia del Riesgo

Ordenadas según el riesgo percibido para el éxito del proyecto (combinación de la probabilidad de dificultad y el impacto sobre los resultados comprometidos / la meta de TRL-7).

| Rango | Incertidumbre | Por qué ocupa este lugar |
| :--- | :--- | :--- |
| 1 | **U2 — Extracción de reglas y criterios desde los documentos de licitación** | La innovación central y la propuesta de valor. Si la extracción dinámica de reglas/criterios no es robusta, toda la arquitectura diferenciada falla y el sistema se reduce a una herramienta rígida de plantilla. Máximo impacto, alta dificultad. |
| 2 | **U4 — Fiabilidad inter-evaluador frente a expertos humanos** | El KPI comprometido principal y la puerta explícita hacia el modo sombra. Alcanzar concordancia a nivel humano en criterios subjetivos es genuinamente incierto y determina directamente si se cumplen los hitos y el TRL-7. |
| 3 | **U1 — Calidad de la extracción de documentos** | Fundacional: todo el razonamiento aguas abajo depende de una recuperación fiel de texto/estructura. Algo mitigado por herramientas maduras, pero la heterogeneidad de los documentos chilenos hace que el fallo sea muy consecuente. |
| 4 | **U3 — Recuperación de evidencia y citas ancladas** | Sustenta directamente la trazabilidad, la confianza y la defensibilidad legal. Una recuperación incompleta o citas alucinadas socavarían tanto la exactitud como el modelo de cumplimiento con humano en el bucle. |
| 5 | **U5 — Confiabilidad y repetibilidad de la orquestación** | Los errores multiagente que se acumulan y el no-determinismo amenazan la consistencia y auditabilidad requeridas en un entorno administrativo; tratable pero no garantizado. |
| 6 | **U7 — Generalización y cobertura bajo escasez de datos** | La meta de cobertura de 20 criterios entre tipos de licitación es ambiciosa dada la escasez de datos etiquetados; afecta más a la amplitud del resultado comprometido que a su factibilidad. |
| 7 | **U6 — Efectividad de la optimización de bucle externo** | Novedosa y de alta incertidumbre, pero es una *mejora* más que una precondición: el sistema puede funcionar y validarse sin ganancias dramáticas de optimización. El sobreajuste es la principal preocupación. |
| 8 | **U9 — Sesgo/equidad y verdad de referencia ruidosa** | Importante para la legitimidad y para la validez de las mediciones de la Fase 2, pero se aborda principalmente mediante monitoreo/auditoría en lugar de bloquear la factibilidad central. |
| 9 | **U8 — Costo y latencia a escala** | Real, pero la más tratable desde la ingeniería (selección de modelos, *caching*, acotamiento de alcance); una cuestión de optimización y configuración más que de factibilidad fundamental. |
