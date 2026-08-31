# Laboratorio 3.1 - Agent Skill

Repositorio del laboratorio de DevOps para crear y probar un skill reutilizable
que genera mensajes de commit con el estándar Conventional Commits.

## Skill incluido

- `commit-message-writer/SKILL.md`

## Instalación

```bash
mkdir -p ~/.agents/skills/commit-message-writer
mkdir -p ~/.claude/skills/commit-message-writer
cp commit-message-writer/SKILL.md ~/.agents/skills/commit-message-writer/SKILL.md
cp commit-message-writer/SKILL.md ~/.claude/skills/commit-message-writer/SKILL.md
```

## Invocación

Directa:

```text
/commit-message-writer
```

Con lenguaje natural:

```text
Genera el mensaje de commit para mis cambios staged.
```

El skill inspecciona únicamente los cambios preparados con `git add`; no crea el
commit automáticamente.
