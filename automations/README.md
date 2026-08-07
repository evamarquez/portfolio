# Automatizaciones

Sistemas que corren solos y le devuelven horas a alguien todas las semanas.

---

# ⭐ 80+ automatizaciones en producción

**Toda la capa de automatización de una agencia de SEO** que atendía 17+ marcas de
e-commerce de 7-9 cifras en Estados Unidos, Australia y Reino Unido.

`Make` · `Trigger.dev` · `Python` · `Airtable` · `Google Workspace APIs`
🏢 Trabajo de cliente · código no publicado

### El contexto

Equipo de 12 personas. Mi terreno eran las automatizaciones y las herramientas
internas, no el trabajo de cliente. Siete meses de contrato.

### Resultado

- **80+ automatizaciones entregadas a producción**
- El conjunto principal **siguió corriendo después de que terminó el contrato**
- **~200 colecciones y páginas** optimizadas con procesos sistematizados
- Los **SOPs** que el equipo usa para operar y extender estos sistemas

### Cómo pienso este trabajo

**Automatizar lo repetible, dejar el juicio en manos humanas.** Cada sistema que
construí elimina trabajo mecánico y deja la decisión con una persona. No es cautela:
es donde está la palanca real. Los dos días que costaba investigar y dar formato nunca
fueron la parte valiosa.

**Determinista donde se pueda, probabilístico donde haga falta.** Los modelos de
lenguaje son buenos razonando sobre entradas desordenadas y malos haciendo lo mismo
idéntico cuarenta veces. Todo lo repetible debe ser código.

**Escribe el SOP o no pasó.** Un sistema que solo una persona sabe operar es un
pasivo, no un activo. La prueba es que estos siguieron funcionando cuando me fui.

**Declara los límites.** De nueve plataformas del scheduler, cuatro quedaron manuales
porque sus APIs no lo permitían. Decir qué partes no funcionaron es lo que hace
creíble el resto.

### Arquitectura general

```
   disparadores                  capa de ejecución              destinos
   ─────────────                 ─────────────────              ────────
   programado (cron)   ─┐                                   ┌─► CMS / tienda
   webhook             ─┼──►  orquestador  ──►  workers  ───┼─► base de datos
   cambio en base      ─┤     (reglas +        (tareas      ├─► plataformas sociales
   acción manual       ─┘      colas)           pesadas)    └─► reportes / Sheets
                                   │
                                   └──► registro de ejecución + alertas
```

---

# ⭐ SC Lead Finder

**Encuentra negocios locales con webs malas o inexistentes y calcula con qué producto
entrarles.** Corre solo cada lunes.

`TypeScript` · `Trigger.dev`
🔒 Repo privado · disponible bajo petición

### El problema

Prospectar negocios locales es trabajo de búsqueda repetitivo: revisar si tienen web,
si funciona, si está actualizada, y decidir qué ofrecerles. Hacerlo a mano cuesta
horas y se hace tarde o no se hace.

### Qué construí

Una automatización desatendida que corre cada lunes: recorre negocios locales en un
mercado definido, evalúa el estado de su presencia web, y **puntúa con qué producto
tiene sentido acercarse** — desde una web desde cero hasta automatización para los más
avanzados.

### Decisiones de diseño

**Desatendida de verdad.** No notifica para pedir permiso ni espera confirmación en
un paso intermedio. Si necesita supervisión semanal, no resolvió el problema.

**Puntúa, no solo lista.** Una lista de 200 negocios sin priorizar es tan inútil como
no tenerla. La salida viene ordenada por dónde hay más probabilidad de cerrar.

`[FALTA: ejemplo de salida, sin datos de negocios reales]`

---

# ⭐ Pipeline de scraping estructurado

**Extracción de datos de sitios web con workflows y plantillas reutilizables.**

`Firecrawl` · `Claude Code` · workflows en markdown

### Qué construí

Un pipeline de scraping donde el proceso vive como SOPs en markdown y las herramientas
ejecutan. Se le apunta a un conjunto de sitios competidores, extrae la estructura, y
destila una plantilla genérica reutilizable — por ejemplo, la estructura común de las
webs de un nicho de servicios técnicos.

### Decisión de diseño

**La salida no es data cruda, es una plantilla.** Scrapear tres competidores y
guardar el HTML no sirve de nada. El valor está en el paso siguiente: qué tienen en
común y qué de eso se puede reutilizar. Ese análisis es parte del pipeline, no algo
que se hace después a mano.

---

# ⭐ Automatizaciones programadas con Trigger.dev

**Trabajos recurrentes que corren en la nube, con reintentos y visibilidad.**

`TypeScript` · `Trigger.dev`

### Por qué Trigger.dev y no un cron

Un cron en un servidor propio funciona hasta que falla en silencio. Trigger.dev da
reintentos con backoff, historial de ejecuciones y alertas cuando algo se rompe.

Para automatización desatendida, **saber que falló importa más que la automatización
misma**. Un proceso que corre mal durante tres semanas sin que nadie se entere es peor
que no tenerlo.

---

## El resto

Construido durante un reto de 7 días de sistemas de IA:

| Proyecto | Qué es |
|---|---|
| **Framework WAT** | Patrón Workflows-Agents-Tools: SOPs en markdown describen el trabajo, el agente orquesta, los scripts ejecutan. Es la base de `newsletter-kit` |
| **Generador de webs** | Pipeline para producir sitios desde plantillas por nicho |
| **Migración y sincronización de datos** | Automatizaciones de traslado entre sistemas |
| **Syndication de contenido** | Distribución automática a plataformas externas |

`[FALTA: confirmar cuáles de estos quieres publicar]`
