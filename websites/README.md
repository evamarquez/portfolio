# Websites

Sitios que diseñé y construí desde el código. No uso Figma: diseño directo en el
navegador.

---

# ⭐ Eras Conversion

**Sitio de una agencia de publicidad en Meta para negocios locales de servicios.**

`Next.js` · `TypeScript` · `Tailwind` · `Vercel`
🔒 Repo privado · `[CONFIRMAR: URL en vivo]`

### Qué es

Eras Conversion es una agencia que llevo en sociedad con dos socias. Nos
especializamos en **publicidad en Meta para negocios locales de servicios**: técnicos
de aire acondicionado, empresas de landscaping y servicios de limpieza. El tipo de
negocio que vive de que suene el teléfono.

Dentro de la sociedad **yo lidero el servicio de páginas web y las automatizaciones**.
Este sitio es la cara pública de la agencia: explica a qué nicho servimos, cómo
trabajamos y cómo empezar.

El visitante típico no es una startup. Es el dueño de un negocio de HVAC que quiere
más llamadas y no tiene tiempo ni interés en aprender de marketing. El sitio está
escrito para esa persona, no para otra agencia.

### El problema del negocio detrás del sitio

Nuestros clientes empezaron a pedir cada vez más **páginas web**, no solo pauta. El
objetivo era poder ofrecer las webs más económicas del nicho, y para cobrar menos hay
que **tardar menos**.

Ese es el problema que estoy resolviendo con sistemas: un cliente de HVAC y otro de
landscaping necesitan la misma estructura de página, las mismas secciones de
conversión y los mismos elementos de confianza. Cambia el copy, los colores y los
datos, no la arquitectura.

### Qué construí

- El sitio de la agencia, desde cero, en código
- Un **sistema de plantillas por nicho**: se scrapean 2-3 competidores del rubro, se
  analiza qué estructura y elementos de conversión tienen en común, y se destila una
  plantilla genérica reutilizable
- Automatizaciones para los clientes más avanzados

### Decisiones de diseño

**Plantilla por nicho, no plantilla genérica.** Una plantilla que sirve para todo no
sirve para nada: un negocio de HVAC necesita un bloque de emergencias 24/7 que a una
empresa de limpieza no le hace falta. Las plantillas se destilan del nicho real, no
de lo que se supone que un sitio de servicios debe tener.

**El sistema de diseño vive en código.** No uso herramientas de diseño. La escala
tipográfica, el espaciado y la paleta son tokens en el código, no decisiones que se
retoman en cada proyecto. Es lo que permite que la web número diez salga más rápido
que la primera sin verse igual.

`[FALTA: screenshot]`

---

# ⭐ by-evamarquez.com

**Mi sitio personal**, bilingüe, sobre el mismo stack que uso para producto.

`Next.js 15` · `Supabase` · `Tailwind` · `TypeScript` · `Vercel`
🟢 [En vivo](https://www.by-evamarquez.com/) · 🔒 Repo privado

### Qué es

El sitio donde vive mi trabajo público: quién soy, qué construyo y lo que voy
escribiendo sobre automatización e IA. Está en español e inglés porque mi audiencia
está partida entre Latinoamérica y Estados Unidos.

No es una landing de una página. Tiene secciones de contenido, navegación real y
está montado sobre Next.js con Supabase detrás — el mismo stack con el que construyo
producto, lo que significa que puede crecer a algo con cuentas y pagos sin rehacerse.

### Decisiones de diseño

**El contenido vive en archivos, no en un CMS.** Escribir una entrada es escribir un
archivo y hacer commit. Sin panel que mantener, sin base de datos que respaldar, y con
historial de cada cambio. Un CMS para un sitio de una persona es infraestructura que
mantienes a cambio de nada.

**Server-side rendering.** Un sitio personal que no aparece en búsqueda no cumple su
función.

**El mismo stack que uso para producto.** Podría haberlo hecho en un constructor
visual en una tarde. Lo hice en Next.js porque el sitio también es evidencia: alguien
que lo abre y mira el código ve cómo trabajo.

`[FALTA: screenshot]`

---

# ⭐ De 0 a Remoto — sitio del producto

**La cara pública de mi plataforma de formación en trabajo remoto.**

🟢 [En vivo](https://de-0-a-remoto.vercel.app) · 🔒 Repo privado

### Qué es

De 0 a Remoto es un negocio propio: enseño a conseguir trabajo remoto en tres áreas
— asistente virtual, marketing digital y project management. Este sitio es la parte de
captación, separada de la plataforma donde están los estudiantes.

Explica las tres rutas, el método, y lleva a la persona a la ruta que le corresponde.
El visitante llega sin saber para cuál de las tres sirve, así que el trabajo del sitio
es orientarlo antes de venderle.

### Decisión de diseño

**Sitio de marketing y plataforma, separados.** El sitio cambia seguido, según lo que
convierte. La plataforma cambia poco y no puede romperse. Acoplarlos habría hecho que
cada prueba de copy fuera un despliegue con riesgo sobre las cuentas de estudiantes
que ya pagaron.

`[FALTA: screenshot]`

---

# ⭐ Guía y tests de roles remotos

**Herramienta de evaluación que te dice para qué rol remoto encajas.**

`HTML` · `JavaScript`
🔒 Repo privado

### Qué es

Un test que hace preguntas sobre perfil, experiencia previa y preferencias de trabajo,
y devuelve **una ruta recomendada** — asistente virtual, marketing digital o project
management — junto con la guía correspondiente para empezar.

Funciona como puerta de entrada a De 0 a Remoto: la persona llega con la duda de si
esto es para ella, sale con una respuesta concreta y un primer paso.

### El problema

La pregunta que más se repetía entre quienes querían trabajar remoto no era "cómo
empiezo". Era **"para cuál de estos sirvo"**. Responderla una por una no escala, y
sin respuesta la gente no arranca.

### Decisiones de diseño

**Sin backend, a propósito.** Toda la lógica de evaluación corre en el navegador.
Nadie tiene que registrarse para obtener valor, no hay datos personales que custodiar,
y el costo de operación es cero.

**La captura de contacto va después del resultado.** Primero la persona recibe algo
útil, después se le pide el correo. Al revés, la mayoría abandona antes de terminar y
tú te quedas sin el dato y sin haber ayudado a nadie.

`[FALTA: screenshot del test y del resultado]`

---

## El resto

| Proyecto | Qué es | Stack | Estado |
|---|---|---|---|
| **Bienestar Natural** | Landing de producto para un negocio de bienestar | HTML | 🟢 Repo público |
| **Sitios de cliente** | Webs para clientes de la agencia, en el nicho de servicios locales | HTML · TypeScript | 🏢 No publicable |
