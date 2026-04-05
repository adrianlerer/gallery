# SafeZone — Skill Anti-Bullying Escolar

Skill de Google AI Edge Gallery para [SafeZone](https://fairsupport-safezone.vercel.app), aplicacion de concientizacion y acompañamiento contra el acoso escolar en Argentina.

## Descripcion

SafeZone asiste a cuatro roles de la comunidad educativa argentina: alumno/a (8-17 años), testigo (bystander), padre/madre y docente/directivo. Cada rol recibe orientacion personalizada, con tono y protocolo adaptados. El asistente ayuda a identificar situaciones de bullying, registrarlas y entender los pasos disponibles segun el marco legal argentino.

**No es psicologo ni terapeuta.** Es una herramienta de orientacion, concientizacion y documentacion.

## Modelo objetivo

**Gemma 4 E2B** — 128K contexto, ~50 tok/s. Respuestas en español rioplatense.

## Archivos

| Archivo | Descripcion |
|---------|-------------|
| `SKILL.md` | Instrucciones del sistema para el modelo LLM |
| `scripts/index.html` | Interfaz WebView + logica de persistencia (localStorage) |

## Roles

| Rol | Pronombre | Descripcion |
|-----|-----------|-------------|
| `alumno` | vos | Chicos/as de 8 a 17 años que sufren bullying |
| `testigo` | vos | Bystanders que presencian el acoso |
| `padre` | usted | Padres y madres preocupados por sus hijos |
| `docente` | usted | Docentes y directivos que gestionan situaciones |

## Acciones del WebView

| Accion | Descripcion |
|--------|-------------|
| `set_role` | Establece el rol activo (persiste en localStorage) |
| `get_role` | Consulta el rol activo |
| `log_situation` | Registra una situacion de bullying con fecha, tipo y severidad |
| `get_situations` | Lista situaciones de los ultimos N dias |
| `export_situations` | Genera texto plano para presentar a la escuela o autoridades |
| `get_resources` | Muestra lineas de ayuda y resumen del marco legal |

## Tipos de bullying soportados

`verbal` | `fisica` | `social` | `ciber` | `prejuicio`

## Lineas de ayuda incluidas

- **102** — NNyA, 24h gratuita y confidencial
- **135** — CAPS, crisis emocional e ideacion suicida
- **137** — Violencia familiar
- **911** — Emergencias
- **0800 33 347225** — Unidad Fiscal CABA (ciberbullying)

## Marco legal

- Ley 26.892 (2013): Convivencia escolar
- Ley 26.061 (2005): Proteccion integral NNyA
- Res. 1473/MEDGC/25 (CABA): Protocolo integral anti-bullying
- Ley 23.592: Actos discriminatorios
- CDN (rango constitucional desde 1994)

## Uso en el asistente

Flujo tipico:

```
Usuario: "Me molestan en el recreo"
Asistente: [llama get_role para verificar rol]
Asistente: [si no hay rol, pregunta y llama set_role]
Asistente: [responde segun rol activo con orientacion concreta]
Asistente: [si el usuario quiere registrar, llama log_situation]
```

Flujo de crisis:

```
Usuario: "No quiero seguir viviendo"
Asistente: Linea 102 + Linea 135 de inmediato. Pregunta si esta en lugar seguro.
```

## Desarrollo

Aplicacion fuente: [fairsupport-safezone.vercel.app](https://fairsupport-safezone.vercel.app)

Base de conocimiento: `fairsupport-safezone-pwa/src/data/knowledge-base.ts` (1.104 lineas)

Fuentes normativas: Ley 26.892, Ley 26.061, Res. 1473/MEDGC/25, CDN, CONICET/UNCuyo estudio CACE-44, UNESCO, groomingarg.org.
