# Resumen Ejecutivo — Puelche: IA Basada en Agentes para la Evaluación de Compras Públicas

> Resumen ejecutivo elaborado a partir de la formulación FONDEF (`KB/FONDEF/Formulacion.md`).

## 1. Problema y oportunidad

La compra pública representa cerca del 12,7% del PIB en países OCDE y el 14,3% del gasto de gobierno en Chile (2021). En 2024, **Mercado Público** procesó más de 2 millones de órdenes de compra, movilizando **US$17.643 millones**. Pese a la madurez digital y regulatoria de Chile (Ley N°19.886 y Decreto N°661), la **evaluación cualitativa de ofertas sigue siendo un cuello de botella manual**, intensivo en tiempo y sensible institucionalmente:

- El tiempo promedio publicación–adjudicación fue de **43,2 días** en 2025.
- El **34,2%** de los procesos excedió sus plazos estimados (retraso promedio de 18,4 días, casos extremos de hasta 345 días).
- La etapa de evaluación y adjudicación concentra la mayoría de la litigación en compras públicas.

Mientras funciones periféricas (clasificación de gasto, detección de anomalías, comunicación con proveedores) tienen desarrollos, la aplicación de LLMs y sistemas agénticos a la **evaluación sustantiva de ofertas** sigue siendo una frontera sin resolver, tanto a nivel global como en Chile.

## 2. Solución propuesta

**Puelche** es un sistema de apoyo a la decisión asistido por IA que **aumenta —no reemplaza—** el trabajo de las comisiones evaluadoras en licitaciones públicas chilenas. Filtra, analiza y estructura la información de las bases y las ofertas, preservando **transparencia, trazabilidad, cumplimiento normativo y control humano (human-in-the-loop)**. Todas las decisiones vinculantes (admisibilidad, puntajes, ranking, adjudicación) permanecen bajo autoridad de los funcionarios públicos.

**Usuarios primarios:** unidades de adquisición, comisiones evaluadoras y equipos legales/financieros de apoyo. Se entrega como plataforma web segura, integrable a los flujos institucionales sin alterar procedimientos formales.

### Arquitectura modular multiagente (6 componentes)

1. **Módulo de Extracción de Datos** — Convierte documentación heterogénea (HTML, PDF, Word, imágenes) en texto estructurado mediante parsers y OCR, preservando trazabilidad al documento original.
2. **Módulo de Filtrado de Propuestas** — Verifica admisibilidad contra requisitos obligatorios de las bases mediante reglas explícitas + razonamiento asistido por LLM. Produce una **matriz de admisibilidad** trazable por oferente.
3. **Módulo de Apoyo a la Evaluación** — Identifica criterios y tablas de evaluación, planifica y descompone la búsqueda de evidencia en subagentes especializados, y consolida evidencia trazable por criterio (sin emitir decisiones vinculantes). Es el componente **más exigente técnicamente** y el foco del prototipo actual.
4. **Biblioteca de Skills y Herramientas de Cumplimiento** — Capa compartida y reutilizable de *tools* (funciones computacionales) y *skills* (capacidades procedurales), implementada bajo estándares emergentes (**Agent Skills Protocol** y **Model Context Protocol / MCP**) para interoperabilidad y auditabilidad.
5. **Capa de Interfaz de Usuario y Trazabilidad** — Interfaz que vincula cada resultado con su evidencia documental de origen, con control de acceso basado en roles integrado al gobierno del sistema.
6. **Optimización de Módulos Agénticos** — Ciclo de mejora "outer-loop" que refina el *harness* agéntico (biblioteca de skills, política supervisora y sustrato de representación) comparando salidas del sistema con evaluaciones humanas previas.

## 3. Estado y madurez tecnológica

- **TRL actual: 4** (tecnología validada en laboratorio). Existe un prototipo funcional del Módulo de Apoyo a la Evaluación probado sobre expedientes reales (evaluación de equipo profesional, metodología, plazos, integridad, impacto ambiental, experiencia del oferente, capacidades de software, etc.).
- **TRL objetivo: 7** (prototipo demostrado en entorno operacional), habilitando despliegue precomercial y adopción institucional (SERVIU y otras unidades de compra).

## 4. Objetivos

**Objetivo general:** Desarrollar un sistema agéntico que haga más eficientes los procesos de compra pública chilenos —sin comprometer transparencia, confianza ni cumplimiento normativo— detectando propuestas inadmisibles y entregando puntajes informados previos durante la evaluación.

**Objetivos específicos:**
1. Caracterizar y modelar el proceso de evaluación de licitaciones en SERVIU Metropolitano.
2. Diseñar y desarrollar la arquitectura multiagente (filtrado y apoyo a la evaluación).
3. Integrar los componentes en una plataforma funcional para las comisiones evaluadoras.
4. Validar experimentalmente con SERVIU RM mediante pilotos en modo *shadow*.
5. Transferir el conocimiento al equipo de SERVIU (capacitación y soporte técnico).

