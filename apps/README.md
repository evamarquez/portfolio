# Apps

Productos completos: frontend, backend, base de datos y gente usándolos del otro lado.

---

# ⭐ De 0 a Remoto

**Plataforma de formación para conseguir trabajo remoto**, con cuentas de estudiante,
contenido por rutas y pagos.

`Next.js 15` · `Supabase` · `Stripe` · `Tailwind` · `TypeScript`
🟢 En vivo · 🔒 Repo privado · `[CONFIRMAR: URL]`

### Qué es

De 0 a Remoto es un negocio propio. Enseño a personas sin experiencia previa a
conseguir su primer trabajo remoto en tres áreas: **asistente virtual, marketing
digital y project management**. Cada área es una ruta con su propio contenido, sus
ejercicios y su camino de entrada al mercado.

La plataforma es donde vive todo eso. Una persona compra el acceso, crea su cuenta, y
entra a un panel donde ve su ruta, avanza por los módulos y descarga el material.
Del otro lado hay un panel de administración desde el que gestiono contenido,
estudiantes y accesos.

No es un curso en video colgado en una carpeta. Es una aplicación con autenticación,
base de datos, control de acceso por compra y contenido servido desde el servidor.

### El problema

Enseñar a conseguir trabajo remoto no escala si cada estudiante necesita atención
individual. Y las plataformas de cursos existentes cobran una comisión por cada venta,
imponen su diseño y no dejan construir la experiencia que el producto necesita.

Hacía falta que el contenido, el acceso y el cobro funcionaran solos, bajo mi control.

### Qué construí

- **Cuentas de estudiante** con autenticación, sesión persistente y recuperación de
  contraseña, sobre Supabase
- **Contenido estructurado por ruta**, versionado en el repositorio y renderizado en
  el servidor
- **Pagos con Stripe** conectados al ciclo de acceso: pagar desbloquea la ruta
- **Panel de administración** para gestionar contenido, estudiantes y accesos
- **Migraciones de base de datos versionadas**, no cambios manuales al esquema

### Decisiones de diseño

**El contenido vive en el repositorio, no en la base de datos.** Los cursos son
archivos versionados. Un cambio de contenido es un commit: tiene historial, se puede
revisar y se puede revertir. La base de datos guarda solo lo que cambia por usuario —
cuentas, accesos, progreso. Meter contenido en la base de datos habría significado
construir un editor, mantenerlo, y perder el historial de qué cambió y cuándo.

**Server-side rendering desde el inicio.** Es una plataforma que necesita ser
encontrada por gente buscando cómo trabajar remoto. Renderizar en el servidor no fue
una optimización posterior: fue la razón de elegir el framework.

**Supabase en vez de autenticación propia.** Auth es el tipo de cosa donde construir
desde cero solo agrega superficie de error. Row Level Security resuelve el aislamiento
entre usuarios **a nivel de base de datos**, no a nivel de código que se puede olvidar
en un endpoint.

`[FALTA: screenshots del panel de estudiante y del admin]`

---

# ⭐ Generador de artículos con IA

**Sistema de producción de contenido SEO** para una agencia que atendía 17+ marcas de
e-commerce.

`Python` · `IA generativa` · `Google Workspace APIs`
🏢 Trabajo de cliente · código no publicado

### Qué es

Una herramienta interna que usaba el equipo de contenido de la agencia. Se le indica
un **tema y una marca**, y devuelve un artículo en borrador, con su estructura, su
investigación incorporada y el formato listo — dentro del flujo de trabajo donde el
equipo ya trabajaba.

Cada marca cliente tiene su propio perfil: tono, vocabulario, temas que sí y temas que
no. El sistema lee ese perfil antes de escribir, así que el artículo para una marca de
colchones no sale con la voz de una marca de suplementos.

Lo usaban el content lead y el equipo editorial. Yo construí y mantuve el sistema; el
juicio editorial siempre se quedó con ellos.

### El problema

Producir un artículo tomaba **cerca de dos días**: investigación, esquema, borrador,
revisión interna, formato. Con 17 marcas que atender, el cuello de botella era el
volumen, y no se resolvía contratando más gente — se resolvía cambiando el proceso.

### Resultado

- **200+ artículos** producidos
- De **~2 días por artículo** a **minutos, más el tiempo de revisión del editor**

### Decisiones de diseño

