# OpenCode Clone

## Descripción

Repositorio monorepo minimal que replica la estructura y experiencia de desarrollo de OpenCode. Contiene un paquete CLI en `packages/cli` que usa OpenTUI para renderizar una interfaz TUI basada en React-like components.

Objetivos del README:

- Proveer un punto único de entrada técnico y operativo para desarrolladores senior.
- Documentar decisiones de arquitectura, comandos de desarrollo y flujo de trabajo para commits/branches.

## Estructura del repositorio

- `package.json` — workspace con `packages/*`.
- `packages/cli/` — paquete principal de la CLI:
  - `src/index.tsx` — entrada de la aplicación CLI usando `@opentui/core` y `@opentui/react`.
  - `package.json` — scripts y dependencias específicas.
  - `tsconfig.json` — configuración de TypeScript orientada a bundler y JSX con `@opentui/react`.

## Decisiones técnicas clave

- Monorepo ligero: permite agregar paquetes posteriormente (p. ej. `web`, `api`, `packages/ui`).
- Runtime y gestor de paquetes: se usa `bun` para dev/run por su velocidad y experiencia integrada.
- TypeScript: `target` y `lib` en ESNext para aprovechar características modernas; `noEmit` y flujo orientado a bundlers.

## Requisitos

- Bun v1.x (o la versión que uses en tu entorno).
- Node.js no es estrictamente necesario para desarrollo local con `bun`, pero tenerlo instalado facilita herramientas externas.

## Configuración y desarrollo local

1. Instala dependencias (desde la raíz del repo):

```bash
bun install
```

2. Ejecutar la CLI en modo desarrollo:

```bash
cd packages/cli
bun run dev
```

El script `dev` ejecuta `bun run --watch src/index.tsx` y arranca el renderer CLI.

## Editor y formateo

Si al formatear Prettier está añadiendo comas finales y quieres evitarlas, aplica cualquiera de estas opciones en el workspace:

- Añadir o actualizar un fichero `.prettierrc` en la raíz del repo con:

```json
{
  "trailingComma": "none"
}
```

- O forzar la opción desde la configuración de VSCode (workspace): crea/edita `.vscode/settings.json` con:

```json
{
  "prettier.trailingComma": "none",
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "editor.formatOnSave": true
}
```

Después de aplicar el cambio, guarda y vuelve a formatear los archivos afectados para eliminar comas finales sobrantes.

## Tests

Actualmente no hay suite de tests configurada. Recomendación inicial para producción:

- Añadir `vitest` o `bun:test` para pruebas unitarias.
- Añadir pruebas E2E mínimas si se expone lógica crítica del CLI.

## Flujo de branching y commits

- Ramas: usa ramas con prefijo `feature/`, `fix/`, `chore/`.
- Antes de crear un commit final, actualiza el `README.md` y `tech-stack.md` si modificas dependencias.
- Usa Conventional Commits para mensajes de commit. Ejemplos:
  - `feat(cli): add ascii welcome screen`
  - `fix(cli): prevent crash on missing renderer`

Commit y push (ejemplo):

```bash
# crea rama
git checkout -b feature/mi-cambio
# stage + commit
git add .
git commit -m "feat(cli): descripción corta y clara"
git push origin feature/mi-cambio
```

Cuando me indiques, prepararé el commit final siguiendo Conventional Commits y haré push a una rama nueva para que tú la merges a `main`.

## Contribución y revisión

- Sigue el patrón PR -> review -> squash/merge.
- Incluye descripción técnica en el PR, pasos para reproducir y cualquier consideración de compatibilidad.

## Próximos pasos recomendados

- Añadir `tech-stack.md` con versiones exactas y racionales de dependencias.
- Añadir CI básico (GitHub Actions) para instalar dependencias y ejecutar linters/tests.
- Añadir una pequeña suite de tests para `packages/cli`.

## Contacto

Para cualquier duda sobre decisiones de arquitectura o flujos, abre un issue o mencióname en el PR.

---

_Este README fue generado por un asistente para acelerar onboarding y cumplir con prácticas senior de mantenimiento y entrega._