## 5. Resultado tecnológico e indicadores comprometidos

**Resultado:** *Puelche: Plataforma de Apoyo a la Decisión con IA Agéntica para la Evaluación de Compras Públicas* (mes 13), compuesta por los 6 módulos descritos.

**Metas de atributos (valores objetivo):**

| Indicador | Meta |
| :--- | :--- |
| Exactitud de inadmisibilidad | 75–95% |
| Confiabilidad inter-evaluador (F1) | ~80% |
| Reducción de tiempo de evaluación | 40% |
| Reducción de costo por evaluación | 40% |
| Cobertura de criterios de evaluación | 20 criterios |

Marco de evaluación en tres dimensiones: **eficacia** (exactitud, consistencia, cobertura), **eficiencia** (reducción de tiempo y costo) y **aceptación institucional** (experiencia de usuario y satisfacción de liderazgo).

### Hitos

- **Hito 1 (mes 10):** Desarrollo y validación técnica de la plataforma. Metas: exactitud >85%, F1 80%, <2 h por propuesta, <US$5 por propuesta, 15 criterios cubiertos.
- **Hito 2 (mes 22):** Transferencia institucional y piloto en SERVIU RM. Metas: 35% reducción de tiempo y costo, satisfacción usuarios 4/5 y liderazgo 4,5/5, 75% de procesos usando el sistema con 75% de conversión.

## 6. Diseño experimental (4 fases)

1. **Fase 1 — Diagnóstico ex-ante (0%):** Mapeo del flujo de trabajo, curación del dataset histórico, y línea base de tiempos y **costos de transacción** (encuesta de horas-persona cruzada con salarios y montos adjudicados). Componentes cuantitativo (API Mercado Público) y cualitativo (entrevistas, talleres, focus groups).
2. **Fase 2 — Validación in itinere (0%–60%):** Validación controlada del prototipo sobre casos históricos con refinamiento offline versionado. Métrica principal: **confiabilidad inter-evaluador** (Kappa de Cohen, Kappa ponderado cuadrático, F1) contra evaluaciones humanas previas como ground truth.
3. **Fase 3 — Integración en modo shadow (60%–95%):** Operación en paralelo a los evaluadores de SERVIU sin afectar decisiones oficiales; evalúa utilidad, usabilidad y trazabilidad, más satisfacción de usuarios y liderazgo.
4. **Fase 4 — Piloto asistido y evaluación ex-post (95%–100%):** Uso en producción de los *packets* de Puelche; evaluación económica de 4 pasos (ahorro administrativo neto), auditoría algorítmica de sesgos y estrategia de monitoreo continuo.

## 7. Mercado y estrategia de transferencia

- **TAM:** 1.086 instituciones compradoras en Mercado Público (~US$17,2 M ingresos recurrentes anuales potenciales).
- **SAM:** red de 16 SERVIU regionales bajo MINVU (~US$253.440 anuales).
- **SOM:** escenario conservador de 4 instituciones tras el piloto (~US$63.360 anuales).

**Ruta de transferencia por etapas:** validación piloto en modo *shadow* → adopción sectorial (red SERVIU/MINVU) → despliegue a mayor escala vía integración con Mercado Público (ChileCompra). Modelo operativo de largo plazo: **GovTech SaaS**, con propiedad del software en CENIA.

## 8. Entidad asociada, equipo y diferenciación

- **Socio validador:** **SERVIU Región Metropolitana (SERVIU RM)** como early adopter, aportando datos históricos, contraparte técnica y contexto para validación en modo *shadow* (10 procesos seleccionados).
- **Ecosistema CENIA:** el proyecto se inserta en la modernización de compras públicas liderada por CENIA (proyectos "Hazlo con IA" con municipios y piloto con SERVIU RM), cubriendo un paso adicional del ciclo de compra.
- **Equipo:** Felipe del Río (Director, PhD Cs. de la Computación PUC), Rodrigo Durán (Subdirector, CEO CENIA), Mitchell Bosley (Investigador, PhD Ciencia Política U. Michigan), Ismael Aguayo (Asistente de Investigación, sociología/NLP).

**Diferenciación clave frente a alternativas (RAG, fine-tuning supervisado, scoring predictivo):**
- Primer sistema **agéntico multiagente** enfocado en el cuello de botella de evaluación cualitativa de ofertas, sin requerir entrenamiento ML (despliegue rápido, bajo costo, mayor flexibilidad).
- **Reglas de compra explícitas y formalizadas** que aportan interpretabilidad y auditabilidad.
- **Governance-by-design / compliance-by-design:** alineado nativamente con privacidad, trazabilidad y regulación pública chilena (incl. anticipación a la Ley de IA en discusión), con configuración de retención cero de datos y sin uso de información de oferentes para entrenar LLMs.
- **Optimización outer-loop** que mejora el sistema en el tiempo, a diferencia de configuraciones estáticas.
