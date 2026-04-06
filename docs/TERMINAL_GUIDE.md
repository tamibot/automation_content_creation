# Guía de Terminales Múltiples — Antigravity

Antigravity permite la ejecución de misiones en paralelo a través de múltiples terminales (sesiones). Esta es la guía para maximizar la velocidad de producción.

---

## ⚡ Ejecución en Paralelo (Subagentes)

Cuando solicitas una tarea compleja al **Orquestador**, este puede abrir múltiples terminales invisibles para delegar misiones:
- **Terminal 1**: `trend-explorer` scrapeando TikTok.
- **Terminal 2**: `visual-expert` analizando un video con Gemini.
- **Terminal 3**: `brand-guardian` revisando borradores antiguos.

### Cómo solicitarlo explícitamente:
Puedes pedirle a Claude:
> *"Usa terminales paralelas para analizar estos 3 videos al mismo tiempo."*

---

## 🖥️ Gestión Manual de Sesiones

Si deseas abrir una nueva sesión de terminal manualmente para otro propósito:

1.  **Scope**: Define siempre qué carpeta o feature va a manejar cada terminal.
2.  **Conflictos**: Evita que dos terminales editen el mismo archivo simultáneamente.
3.  **Logs**: Cada sesión guarda su propio historial en `.claude/sessions/`.

### Reglas para Agentes Paralelos:
- **No tocar el mismo archivo**: Si el `remixer` está escribiendo en `remix_01.md`, el `guardian` no debe leerlo hasta que el `remixer` haya terminado y guardado.
- **Uso de `/brain`**: La carpeta de memoria compartida es el único punto de contacto entre terminales paralelas.

---

## 🔍 Monitoreo
Todas las salidas de las terminales paralelas se consolidan en el flujo de chat principal de Antigravity, pero cada una mantiene su propio "contexto de trabajo".
