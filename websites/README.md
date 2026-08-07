# Websites

Sitios que diseñé y construí, desde el código. No uso Figma: diseño directo en el
navegador.

---

# ⭐ by-evamarquez.com

**Sitio personal**, bilingüe, construido sobre el mismo stack que uso para producto.

`Next.js 15` · `Supabase` · `Tailwind` · `TypeScript` · `Vercel`
🟢 [En vivo](https://www.by-evamarquez.com/) · 🔒 Repo privado

### Qué es

Sitio propio con contenido versionado en el repositorio y renderizado en servidor.
No es una plantilla adaptada: es el mismo stack que uso para construir producto, lo
que significa que puede crecer a algo con cuentas y pagos sin rehacerlo.

### Decisiones de diseño

**El contenido vive en archivos, no en un CMS.** Escribir una entrada es escribir un
archivo y hacer commit. Sin panel que mantener, sin base de datos que respaldar, y con
historial completo de cada cambio.

**Server-side rendering.** Un sitio personal que no se encuentra en búsqueda no
cumple su función.

`[FALTA: screenshot]`

---

# ⭐ De 0 a Remoto — sitio del producto

**Sitio de captación** para la plataforma de formación.

🟢 [En vivo](https://de-0-a-remoto.vercel.app) · 🔒 Repo privado

### Qué es

La cara pública del producto: explica las tres rutas de formación, el método y el
camino de entrada. Separado de la plataforma con cuentas para que se pueda iterar el
mensaje sin tocar el sistema donde están los estudiantes.

### Decisión de diseño

**Sitio de marketing y plataforma separados.** El sitio cambia seguido, según lo que
convierte. La plataforma cambia poco y no puede romperse. Acoplarlos habría hecho que
cada prueba de copy fuera un despliegue con riesgo sobre las cuentas de los estudiantes.

`[FALTA: screenshot]`

---

# ⭐ Guía y tests de roles remotos

**Herramienta de evaluación** que ayuda a alguien a identificar para qué rol remoto
encaja mejor.

`HTML` · `JavaScript`
🔒 Repo privado

### El problema

La pregunta que más se repetía entre quienes querían trabajar remoto no era "cómo
empiezo", era **"para cuál de estos sirvo"**. Responderla uno por uno no escala.

### Qué construí

Un test que evalúa perfil y devuelve una ruta recomendada — asistente virtual,
marketing digital o project management — junto con la guía correspondiente.

### Decisión de diseño

**Sin backend a propósito.** Toda la lógica corre en el navegador. Nadie tiene que
registrarse para obtener valor, no hay datos personales que custodiar, y el costo de
operación es cero. La captura de contacto viene *después* del resultado, cuando la
persona ya recibió algo útil.

`[FALTA: screenshot del test y del resultado]`

---

## El resto

| Proyecto | Qué es | Stack | Estado |
|---|---|---|---|
| **Eras Conversion** | Sitio de la agencia de publicidad en Meta para negocios locales de servicios — HVAC, landscaping, limpieza. Lidero el servicio web | TypeScript · Next.js | 🔴 Despliegue caído |
| **Bienestar Natural** | Landing de producto | HTML | 🟢 Repo público |
| **Sitios de cliente** | Trabajo web para clientes de la agencia | HTML · TypeScript | 🏢 No publicable |
