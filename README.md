# OpenCode Clone

Monorepo minimal para construir una experiencia de CLI/TUI inspirada en OpenCode. El paquete principal vive en `packages/cli` y renderiza una interfaz de terminal con OpenTUI y componentes React-like.

## Estado actual

El proyecto está en fase inicial. Actualmente incluye la base visual de la CLI, configuración TypeScript estricta y tooling de desarrollo con Bun.

## Requisitos

- Bun 1.x
- TypeScript 5.x

Node.js no es obligatorio para ejecutar el proyecto con Bun, aunque puede ser útil para herramientas externas.

## Instalación

Desde la raíz del repositorio:

```bash
bun install
```

## Desarrollo

Ejecutar la CLI en modo watch desde la raíz:

```bash
bun run dev:cli
```

O desde el paquete CLI:

```bash
cd packages/cli
bun run dev
```

## Estructura

```txt
.
├── package.json
├── tsconfig.base.json
├── packages/
│   └── cli/
│       ├── package.json
│       ├── tsconfig.json
│       └── src/
│           ├── index.tsx
│           └── components/
└── skills-lock.json
```

## Paquetes

| Paquete | Descripción |
|---|---|
| `packages/cli` | Aplicación CLI/TUI basada en `@opentui/core`, `@opentui/react` y React. |

## Decisiones técnicas

| Área | Decisión |
|---|---|
| Runtime | Bun para instalación, desarrollo y ejecución local. |
| Organización | Monorepo con workspaces para permitir futuros paquetes. |
| UI de terminal | OpenTUI con componentes JSX. |
| TypeScript | Configuración estricta compartida desde `tsconfig.base.json`. |

## Scripts

| Comando | Descripción |
|---|---|
| `bun run dev:cli` | Ejecuta la CLI en modo watch desde la raíz. |
| `bun run dev` | Ejecuta la CLI desde `packages/cli`. |

## Calidad y testing

Todavía no hay suite de tests configurada. Antes de agregar lógica crítica conviene incorporar:

- `bun:test` o Vitest para pruebas unitarias.
- Un script `typecheck` en la raíz.
- CI básico para instalación, typecheck y tests.

## Skills del proyecto

El repositorio incluye skills locales en `.agents/skills/`, registrados en `skills-lock.json`, para asistir el trabajo con:

- Bun y Bun CLI.
- TypeScript estricto.
- ESLint/Prettier.
- Tests unitarios.
- Quality gates.

Después de instalar o actualizar skills, reiniciá el agente para que los cargue.

## Convenciones de trabajo

- Usar Conventional Commits.
- No agregar atribución de IA ni `Co-Authored-By` en commits.
- Mantener los cambios chicos y revisables.
- Actualizar documentación cuando cambien comandos, dependencias o flujo de desarrollo.

## Próximos pasos recomendados

1. Agregar scripts de `typecheck` y `test`.
2. Configurar una suite mínima de tests.
3. Separar lógica de aplicación de componentes visuales cuando aparezca comportamiento real.
4. Agregar CI para validar el proyecto en cada PR.
