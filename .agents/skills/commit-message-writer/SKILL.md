---
name: commit-message-writer
description: >
  Redacta mensajes de commit consistentes en formato Conventional Commits a partir del diff actual (staged o sin stagear), inspeccionando el historial reciente del repositorio para respetar el idioma, el estilo de scope y el tono ya usados en el proyecto. Usa esta skill siempre que el usuario pida ayuda para escribir, generar, revisar o mejorar un mensaje de commit, cuando diga cosas como "hazme el commit", "redacta el mensaje de commit", "qué pongo en el commit", "genera un commit message para estos cambios" o "resume estos cambios para el commit". Actívala también antes de ejecutar `git commit` si el usuario no ha aportado ya un mensaje propio.
---

# Redactor de mensajes de commit

Genera mensajes de commit en formato [Conventional Commits](https://www.conventionalcommits.org/) a partir de los cambios reales del repositorio, no de suposiciones. El mensaje debe reflejar lo que el diff hace de verdad y sonar como si lo hubiera escrito quien mantiene este proyecto.

## Proceso

1. **Mira los cambios reales.**
   - Si hay cambios en staging: `git diff --staged` y `git status`.
   - Si no hay nada staged: `git diff` sobre el working tree y avisa de que aún no está en staging.
   - Lee el diff completo, no solo los nombres de archivo. El tipo y el resumen deben basarse en qué hace el cambio, no en qué carpeta toca.

2. **Infiere las convenciones del proyecto.** Ejecuta `git log --oneline -15` (y `git log -5 --format='%B---'` si necesitas ver cuerpos completos) y detecta:
   - Idioma habitual de los mensajes (español o inglés).
   - Si usan `tipo(scope): descripción` o solo `tipo: descripción`.
   - Longitud típica del asunto y si suelen añadir cuerpo.
   - Cualquier convención propia (prefijos de ticket, firma, emojis, etc.).
   Sigue lo que ya hace el proyecto aunque no coincida exactamente con el estándar de Conventional Commits — la consistencia con el historial real pesa más que la pureza del estándar.

3. **Elige el tipo correcto** según lo que domine en el diff:
   - `feat`: añade una funcionalidad nueva visible para el usuario.
   - `fix`: corrige un comportamiento incorrecto.
   - `docs`: cambios solo en documentación.
   - `style`: formato, espacios, punto y coma — sin cambio de lógica.
   - `refactor`: reestructura código sin cambiar comportamiento externo.
   - `perf`: mejora de rendimiento.
   - `test`: añade o corrige tests.
   - `build`: cambios en el sistema de build o dependencias.
   - `ci`: cambios en configuración de integración continua.
   - `chore`: tareas de mantenimiento que no encajan en las anteriores.

   Si el diff mezcla varios tipos de cambio sin relación entre sí (p. ej. una feature nueva y una corrección aparte), dilo explícitamente y sugiere dividirlo en varios commits en lugar de forzar un solo mensaje que lo tape todo.

4. **Determina el scope** (opcional) solo si aporta claridad real: el módulo, carpeta o componente principal afectado. Si el cambio es transversal o no hay un scope claro, omítelo — no lo inventes por rellenar.

5. **Redacta el asunto:**
   - Verbo en modo imperativo o infinitivo (según lo que use el historial del proyecto), no en pasado ("añade", no "añadido" ni "añadió").
   - Máximo ~72 caracteres.
   - Sin punto final.
   - Describe el efecto del cambio, no el proceso para llegar a él.

6. **Añade cuerpo solo si el asunto no basta** para entender el porqué. El cuerpo explica motivación y contexto (el qué y el por qué), nunca el cómo línea a línea — eso ya está en el diff. Si el cambio es autoexplicativo, no fuerces un cuerpo.

7. **Marca breaking changes** si el diff rompe compatibilidad hacia atrás: añade `!` tras el tipo/scope (`feat(api)!: ...`) y un footer `BREAKING CHANGE: <explicación>`.

## Salida

Entrega el mensaje final listo para copiar, en un bloque de código, sin ningún comentario alrededor que haya que borrar. Si el mensaje lleva cuerpo, sepáralo del asunto con una línea en blanco.

No ejecutes `git commit` por tu cuenta salvo que el usuario lo pida explícitamente. Tu trabajo es proponer el mensaje; el commit lo dispara el usuario.

## Casos especiales

- **Nada en staging ni working tree modificado**: dilo y no inventes un mensaje.
- **Diff enorme con cambios no relacionados**: prioriza claridad sobre exhaustividad — resume el propósito dominante y menciona que hay más de un cambio si aplica.
- **El usuario ya dio parte del mensaje**: úsalo como punto de partida y ajústalo al formato/convenciones del proyecto en vez de sustituirlo por otro genérico.