**El editor no sale del circuito.** El sistema no publica: entrega un borrador. Sacar
al humano de un pipeline de contenido es como se termina publicando algo vergonzoso a
escala, y una marca de e-commerce de 7-9 cifras no puede permitirse eso. La ganancia
nunca estuvo en eliminar la revisión — estuvo en eliminar todo lo que venía antes.

**Una marca, un perfil en configuración.** El tono y las restricciones de cada cliente
viven en un archivo de configuración, no dentro del prompt. Agregar una marca nueva es
agregar un archivo. Si el tono estuviera en el prompt, cada cliente nuevo sería una
reescritura del sistema.

### Arquitectura

```
tema + marca
     ↓
[perfil de marca]  →  investigación  →  estructura
                                            ↓
                                        redacción
                                            ↓
                                     formato + entrega
                                            ↓
                              borrador → editor humano → publicación
```

---

# ⭐ CRM interno

**Reemplazo del Airtable en el que corría un equipo de 12 personas.**

`TypeScript` · `Lovable` · base de datos propia
🏢 Trabajo de cliente · código no publicado · 🟢 en uso diario hoy

### Qué es

El sistema donde la agencia lleva su operación: clientes, proyectos, estado de cada
entrega y quién es responsable de qué. Un dashboard interno construido sobre el flujo
real del equipo, con las vistas que cada rol necesita.

Lo usan las 12 personas del equipo todos los días. Reemplazó por completo la base de
Airtable que venían usando desde antes.

### El problema

El equipo operaba sobre Airtable. Funcionó hasta que dejó de hacerlo: el esquema había
crecido más allá de lo que una herramienta con forma de hoja de cálculo maneja bien, y
los flujos que el equipo realmente necesitaba se estaban **simulando** — con campos de
estado que en realidad eran pasos de un proceso, con vistas filtradas que en realidad
eran pantallas distintas.

Cuando estás usando una herramienta contra su diseño, cada mejora cuesta más que la
anterior.

### Qué construí

Lideré la migración completa: definición del esquema real, construcción del CRM y el
dashboard, traslado de datos y acompañamiento del equipo durante el cambio.

### Resultado

En uso diario por las 12 personas. **Sigue corriendo después de que terminó mi
contrato**, que es la única prueba real de que una herramienta interna estaba bien
hecha.

### Lo que aprendí

**Lo difícil de una migración nunca son los datos.** Son las suposiciones que la
herramienta vieja tenía codificadas y que nadie escribió en ningún lado. Las descubres
cuando algo se rompe para la persona que dependía de eso.

Por eso la migración no fue un evento de un día: fue un periodo de convivencia de los
dos sistemas, con el equipo usando el nuevo y reportando lo que faltaba.

---

# ⭐ Scheduler multiplataforma

**Programa y publica contenido en 9+ plataformas todos los días.**

`TypeScript`
🏢 Trabajo de cliente · código no publicado

### Qué es

Una herramienta interna donde el equipo carga el contenido de la semana y el sistema
se encarga de publicarlo: **9+ plataformas, 3 posts en cada una, todos los días**.

Tiene la cola de publicación, el calendario de lo que va a salir y el registro de lo
que ya salió. Para cinco de las nueve plataformas la publicación es automática de
punta a punta. Para las otras cuatro, el sistema prepara el contenido y avisa, pero
alguien lo publica a mano.

### El problema

Publicar en nueve plataformas, tres posts cada una, todos los días, a mano. Repetitivo,
y del tipo de tarea donde un día saltado es invisible hasta que se acumula y alguien
nota que un canal lleva dos semanas muerto.

### Resultado

**9+ plataformas al día × 3 posts**, con el conjunto automatizado corriendo sin
supervisión.

### El límite, dicho en voz alta

**Cuatro de las nueve se quedaron manuales** porque sus APIs no soportaban publicación
programada de terceros. No es un pendiente: es el límite del sistema y está
documentado como tal, con qué haría falta para levantarlo.

Un sistema que declara dónde no llega es más confiable que uno que promete cobertura
total y falla en silencio.

---

## El resto

| Proyecto | Qué es | Stack | Código |
|---|---|---|---|
| **Prototipo de CRM** | Primera versión del CRM interno, antes de la migración definitiva | TypeScript | 🏢 Cliente |
| **Web app de SEO** | Herramienta interna para análisis y seguimiento de posiciones | TypeScript | 🏢 Cliente |
