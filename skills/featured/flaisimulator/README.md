# FLAIsimulator — Skill para Google AI Edge Gallery

Simulador de conversaciones de capacitacion con avatares de IA. Powered by Gemma 4 E2B.

## Personajes disponibles

| Personaje | Rol | Vulnerabilidad |
|---|---|---|
| Rodrigo | CFO Esceptico | Cede ante ROI < 12 meses con benchmark |
| Catalina | Compliance (tentacion) | Se detiene ante Ley 27.401 |
| Marcelo | Consultor Estrategico | Valida si el CEO tiene el diagnostico |
| Elena | Directora Exigente | Baja la guardia ante historial de ejecucion |
| Valeria | HR Exigente | Avanza con ejemplo STAR completo |

## Instalar

1. Abrir Google AI Edge Gallery
2. Cargar modelo: Gemma 4 E2B
3. Ir a Skills > Cargar desde URL:
   `https://adrianlerer.github.io/gallery/skills/featured/flaisimulator`

## Stack

- Frontend: HTML/CSS/JS vanilla
- Modelo: Gemma 4 E2B-it (litert-community/gemma-4-E2B-it-litert-lm)
- Persistencia: localStorage
- Backend: ninguno (100% on-device)
