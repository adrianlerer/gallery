# LoveLink Vincular — Google AI Edge Gallery Skill

Coach vincular práctico para relaciones de pareja. Orientado a la acción, no a la terapia. Respuestas en español con tratamiento de usted.

## Target

- **Modelo**: Gemma 4 E2B (128K contexto, ~50 tok/s)
- **Idioma**: Español (adaptación cultural por país)
- **App**: [LoveLink](https://lovelink.app) — PWA de coaching vincular

## Módulos internos

El asistente detecta automáticamente el contexto y responde según el módulo correspondiente. No menciona los módulos al usuario.

| Módulo | Cuándo activa | Qué da |
|---|---|---|
| BÚSQUEDA | Inicio de relación, acercarse a alguien | Señales de interés, formas de iniciar, cómo proponer salida |
| DESVINCULACIÓN | Ruptura o separación | Protocolo contacto cero, primeros 30 días, rutinas de reconstrucción |
| RENEGOCIACIÓN | Problemas en relación actual | Frases de apertura, técnica mensaje-yo, qué evitar |
| AMBIVALENCIA | No sabe si quedarse o irse | 3 preguntas de clarificación, señales objetivas en ambas direcciones |

## Acciones del diario (index.html)

El script en `scripts/index.html` gestiona un diario de estado de ánimo con persistencia en `localStorage`. El asistente llama `run_js` con el script y un JSON de acción.

### `log_journal`
```json
{
  "action": "log_journal",
  "mood": 4,
  "text": "Tuve una conversación difícil pero productiva",
  "tags": ["conversación-difícil", "avance"]
}
```
`mood`: 1 (muy mal) a 5 (muy bien). Tags disponibles: `ansiedad`, `esperanza`, `duelo`, `avance`, `recaída`, `conversación-difícil`, `descubrimiento`, `soledad`, `gratitud`.

### `get_journal`
```json
{"action": "get_journal", "days": 30}
```
Retorna entradas del período y el promedio de ánimo.

### `get_patterns`
```json
{"action": "get_patterns"}
```
Analiza frecuencia de etiquetas, ánimo por día de la semana y tendencia (últimos 7 días vs. período anterior). Muestra visualización en el webview.

### `export_journal`
```json
{"action": "export_journal"}
```
Genera texto plano listo para compartir con un profesional de salud. También muestra el texto en el webview.

## UI

- Fondo oscuro (`#0f0a0f`) con acentos rosa/fucsia (`#f472b6`) y violeta (`#c084fc`)
- Estadísticas rápidas: total de entradas, entradas de la semana, promedio de ánimo
- Tarjetas con fecha, emoji de ánimo, texto y etiquetas
- Vista de patrones: barra de ánimo por día de la semana, frecuencia de etiquetas

## Reglas de respuesta

1. Siempre dar la respuesta, no preguntar si la respuesta no cambia.
2. Frases para decirle a alguien: entre comillas, en primera persona.
3. No confirmar ni refutar etiquetas diagnósticas sobre terceros.
4. No asumir orientación, género ni formato relacional.
5. Nunca usar em dash.
6. Crisis: derivar a línea de ayuda local inmediatamente.

## Crisis: recursos por país

| País | Crisis general | Violencia de género |
|---|---|---|
| Argentina | Línea 135 | Línea 137 |
| Colombia | Línea 106 | Línea 155 |
| Chile | 600 360 7777 | 1455 |
| México | SAPTEL 55 5259-8121 | Línea de la Vida 800 911 2000 |

## Estructura de archivos

```
lovelink-vincular/
├── SKILL.md          # Instrucciones del sistema para el modelo
├── README.md         # Este archivo
└── scripts/
    └── index.html    # Diario vincular (webview, localStorage)
```
