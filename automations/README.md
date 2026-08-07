# Automatizaciones

Sistemas que corren solos y le devuelven horas a alguien todas las semanas.
Ordenados por complejidad, no por dónde los construí.

---

# ⭐ Ciclo de vida completo de un cliente

**Onboarding y offboarding automatizados de punta a punta**, orquestando Slack, Google
Drive, Airtable y Fillout en una sola cadena.

`Make` · `Slack API` · `Google Drive API` · `Airtable` · `Fillout`
🏢 Trabajo de cliente · blueprints no publicados

### Qué es

Cuando una agencia firma un cliente nuevo, hay unas veinte cosas que tienen que pasar,
en orden, sin que se olvide ninguna. Y cuando un cliente se va, otras tantas. Todo eso
se hacía a mano, con checklist, y se olvidaban pasos.

Lo convertí en una cadena automatizada:

**Al entrar un cliente:**
1. Llega el formulario de onboarding → se valida el ID y se cargan los datos
2. Se crean los canales de Slack, interno y externo con el cliente
3. Se invita al equipo que corresponde a cada canal
4. Se crea la carpeta del cliente en Drive, con más de 4 plantillas ya copiadas dentro
5. Se guardan todos los IDs generados de vuelta en Airtable
6. Se agrega el bookmark del documento de PR al canal del cliente
7. Cuando el cliente acepta la invitación de Slack, se dispara la bienvenida, se le
   asigna la auditoría técnica al desarrollador, se crea la tarea en Airtable y se
   notifica al fundador para los documentos de facturación

**Al salir un cliente:**
Se archivan los canales, se mueve la carpeta a "Archived Brands", se actualizan los
flags en Airtable, y se notifica a operaciones con **el checklist de lo que sí queda
manual**.

### Decisiones de diseño

**Idempotencia sobre reintentos.** Estas cadenas tocan sistemas externos que fallan.
Cada paso verifica si su efecto ya existe antes de ejecutarlo, para que un reintento
no cree el canal de Slack dos veces ni duplique la carpeta.

**El offboarding entrega un checklist de lo manual.** No todo se puede automatizar —
hay accesos y contratos que alguien tiene que cerrar a mano. En vez de fingir cobertura
total, el sistema termina diciendo exactamente qué falta.

**La versión vieja está documentada como deprecada, con sus bugs.** El onboarding
anterior corría en Zapier y tenía cinco errores identificados: IDs incorrectos, un
canal hardcodeado y un JSON malformado. Está archivado con esos bugs escritos, porque
saber por qué se reemplazó algo vale más que borrarlo.

---

# ⭐ Pipeline de generación de blogs con IA

**Cadena multi-etapa que investiga, redacta y entrega artículos SEO**, con callbacks
asíncronos entre Make, Google Apps Script y tres proveedores de IA distintos.

`Make` · `Google Apps Script` · `OpenAI` · `Claude` · `Perplexity` · `Reddit API` · `Airtable`
🏢 Trabajo de cliente · blueprints no publicados

### Qué es

El sistema detrás de los 200+ artículos. No es una llamada a un modelo: es un pipeline
con varias fases, cada una en un sistema distinto, coordinadas por callbacks.

Produce dos tipos de artículo con estructuras distintas — *"Marca vs Competidor"* y
*"Alternativas al competidor"* — y cada uno tiene su propia cadena.

**Cómo corre una generación:**
1. Un checkbox en Airtable dispara el flujo, o alguien lo lanza manualmente
2. Make llama a Google Apps Script y **libera el hilo** — la generación tarda minutos
3. Fase de investigación: Perplexity para el research, y **la API de Reddit con OAuth
   para minar comentarios reales** sobre la marca y el competidor, con reintentos y
   manejo de errores
4. Fase de redacción: cuatro prompts encadenados de OpenAI, alternando modelos según
   la tarea
5. Se crea el Google Doc en la carpeta del sprint que corresponde
6. El script llama de vuelta al webhook de Make, que actualiza Airtable con la URL

### Decisiones de diseño

**Asíncrono con callback, no espera bloqueante.** Un flujo que espera minutos a que
termine un modelo consume operaciones y se cae por timeout. La generación se dispara,
el flujo termina, y el script avisa cuando acabó. Es la diferencia entre un pipeline
que escala y uno que se rompe con volumen.

**Cada proveedor donde es mejor.** Perplexity para búsqueda con fuentes, OpenAI para
redacción larga, Claude para el procesamiento de contenido raspado. Casar el sistema
con un solo proveedor habría significado usar la peor herramienta en dos de las tres
etapas.

**Reddit como fuente, no como relleno.** La diferencia entre un artículo genérico y
uno útil es si contiene lo que la gente realmente dice del producto. Minar comentarios
reales fue una decisión de calidad, no de volumen.

---

# ⭐ SC Lead Finder

**Encuentra negocios locales con webs malas y puntúa con qué producto entrarles.**
Corre solo cada lunes.

`TypeScript` · `Trigger.dev`
🔒 Repo privado · disponible bajo petición

### Qué es

Automatización de prospección para mi agencia. Cada lunes, sin que nadie la toque,
recorre negocios locales de South Carolina, evalúa el estado de su presencia web y
devuelve una lista **ordenada por oportunidad**.

Para cada negocio revisa si tiene sitio, si funciona, si está actualizado y qué tan mal
está. Con eso puntúa con qué producto acercarse: a uno sin web, una web desde cero; a
uno con web decente pero sin captación, pauta; a los más avanzados, automatización.

