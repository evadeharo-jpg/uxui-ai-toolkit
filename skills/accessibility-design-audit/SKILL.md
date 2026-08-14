---
name: accessibility-design-audit
description: Auditar y mejorar la accesibilidad de un diseño en Figma desde una perspectiva UX/UI, siguiendo WCAG 2.1, sin entrar en implementación técnica (HTML/ARIA/código). Usar cuando se pida "auditoría de accesibilidad de diseño", "revisar contraste", "accesibilidad en Figma" o "checklist de accesibilidad para diseño".
---

# Auditoría de Accesibilidad para Diseño (Figma)

Checklist y criterios para revisar la accesibilidad de un diseño **antes** de que llegue a desarrollo. Basado en WCAG 2.1, pero traducido a decisiones de diseño: color, tipografía, layout, contenido y anotaciones.

## Los 4 principios (POUR), en clave de diseño

| Principio | En diseño significa... |
|---|---|
| **Perceptible** | La info no depende de un solo sentido (color, forma, sonido) |
| **Operable** | Todo elemento interactivo es alcanzable y usable (tamaño, foco, orden) |
| **Comprensible** | Jerarquía clara, lenguaje simple, errores explicados |
| **Robusto** | El diseño se puede traducir a una estructura semántica coherente |

## Niveles: qué exigir en la auditoría

- **A**: innegociable, bloquea entrega
- **AA**: el estándar a cumplir siempre (referencia legal en la mayoría de proyectos)
- **AAA**: deseable, se documenta como mejora si no se cubre

---

## 1. Color y contraste

**Qué revisar:**
- Texto normal (<18px o <14px bold) → contraste mínimo **4.5:1**
- Texto grande (≥18px o ≥14px bold) → mínimo **3:1**
- Iconos y componentes UI (bordes de inputs, iconos funcionales) → mínimo **3:1**
- Estados de foco → deben tener contraste suficiente frente al fondo

**Herramientas en Figma:**
- Plugin *Stark* o *Contrast* — chequeo directo sobre los estilos
- Plugin *A11y – Color Contrast Checker*

**No depender solo del color:**
- Errores, éxito, warnings → deben llevar también icono y/o texto, no solo un cambio de color de borde/fondo
- Gráficas y datos → usar patrones/etiquetas además de color

## 2. Tipografía y legibilidad

- Tamaño mínimo recomendado: 16px para texto de cuerpo
- Interlineado (line-height) generoso: ~1.5 para párrafos
- Evitar justificar texto (dificulta lectura a personas con dislexia)
- Longitud de línea: no superar ~80 caracteres
- No usar solo mayúsculas para bloques largos de texto

## 3. Áreas táctiles y espaciado (Operable)

- Tamaño mínimo de zona interactiva: **44x44px** (táctil) / 24x24px (puntero, con espaciado alrededor)
- Espaciado suficiente entre elementos clicables para evitar toques accidentales
- Evitar acciones que dependan solo de gestos complejos (arrastrar, pellizcar) sin alternativa simple

## 4. Estados de foco y orden de navegación

- Todo componente interactivo (botón, link, input, tab) necesita un **estado de foco visible** diseñado explícitamente — no asumir que el navegador lo pondrá bien
- Definir y anotar el **orden lógico de tabulación** en pantallas complejas (formularios, dashboards): normalmente de arriba a abajo, izquierda a derecha
- Modales y overlays: anotar que el foco debe quedar atrapado dentro mientras estén abiertos, y volver al elemento que los abrió al cerrarse

## 5. Contenido y jerarquía (Comprensible)

- Cada pantalla necesita **un único H1** conceptual (aunque en el diseño no se llame así, debe haber un título principal claro)
- Jerarquía visual de títulos coherente y consistente entre pantallas (no saltar niveles)
- Textos de enlaces y botones descriptivos: evitar "Click aquí", "Ver más" sin contexto — usar "Ver detalles del pedido"
- Idioma del contenido claro (si hay mezcla de idiomas en una misma pantalla, anotarlo)

## 6. Formularios

- Todo campo necesita una **label visible** (evitar depender solo de placeholder, que desaparece al escribir)
- Instrucciones y requisitos (ej. formato de contraseña) visibles **antes** de que el usuario cometa el error, no solo después
- Mensajes de error: claros, específicos, y diseñados para aparecer junto al campo (no solo arriba del formulario)
- Diseñar el estado de "resumen de errores" si el formulario es largo

## 7. Imágenes y contenido no textual

- Cada imagen debe llevar una nota de diseño indicando si es **decorativa** (no necesita alt) o **informativa** (necesita alt descriptivo) — y sugerir el texto alternativo cuando sea relevante (gráficas, infografías)
- Iconos sin texto acompañante → deben llevar un nombre accesible sugerido en las anotaciones (ej. "icono de menú → alt: Abrir menú")

## 8. Movimiento y animación

- Cualquier animación relevante (carrousels, transiciones automáticas, parallax) debe tener una alternativa o pausa para usuarios sensibles al movimiento
- Evitar parpadeos o destellos rápidos (riesgo de fotosensibilidad)

---

## Checklist de auditoría (para copiar en Figma / FigJam)

- [ ] Contraste de texto y componentes UI verificado (AA mínimo)
- [ ] Estados de error no dependen solo del color
- [ ] Tamaño de fuente y line-height legibles
- [ ] Áreas táctiles ≥ 44x44px con espaciado adecuado
- [ ] Estados de foco diseñados para todos los interactivos
- [ ] Orden de tabulación anotado en pantallas complejas
- [ ] Jerarquía de títulos consistente
- [ ] Textos de links/botones descriptivos
- [ ] Labels visibles en todos los campos de formulario
- [ ] Mensajes de error diseñados y específicos
- [ ] Imágenes clasificadas (decorativa/informativa) con alt sugerido
- [ ] Animaciones con alternativa a movimiento reducido

## Cómo entregar la auditoría

Para cada hallazgo, documentar:
1. **Pantalla / componente** afectado
2. **Criterio WCAG** relacionado (ej. 1.4.3 Contraste)
3. **Severidad**: crítico / serio / moderado
4. **Propuesta de solución** (a nivel de diseño, no de código)

### Severidad — misma clasificación que developers

**Crítico**: labels ausentes, contraste insuficiente, sin estado de foco, trampas de navegación
**Serio**: jerarquía de títulos rota, links no descriptivos, sin alternativa a animación
**Moderado**: iconos sin nombre accesible sugerido, navegación inconsistente entre pantallas

## Referencias

- [WCAG 2.1 Quick Reference](https://www.w3.org/WAI/WCAG21/quickref/)
- [references/WCAG.md](./references/WCAG.md) tabla de criterios WCAG 2.1 (A y AA) traducidos a qué comprobar en el diseño
- Plugins de Figma: Stark, A11y Color Contrast Checker, Focus Order