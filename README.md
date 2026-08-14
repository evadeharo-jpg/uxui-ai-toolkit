# UX/UI AI Toolkit

Toolkit de configuración, instrucciones y skills reutilizables para trabajar con agentes de IA en procesos de diseño UX-UI.

El objetivo es mantener una forma de trabajo consistente entre diferentes agentes sin duplicar instrucciones ni vincular la configuración a proyectos concretos.

## Structure

```text
uxui-ai-toolkit/
├── AGENTS.md
├── CLAUDE.md
├── README.md
└── skills/
    └── <skill-name>/
        └── SKILL.md
```

### `AGENTS.md`

Fuente principal de instrucciones globales.

Define cómo debe trabajar un agente dentro del entorno: criterios de colaboración, rigor, accesibilidad, diseño, desarrollo, gestión de archivos, confidencialidad y formato de respuesta.

Las reglas específicas de un proyecto no deben añadirse aquí.

### `CLAUDE.md`

Adaptador para Claude Code.

Importa las instrucciones globales desde `AGENTS.md`:

```md
@AGENTS.md
```

Esto permite mantener `AGENTS.md` como única fuente de verdad.

### `skills/`

Contiene procedimientos especializados y reutilizables.

Cada skill debe resolver un tipo de tarea concreto y mantenerse independiente de proyectos específicos.

Ejemplo:

```text
skills/
└── accessibility-design-audit/
    └── SKILL.md
```

## Adding a skill

Antes de añadir una nueva skill, comprobar que:

1. Resuelve un proceso suficientemente concreto.
2. Puede reutilizarse en diferentes proyectos.
3. No contiene información específica o confidencial de un proyecto.
4. No duplica comportamiento que ya pertenece a `AGENTS.md`.
5. No duplica otra skill existente.

Usar nombres descriptivos en `kebab-case`:

```text
skills/
├── accessibility-design-audit/
├── design-system-audit/
├── divergent-thinking/
└── usability-review/
```