La salida es con lo que el equipo comercial arranca el lunes.

### Decisiones de diseño

**Desatendida de verdad.** No notifica para pedir permiso ni espera confirmación en un
paso intermedio. Si necesita supervisión semanal, no resolvió el problema — solo lo
movió de lugar.

**Puntúa, no solo lista.** Una lista de 200 negocios sin priorizar es tan inútil como
no tenerla. El valor está en el orden.

`[FALTA: ejemplo de salida, sin datos de negocios reales]`

---

# ⭐ Reconciliación de datos de pagos

**Dos estrategias complementarias para el mismo problema**: emparejar clientes de
Stripe con registros internos.

`Make` · `Stripe API` · `Airtable`
🏢 Trabajo de cliente · blueprints no publicados

### Qué es

El sistema de facturación y el CRM interno vivían separados, así que nadie sabía con
certeza qué registro de Airtable correspondía a qué cliente de Stripe. Eso rompe los
reportes de ingresos y el seguimiento de renovaciones.

Lo resolví con dos automatizaciones que se complementan:

**Reconciliación masiva** — recorre todos los clientes de Stripe y busca coincidencia
en Airtable por correo o por nombre, guardando el Customer ID donde corresponde. Limpia
el histórico.

**Listener en tiempo real** — escucha eventos de checkout de Stripe y, si es el primer
pago de ese cliente, captura el Customer ID en el momento. Evita que el problema
vuelva a crecer.

### Decisión de diseño

**Limpiar el pasado y cerrar la fuga, por separado.** Solo el listener habría dejado
sin resolver todo el histórico. Solo la reconciliación masiva habría requerido correrla
para siempre cada semana. Los dos juntos convierten un problema recurrente en uno
resuelto.

---

# ⭐ Pipeline de scraping estructurado

**Extrae la estructura de sitios competidores y destila una plantilla reutilizable.**

`Firecrawl` · `Claude Code` · workflows en markdown

### Qué es

Resuelve un problema concreto de mi agencia: **cuando llega un cliente nuevo de un
nicho, no armar la página desde cero.**

Se le apunta a 2-3 competidores del rubro — técnicos de aire acondicionado, por
ejemplo — y el pipeline scrapea sus sitios, analiza qué estructura, secciones y
elementos de conversión tienen en común, y **produce una plantilla genérica** para ese
nicho. Después, con el cliente real, solo se cambian datos, colores y copy.

Es la diferencia entre entregar una web en dos semanas o en dos días.

### Decisiones de diseño

**La salida no es data cruda, es una plantilla.** Scrapear tres competidores y guardar
el HTML no sirve de nada. El valor está en qué tienen en común y qué de eso se
reutiliza. Ese análisis es parte del pipeline; si no, solo movió el trabajo.

**El proceso vive en markdown, la ejecución en código.** Los SOPs describen qué hacer
y en qué orden; las herramientas ejecutan. Cambiar el criterio es editar un documento.

---

## El resto del catálogo

**40 automatizaciones documentadas**, cada una con su blueprint exportable y sus notas
de qué hace, de qué depende y cómo migrarla. Una muestra:

| Automatización | Qué hace |
|---|---|
| **Balanceo de carga de backlinks** | Asigna cada backlink al slot del sprint con menos carga, equilibrando por fecha de entrega |
| **Monitor de tiendas** | Vigila cambios de tema en las tiendas Shopify de los clientes y alerta si detecta modificaciones |
| **Watcher de correo** | Captura reportes de Ahrefs y SEMrush desde Gmail, los guarda, espera a que se vinculen por dominio y notifica al canal del cliente |
| **RSS de competidores** | Cron diario que lee el RSS de sitios competidores y guarda los artículos nuevos en una base dedicada |
| **Estructura de sprints en Drive** | Al crear un sprint, genera la jerarquía de carpetas y guarda los IDs de vuelta en el registro |
| **Documentos por página** | Copia la plantilla correcta según el tipo de página y enlaza el documento al registro |
| **Reporte mensual por Slack** | Itera clientes y marcas, arma y envía el reporte de rendimiento |
| **Resumen semanal de entregas** | Cron de viernes: resumen de backlinks y páginas entregadas, al canal de cada marca |
| **Scraper con procesamiento IA** | Raspa la URL viva de una página, la procesa con Claude y genera el documento, sin duplicar si ya existe |
| **Subescenario de clientes** | Componente reutilizable que devuelve todos los clientes con sus marcas, llamado por las demás automatizaciones |

### Cómo pienso este trabajo

**Automatizar lo repetible, dejar el juicio en manos humanas.** Cada sistema elimina
trabajo mecánico y deja la decisión con una persona.

**Los subescenarios existen por algo.** Cuando diez automatizaciones necesitan la
lista de clientes, se construye una vez y las demás la llaman. Copiar la lógica diez
veces es garantizar que nueve queden desactualizadas.

**Escribe el SOP o no pasó.** Un sistema que solo una persona sabe operar es un pasivo.
Las 40 quedaron documentadas con su blueprint y sus notas — por eso el equipo pudo
seguir operándolas cuando terminó mi contrato.

**Documenta los bugs, incluso los tuyos.** Varias automatizaciones tienen advertencias
escritas: una búsqueda sin filtro que puede fallar con múltiples clientes, un ID usado
contra la tabla equivocada, un blueprint parcial. Están anotadas para quien venga
después, no escondidas.
