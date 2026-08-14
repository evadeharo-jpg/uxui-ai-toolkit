---
name: conversation-trace
description: Registra en tiempo real todos los recursos usados durante una conversación (skills invocadas, herramientas, búsquedas y URLs consultadas, archivos leídos/creados/editados) y los vuelca en un archivo Markdown. Se activa cuando el usuario escribe "Inicio sesión" (empieza el registro) y se cierra cuando escribe "Cierro sesión" (finaliza y guarda el archivo). Úsala también con variantes sin tilde ("Inicio sesion" / "Cierro sesion").
---

# Conversation Trace

Lleva un registro cronológico de los recursos que Claude consulta o utiliza durante un tramo de la conversación delimitado por dos frases del usuario, y lo entrega como un archivo Markdown.

## Disparadores

- **Inicio de registro:** el usuario escribe `Inicio sesión` (o `Inicio sesion`, sin tilde). A partir de ese mensaje, empieza a trackear.
- **Fin de registro:** el usuario escribe `Cierro sesión` (o `Cierro sesion`). Cierra el trackeo, completa el archivo y confirma la ruta al usuario.
- Si el usuario escribe `Cierro sesión` sin haber abierto una sesión antes, avísale de que no hay ningún registro activo y no generes archivo.
- Si el usuario escribe `Inicio sesión` teniendo ya una sesión abierta, avísale y pregunta si quiere cerrar la anterior o continuar con la misma.

## Al recibir "Inicio sesión"

1. Averigua la fecha/hora actual (por ejemplo con `date "+%Y-%m-%d %H:%M:%S"` vía Bash) para usarla como timestamp de inicio.
2. Crea el archivo `~/conversation-traces/conversation-trace-YYYY-MM-DD-HHMMSS.md` (crea la carpeta `~/conversation-traces/` si no existe). Es una ruta fija en el home del usuario, independiente del directorio de trabajo desde el que se invoque la skill, para no mezclar trazas con el código de los proyectos. Usa este esqueleto inicial:

   ```markdown
   # Registro de conversación

   **Inicio:** <timestamp>
   **Fin:** _(sesión en curso)_

   ## Skills utilizadas

   ## Herramientas utilizadas

   ## Búsquedas y URLs consultadas

   ## Archivos consultados / creados / editados

   ## Resumen
   ```

3. Confirma brevemente al usuario que el registro ha empezado y en qué ruta se irá guardando.
4. Guarda internamente la ruta del archivo activo: la necesitarás en cada paso siguiente y al cerrar la sesión.

## Durante la sesión (mientras el registro esté activo)

Cada vez que uses un recurso rastreable, añade una línea a la sección correspondiente del archivo activo (usa Edit para insertar la línea; no reescribas todo el archivo). No esperes a "Cierro sesión" para volcarlo: así no se pierde nada si la conversación se resume o se comprime.

Recursos a registrar, con una línea breve por evento (qué se usó + para qué, en un renglón):

- **Skill invocada** → `- [HH:MM] <nombre-skill>: <motivo/tarea>`
- **Herramienta usada** (Bash, Read, Write, Edit, Agent/subagente, MCP, etc.) → `- [HH:MM] <herramienta>: <qué se hizo, en pocas palabras>`
- **Búsqueda web o URL consultada** (WebSearch, WebFetch, navegación con Claude in Chrome, enlaces de Figma, etc.) → `- [HH:MM] <URL o consulta>: <por qué se consultó>`
- **Archivo tocado** (leído, creado o editado) → `- [HH:MM] <ruta relativa>: <leído|creado|editado>`

No registres el propio archivo de trace como recurso. Sé conciso: una línea por evento, sin explicaciones largas.

## Al recibir "Cierro sesión"

1. Obtén el timestamp de cierre igual que al inicio.
2. Actualiza el campo `**Fin:**` del archivo con ese timestamp.
3. Rellena la sección `## Resumen` con 3-5 frases en prosa que expliquen qué se hizo en la sesión (objetivo, principales acciones, resultado), basándote en las entradas registradas.
4. Si alguna sección quedó vacía, dile "Ninguno" en vez de dejarla en blanco.
5. Informa al usuario de que la sesión se ha cerrado y comparte el archivo Markdown generado.
6. Olvida la ruta activa: la próxima "Inicio sesión" debe crear un archivo nuevo.
