---
name: traductor-bizkaiera
description: Traduce textos del castellano al euskera (variante bizkaiera) para uso profesional (emails, informes, contenido web, comunicaciones de Adimedia). Usa esta skill siempre que el usuario pegue un texto en castellano y pida traducirlo al euskera, al vasco, o mencione "bizkaiera", "traduce esto al euskera", "pásame esto en euskera", "cómo se dice esto en euskera" o cualquier variación que implique convertir un texto de castellano a euskera. También se activa si pide revisar o mejorar una traducción al euskera ya existente. El input es siempre texto pegado directamente en el chat (no ficheros) y la salida es siempre el texto traducido en el propio chat, sin generar documentos.
---

# Traductor Castellano → Euskera (Bizkaiera)

Traduce textos profesionales del castellano al euskera, usando la variante **bizkaiera**, para el uso diario del usuario en su trabajo en Adimedia (emails, informes, textos web, comunicaciones internas/externas).

## Cuándo se usa

- El usuario pega un texto en castellano y pide su traducción al euskera.
- El usuario pide revisar o pulir una traducción al euskera que ya tiene.
- El contexto es mayoritariamente profesional: emails a clientes o compañeros, informes, textos de páginas web, comunicaciones internas.

## Cómo traducir

1. **Registro**: mantén un tono profesional pero natural, igual que el del texto original en castellano. Si el texto original es formal, la traducción debe serlo también; si es cercano/informal (p. ej. un email interno rápido), refleja ese mismo tono en euskera.
2. **Variante**: usa **bizkaiera** como base (rasgos morfológicos y léxicos propios de Bizkaia: p. ej. *dot* en vez de *dut*, *dabil* en vez de *dabil* estándar cuando corresponda, terminaciones verbales bizkainas, vocabulario propio). No traduzcas en euskera batúa salvo que el texto contenga terminología técnica sin equivalente claro en bizkaiera, en cuyo caso puedes usar la forma batúa de ese término puntual y seguir en bizkaiera el resto de la frase.
3. **Terminología técnica y de negocio**: términos de UX, digital, marketing, analítica, nombres propios de empresas, productos, herramientas o siglas (KPI, SEO, UX, CaixaBank Dualiza, Adimedia, etc.) se mantienen tal cual en castellano/inglés dentro del texto en euskera, salvo que exista una traducción de uso común y natural en euskera técnico.
4. **Nombres propios y marcas**: nunca se traducen (personas, empresas, productos, nombres de proyectos).
5. **Fidelidad**: traduce el sentido completo del texto, sin añadir ni quitar información. Si una frase castellana no tiene una construcción natural directa en bizkaiera, adapta la estructura para que suene natural en euskera, no traduzcas palabra por palabra.
6. **Dudas de ambigüedad**: si el texto original es ambiguo (p. ej. un "usted" que podría ser singular o plural, o un término con varias lecturas posibles), elige la interpretación más razonable según el contexto y sigue adelante; no hace falta preguntar salvo que la ambigüedad cambie completamente el sentido del mensaje.

## Formato de salida

- Devuelve **solo el texto traducido en euskera**, directamente en el chat, sin generar ficheros ni documentos.
- No añadas explicaciones largas sobre las decisiones de traducción salvo que el usuario las pida explícitamente. Si hay algún matiz relevante (p. ej. un término que se ha dejado en castellano a propósito, o una elección de registro concreta), puedes indicarlo brevemente después del texto traducido, en una línea aparte.
- Si el texto original tiene formato (saludo, despedida, firma, listas, párrafos), respeta esa misma estructura en la traducción.

## Ejemplo

**Input (castellano):**
> Hola equipo, os adjunto el informe de KPIs del mes de junio para Observatorio FP. Cualquier duda, decídmelo antes del viernes. Gracias.

**Output (bizkaiera):**
> Kaixo talde, ekaineko Observatorio FP-ren KPI txostena bialtzen deutsuet erantsita. Zeozer galdetu gura badozue, esaidazue barikuaren aurretik. Eskerrik asko.

*(Nota: nombres propios como "Observatorio FP" y el término "KPI" se mantienen sin traducir.)*
