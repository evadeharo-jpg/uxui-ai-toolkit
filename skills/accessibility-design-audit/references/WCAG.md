# Referencia rápida WCAG 2.1 (criterios relevantes para diseño)

Solo los criterios que se deciden o se pueden verificar **en el diseño**. Se excluyen los que dependen exclusivamente de implementación (parsing de HTML, ARIA, etc.) — para eso, ver la skill técnica `accessibility`.

## Nivel A

| Criterio | Qué comprobar en el diseño |
|---|---|
| 1.1.1 Contenido no textual | Imágenes/iconos tienen alt sugerido o están marcados como decorativos |
| 1.3.1 Info y relaciones | La jerarquía visual (títulos, listas, tablas) es reconocible, no solo "parece" un título |
| 1.3.2 Secuencia significativa | El orden de lectura tiene sentido si se linealiza (móvil, lector de pantalla) |
| 1.3.3 Características sensoriales | Las instrucciones no dependen solo de "el botón verde" o "arriba a la derecha" |
| 1.4.1 Uso del color | El color no es el único medio para transmitir información |
| 1.4.2 Control de audio | Si hay audio autoplay, debe poder pausarse |
| 2.1.1 / 2.1.2 Teclado | Todo lo interactivo es alcanzable y no queda "atrapado" (ej. modales) |
| 2.2.1 / 2.2.2 Tiempo | Límites de tiempo ajustables; contenido en movimiento puede pausarse |
| 2.3.1 Tres destellos | Nada parpadea más de 3 veces por segundo |
| 2.4.1 Evitar bloques | Existe manera de saltar navegación repetida (skip link, landmarks) |
| 2.4.2 Título de página | Cada pantalla tiene un título descriptivo previsto |
| 2.4.3 Orden del foco | El orden de tabulación previsto conserva el sentido |
| 2.4.4 Propósito del enlace | Los textos de link/botón son descriptivos por sí mismos |
| 2.5.1–2.5.4 Gestos y puntero | Gestos complejos tienen alternativa simple; el estado "pulsado" no dispara la acción antes de soltar |
| 3.2.1 / 3.2.2 Al enfocar/escribir | El foco o la escritura no disparan cambios de contexto inesperados |
| 3.3.1 / 3.3.2 Errores y labels | Todo campo tiene label visible; los errores están claramente descritos |

## Nivel AA

| Criterio | Qué comprobar en el diseño |
|---|---|
| 1.4.3 Contraste (mínimo) | 4.5:1 texto normal, 3:1 texto grande |
| 1.4.4 Redimensionar texto | El layout no se rompe al 200% de zoom |
| 1.4.5 Imágenes de texto | Se usa texto real, no texto incrustado en imágenes |
| 1.4.10 Reflow | El diseño funciona en 320px de ancho sin scroll horizontal |
| 1.4.11 Contraste no textual | Bordes, iconos funcionales, controles: 3:1 mínimo |
| 1.4.12 Espaciado de texto | El layout tolera line-height/letter-spacing ampliados |
| 1.4.13 Contenido en hover/focus | Tooltips y popovers son descartables y no desaparecen solos |
| 2.4.5 Múltiples vías | Hay más de una forma de llegar a una pantalla (búsqueda, menú, breadcrumbs) |
| 2.4.6 Títulos y labels | Son descriptivos, no genéricos ("Sección 1") |
| 2.4.7 Foco visible | Todo interactivo tiene un estado de foco diseñado |
| 3.2.3 / 3.2.4 Consistencia | Navegación y patrones se repiten igual en todo el producto |
| 3.3.3 Sugerencia de error | El mensaje de error sugiere cómo corregirlo, no solo que "está mal" |
| 3.3.4 Prevención de errores | Acciones importantes (borrar, pagar) son reversibles o piden confirmación |

*(Nivel AAA se documenta caso por caso como mejora opcional, no como bloqueante.)*

## Enlaces

- [WCAG 2.1 Quick Reference (oficial)](https://www.w3.org/WAI/WCAG21/quickref/)
