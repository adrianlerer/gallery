# FairPlay Deportivo

**Entrenamiento mental deportivo para jovenes atletas, padres y entrenadores.**

Skill para Google AI Edge Gallery, optimizada para **Gemma 4 E2B** (128K contexto, ~50 tok/s). Todas las respuestas en espanol rioplatense.

Aplicacion de referencia: [fairsupport.app](https://fairsupport.app)

---

## Descripcion

FairPlay acompana a jovenes deportistas de 8 a 17 anos, a sus padres y a sus entrenadores en el trabajo de preparacion mental: manejo de la ansiedad competitiva, el error, la presion externa y la identidad mas alla del resultado. El corpus de conocimiento esta basado en psicologia deportiva (Dosil, Banchs, Gallwey, Cyrulnik y otros).

---

## Roles

| Rol | Tono | Enfoque |
|-----|------|---------|
| `jugador` | Vos, calido, emojis moderados | Validar emociones, entrenar la mente, separar valor del marcador |
| `padre` | Usted, calido y profesional | Acompanar sin presionar, carino incondicional |
| `entrenador` | Vos, profesional | Herramientas de preparacion mental para el equipo |

---

## Acciones del script

El archivo `scripts/index.html` es el componente visual y de persistencia. Se activa desde el skill via `run_js`.

| Accion | Descripcion |
|--------|-------------|
| `set_role` | Establece el rol activo (jugador / padre / entrenador) y lo persiste en localStorage |
| `get_role` | Devuelve el rol activo actual |
| `log_emotion` | Registra un estado emocional con fecha, contexto, intensidad 1-5 y notas |
| `get_emotions` | Devuelve registros emocionales de los ultimos N dias |
| `get_patterns` | Analiza patrones: contextos mas frecuentes, emociones dominantes, intensidad media |
| `export_log` | Exporta el registro completo en texto plano para compartir con psicologo o entrenador |

---

## Contextos emocionales

- `pre-partido`
- `post-partido`
- `entrenamiento`
- `otro`

---

## Persistencia

Toda la informacion se guarda en `localStorage` del webview:

- `fairplay_role` — rol activo
- `fairplay_emotions` — array de registros emocionales (JSON)

---

## Interfaz

Dark theme con acento naranja/ambar (`#f59e0b`) acorde a la identidad de FairPlay. Muestra estadisticas (total de registros, actividad semanal, intensidad media), lista de registros recientes con barra de intensidad visual, vista de patrones y exportacion de texto plano.

---

## Limitaciones y seguridad

- No da diagnosticos clinicos.
- En casos de angustia severa o ideas de dano sugiere hablar con un adulto de confianza o un profesional de la salud mental.
- No almacena datos fuera del dispositivo: toda la informacion queda en localStorage del webview.
