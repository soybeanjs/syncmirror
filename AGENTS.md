## Coding standards

- **TypeScript** — obey the `typescript-functional-style` skill for every `**/*.{ts,tsx,js,jsx}` file. Read `~/.agents/skills/typescript-functional-style/SKILL.md` before writing code.
- **Vue SFC** — obey the `vue-sfc-structure` skill for every `**/*.vue` file. Read `~/.agents/skills/vue-sfc-structure/SKILL.md` before writing code.

These rules are mandatory: read the skill instead of guessing the convention, and follow it even for small edits.

## Toolchain

- **Vite+ (`vp`) is the only toolchain entry point.** Run `vp fmt`, `vp lint`, `vp check`, `vp pack`, and `vp staged`; never call `vite`, `tsup`, `eslint`, `prettier`, or `vitest` directly — `vite-plus` ships no `vite` bin.
- `prettier` / `eslint` / `lint-staged` / `simple-git-hooks` / `tsup` / `unbuild` are no longer dependencies. Lint and format rules live in `@soybeanjs/oxc-config`, wired through the `lint` / `fmt` blocks in `vite.config.ts`.
- Library build is `vp pack` in `vite.config.ts` (`pack` block), not a separate `tsup.config.ts`.
- Commit hooks are project-owned scripts under `.vite-hooks/` plus the `staged` block in `vite.config.ts`. The generated dispatcher `.vite-hooks/_` is git-ignored; `vp config` syncs it.

## Commits

- **Conventional Commits.** Format: `<type>(<scope>): <subject>`, with the subject in the imperative mood. **Both type and scope are required** — never omit the scope; use the area the change touches (e.g. `ubean`, `proposals`, `agents`). Allowed types: `feat`, `fix`, `docs`, `style`, `refactor`, `perf`, `test`, `build`, `ci`, `chore`, `revert`.
- **Commit messages are written in English.** Subject, body, and any `BREAKING CHANGE:` footer. Never commit Chinese text.
- Keep the subject under 72 characters; explain the _why_ in the body, wrapped at 72 columns.
