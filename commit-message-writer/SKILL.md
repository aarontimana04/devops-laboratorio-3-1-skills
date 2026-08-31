---
name: commit-message-writer
description: >
  Genera mensajes de commit con formato Conventional Commits a partir de los
  cambios staged. Usar cuando se solicite escribir o crear un mensaje de commit,
  commitear cambios, resumir el diff staged o generar el mensaje para git commit.
  Produce una línea de asunto, cuerpo opcional y footer opcional; no realiza el
  commit automáticamente.
---

# Commit Message Writer

Inspecciona exclusivamente los cambios staged mediante `git diff --cached`. No
incluyas cambios del working tree que todavía no hayan sido preparados.

Si no existen cambios staged, responde exactamente:

```text
No hay cambios staged para generar un mensaje de commit.
```

## Formato de output

Usa Conventional Commits:

```text
type(scope): descripción corta

[cuerpo opcional]

[footer opcional]
```

Entrega solamente el mensaje de commit, dentro de un bloque de código. Si hay
grupos de cambios claramente independientes, entrega una propuesta separada para
cada grupo.

## Tipos permitidos

- `feat`: nueva funcionalidad
- `fix`: corrección de un error
- `docs`: documentación
- `refactor`: cambio interno sin modificar el comportamiento
- `test`: creación o corrección de pruebas
- `chore`: mantenimiento, configuración o herramientas

## Reglas

1. Usa un scope breve cuando pueda inferirse con claridad.
2. Escribe la descripción en inglés y modo imperativo, por ejemplo `add`, no
   `added`.
3. Limita la primera línea a 72 caracteres.
4. Resume la intención del cambio, no una lista mecánica de archivos.
5. Evita frases vagas como `update stuff` o `fix things`.
6. Usa cuerpo solo cuando ayude a explicar el motivo o una decisión relevante.
7. Usa footer para referencias o cambios incompatibles, incluido
   `BREAKING CHANGE:` cuando corresponda.
8. No ejecutes `git commit` ni modifiques archivos.
9. Genera el resultado directamente, sin preguntas innecesarias.

## Ejemplos

Correcto:

```text
feat(auth): add JWT token refresh endpoint
```

Correcto con cuerpo:

```text
fix(api): handle expired session tokens

Return an authentication error instead of retrying invalid sessions.
```

Incorrecto:

```text
Updated the auth stuff
feat: added new feature for authentication
```

El primer ejemplo es vago. El segundo está en pasado y omite un scope que puede
inferirse.
