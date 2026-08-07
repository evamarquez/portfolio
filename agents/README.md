# Agentes

Sistemas donde un modelo toma decisiones dentro de una estructura que yo diseñé.

La parte interesante nunca es que un agente escriba algo. Es qué le dejas decidir y
qué le quitas de las manos.

---

# ⭐ Newsletter Kit

**Dices "necesito un newsletter sobre X"** y el sistema investiga el tema, escribe la
edición, dibuja los gráficos de datos, genera la ilustración editorial, renderiza HTML
compatible con clientes de correo y deja un borrador listo. También puede correr solo
en un horario.

`Python` · `Jinja` · `Playwright` · `premailer` · `GitHub Actions` · `Cloudflare R2`
🟢 **[Código público](https://github.com/evamarquez/newsletter-kit)** · MIT

### La arquitectura

Construido sobre el patrón **WAT** (Workflows, Agents, Tools): SOPs en markdown
describen el trabajo, el agente orquesta, y scripts de Python ejecutan. El
razonamiento probabilístico se queda donde ayuda; todo lo repetible es código
determinista.

```
tema ─→ research_topic.py ──→ [issue.json] ──┬─→ make_infographic.py ──┐
        (5 ángulos en        (validado        │   (Playwright → PNG)    │
         paralelo)            contra schema)  └─→ generate_image.py ────┤
                                                                        ↓
  log_issue.py ←── send_gmail.py ──────────────────── render_newsletter.py
  (archivo)        (SMTP + imágenes CID)              (Jinja + premailer)
```

### Las dos reglas sobre las que descansa el diseño

**El agente nunca escribe HTML.** Produce un `issue.json` validado contra schema, y
plantillas Jinja fijas lo renderizan. El HTML de correo no es HTML web: Outlook
renderiza con el motor de Word, Gmail elimina casi todo el `<head>`, flexbox y grid
son inutilizables. El markup generado a mano se rompe distinto en cada edición. Esta
separación es la razón de que la edición #1 y la #40 se vean idénticas, y de que un
bug visual sea un cambio en un archivo y no un re-prompt.

**Los números nunca van dentro de una imagen generada.** Un modelo generativo no puede
garantizar que una barra dibujada para 47% mida proporcionalmente 47%, y puede alterar
un dígito de forma invisible. Dos carriles separados: un modelo dibuja conceptos, un
script dibuja datos desde los valores reales. El schema lo hace cumplir rechazando
dígitos en los prompts de imagen.

### Guardrails

Enviar es la única acción irreversible del sistema, así que está protegida en capas:
restricción de envío a nivel de marca, un workflow programado que no tiene la bandera
de envío en ningún lado, un mensaje por destinatario en vez de exponer la lista, y una
referencia de imagen rota tratada como error fatal y no como advertencia — una campaña
enviada no se puede recuperar.

### Aprendizajes documentados

El README incluye una sección de lo que salió mal: el autoescaping de Jinja rompiendo
un font stack de CSS de forma silenciosa, `strftime` usando el locale de la máquina y
no el del contenido, artefactos de CI que reportan éxito sin subir nada. Están ahí
porque es la parte que ahorra tiempo a quien construya algo parecido.

→ **[Ver el repositorio completo](https://github.com/evamarquez/newsletter-kit)**

---

# ⭐ Executive Assistant

**Asistente ejecutivo construido como sistema multi-agente**, no como una ventana de
chat con un prompt largo.

`Claude Code` · `Model Context Protocol` · `Firecrawl` · `Git`
🔒 Repo privado — contiene contexto personal de negocio

### El problema con el chat

Un asistente de chat olvida. Cada conversación empieza en cero, así que reexplicas tu
negocio, tus prioridades y tus preferencias antes de poder pedir algo. Te ayuda a
llegar al 50% en vez del 90%, y la diferencia es contexto que ya diste la semana
pasada.

### La arquitectura

```
CLAUDE.md          punteros, no contenido — se carga en cada mensaje
context/           quién soy, el negocio, prioridades, metas
.claude/
  rules/           un archivo por tema: tono, voz pública, criterios
  skills/          procedimientos invocables, con YAML front matter
  agents/          sub-agentes con contexto y modelo propios
projects/          una carpeta por frente activo, los outputs viven ahí
decisions/log.md   append-only: qué se decidió y por qué
```

### Tres decisiones de diseño

**El cerebro guarda punteros, no contenido.** `CLAUDE.md` se carga completo en cada
mensaje, así que meter ahí el contexto de negocio quemaría la ventana antes de la
primera pregunta. En su lugar dice *"si necesitas saber de prioridades, lee este
archivo"*. El contexto se carga bajo demanda. El archivo se queda bajo 150 líneas y el
sistema sabe todo.

**Skills y sub-agentes son herramientas distintas.** Una skill corre en el contexto
actual con el modelo actual: es un procedimiento que quieres que se siga. Un
sub-agente recibe contexto fresco y puede correr un modelo distinto y más barato: es
para trabajo que produce mucho output intermedio que nadie necesita ver. El research
que barre veinte fuentes va a un sub-agente; la conversación principal recibe el
reporte, no el proceso.

**Las decisiones son append-only.** Nunca se edita una entrada. Cuando algo cambia,
una nueva la revierte y explica por qué. Seis meses después el razonamiento es la
parte valiosa: *"probamos esto y no funcionó porque X"* es información cara de perder.

### Por qué mejora con el uso

Cada reporte, borrador y decisión se escribe a un archivo dentro del proyecto. Se
limpia la conversación y el asistente retoma leyéndolos. El sistema acumula en vez de
reiniciarse.

---

# ⭐ Agente de reportes

**Eliminó por completo un proceso manual recurrente** en una agencia de SEO.

🏢 Trabajo de cliente · código no publicado

### El problema

Un reporte recurrente que se armaba a mano: extraer los datos, ordenarlos, darles
formato y entregarlos. El tipo de tarea que consume una porción predecible de cada
semana y no deja nada que nadie recuerde haber hecho.

### Qué construí

Un agente que extrae los datos de las fuentes, arma el reporte y lo entrega.

### Resultado

El proceso manual desapareció de punta a punta. No se redujo: se eliminó.

### Decisión de diseño

**El agente no interpreta los números, los presenta.** Pedirle a un modelo que
concluya sobre datos de rendimiento es pedirle que invente una narrativa. Extrae,
calcula y formatea de manera determinista; el análisis lo hace quien conoce al cliente.

---

## El resto

Skills de Claude Code construidas durante un reto de 7 días de sistemas de IA:

| Skill | Qué hace |
|---|---|
| **Diagramas Excalidraw** | Genera diagramas editables a partir de una descripción |
| **Generación de imágenes controlada** | Prompts parametrizados en JSON para imágenes hiperrealistas, evitando el aspecto plástico de IA |
| **Frontend design** | Interfaces con criterio de diseño, evitando el resultado genérico |
| **Video a website** | Convierte un video en un sitio animado con scroll |

Cada una con YAML front matter que define **cuándo** invocarla, no solo qué hace.
