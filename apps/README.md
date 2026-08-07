# Apps

Productos completos: frontend, backend, base de datos y gente usándolos del otro lado.

---

# ⭐ De 0 a Remoto

**Plataforma de formación para personas que se mueven a trabajo remoto**, con tres
rutas: asistente virtual, marketing digital y project management.

`Next.js 15` · `Supabase` · `Stripe` · `Tailwind` · `TypeScript`
🟢 En vivo · 🔒 Repo privado

### El problema

Enseñar a conseguir trabajo remoto no escala si cada estudiante necesita atención
individual. Hacía falta que el contenido, el acceso y el cobro funcionaran solos.

### Qué construí

Una plataforma completa, no una landing con un checkout pegado:

- **Cuentas de estudiante** con autenticación y sesión persistente sobre Supabase
- **Contenido estructurado** por ruta, servido desde el repositorio y renderizado
  en el servidor
- **Pagos con Stripe** integrados al ciclo de acceso
- **Panel de administración** para gestionar contenido y estudiantes
- Migraciones de base de datos versionadas

### Decisiones de diseño

**Contenido en el repositorio, no en la base de datos.** Los cursos viven como
archivos versionados. Un cambio de contenido es un commit con historial y reversible,
no un UPDATE que nadie recuerda haber hecho. La base de datos guarda lo que cambia por
usuario: cuentas, accesos, progreso.

**Server-side rendering desde el inicio.** Es una plataforma que necesita ser
encontrada. Renderizar en el servidor no fue optimización tardía: fue la razón de
elegir el framework.

**Supabase en vez de montar auth propio.** Autenticación es el tipo de cosa donde
construir desde cero solo agrega superficie de error. Row Level Security resuelve el
aislamiento entre usuarios a nivel de base de datos, no a nivel de código que se puede
olvidar.

### Demo

`[FALTA: screenshots del dashboard y de una ruta de curso]`
`[CONFIRMAR: URL en vivo — hay dos despliegues y quiero poner el correcto]`

---

# ⭐ Generador de artículos con IA

**Sistema de generación de contenido para una agencia de SEO** que atendía 17+ marcas
de e-commerce.

`Python` · `IA generativa` · `Google Drive API`
🏢 Trabajo de cliente · código no publicado

### El problema

Producir un artículo tomaba **cerca de dos días**: investigación, esquema, borrador,
revisión interna, formato. Con 17 marcas que atender, el cuello de botella era el
volumen, y no se resolvía contratando.

### Qué construí

Un sistema que recibe un tema y una marca, y devuelve un borrador listo para revisión
editorial. La investigación, la estructura, la redacción y el formato los hace el
sistema. El juicio se queda con el editor.

### Resultado

- **200+ artículos** producidos
- De **~2 días por artículo** a **minutos más el tiempo de revisión del editor**

### Decisiones de diseño

**El editor no sale del circuito.** El sistema no publica: entrega un borrador. Sacar
al humano de un pipeline de contenido es como se termina publicando algo vergonzoso a
escala. La ganancia nunca estuvo en eliminar la revisión — estuvo en eliminar todo lo
que venía antes.

**Una marca, un perfil.** Cada cliente tiene su tono, su vocabulario y sus temas
prohibidos. Eso vive en configuración, no en el prompt. Agregar una marca es agregar
un archivo, no reescribir el sistema.

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

### El problema

El equipo operaba sobre Airtable. Funcionó hasta que dejó de hacerlo: el esquema había
crecido más allá de lo que una herramienta con forma de hoja de cálculo maneja bien, y
los flujos que el equipo realmente necesitaba se estaban simulando en vez de
soportarse.

### Qué construí

Lideré la migración a un CRM y dashboard internos, diseñados sobre el flujo real del
equipo y no sobre una plantilla.

### Resultado

En uso diario por las 12 personas del equipo. **Sigue corriendo después de que
terminó mi contrato**, que es la única prueba real de que una herramienta interna
estaba bien hecha.

### Lo que aprendí

**Lo difícil de una migración nunca son los datos.** Son las suposiciones que la
herramienta vieja tenía codificadas y que nadie escribió en ningún lado. Las descubres
cuando algo se rompe para la persona que dependía de eso.

Por eso la migración no fue un evento: fue un periodo de convivencia de los dos
sistemas, con el equipo usando el nuevo y reportando lo que faltaba.

---

# ⭐ Scheduler multiplataforma

**Programación y publicación automática de contenido en 9+ plataformas.**

`TypeScript`
🏢 Trabajo de cliente · código no publicado

### El problema

Publicar en nueve plataformas, tres posts en cada una, todos los días. Manual,
repetitivo, y del tipo de tarea donde un día saltado es invisible hasta que se acumula.

### Qué construí

Un scheduler que programa y publica en todo el conjunto de plataformas, automatizando
cinco de las nueve de punta a punta.

### Resultado

**9+ plataformas al día × 3 posts**, con el conjunto automatizado corriendo sin
supervisión.

### El límite, dicho en voz alta

**Cuatro de las nueve se quedaron manuales** porque sus APIs no soportaban lo que hacía
falta. No es un pendiente: es el límite del sistema y está documentado como tal.

Un sistema que declara dónde no llega es más confiable que uno que promete cobertura
total.

---

## El resto

| Proyecto | Qué es | Stack | Código |
|---|---|---|---|
| `[FALTA]` | | | |

_Pendiente de completar con lo que no entró arriba._
