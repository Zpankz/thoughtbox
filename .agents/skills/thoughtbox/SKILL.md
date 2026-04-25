```markdown
# thoughtbox Development Patterns

> Auto-generated skill from repository analysis

## Overview

This skill teaches you how to contribute effectively to the `thoughtbox` codebase, a TypeScript project built on Express. You'll learn the project's coding conventions, commit patterns, and the main development workflows—from feature phases and architectural transitions to documentation, testing, and repo cleanup. This guide includes step-by-step instructions and code examples to help you follow best practices and maintain consistency.

## Coding Conventions

### File Naming

- Use **camelCase** for file and directory names.
  - Example: `thoughtHandler.ts`, `toolRegistry.ts`

### Imports

- Use **relative import paths**.
  - Example:
    ```typescript
    import { getSession } from './sessions/sessionManager'
    ```

### Exports

- Use **named exports** (not default exports).
  - Example:
    ```typescript
    // sessions/sessionManager.ts
    export function getSession(id: string) { ... }
    ```

### Commit Messages

- Follow the **Conventional Commits** format.
  - Prefixes: `feat:`, `fix:`, `docs:`, `chore:`, `refactor:`
  - Example:
    ```
    feat: add progressive disclosure to gateway handler
    docs: update architecture diagram for new persistence layer
    ```

## Workflows

### Feature Development with Roadmap Phase
**Trigger:** When adding a major capability or architectural layer  
**Command:** `/new-feature-phase`

1. Create new files for the feature (e.g. `storage`, `registry`, `handler`, etc.)
2. Update or create index/registry/handler files to wire in the new feature
3. Add or update types and schemas as needed
4. Document the new feature in `README.md` or architecture docs
5. Merge via pull request with `feat:` or `refactor:` prefix

**Files Involved:**
- `src/persistence/*.ts`
- `src/discovery-registry.ts`
- `src/tool-descriptions.ts`
- `src/tool-registry.ts`
- `src/init/**`
- `src/server-factory.ts`
- `src/thought-handler.ts`
- `src/sessions/**`
- `src/gateway/**`
- `README.md`

**Example:**
```typescript
// src/persistence/newStorage.ts
export function saveData(data: Data) { ... }
```
```typescript
// src/tool-registry.ts
export { saveData } from './persistence/newStorage'
```

---

### Documentation and Architecture Update
**Trigger:** When updating docs to match codebase or explain new workflows  
**Command:** `/update-docs`

1. Edit `README.md` to add/update sections, tables, or diagrams
2. Edit or add files in `src/resources/` or `docs/` for architecture content
3. Update `CONTRIBUTING.md` if conventions or architecture change
4. Add or rename images in `public/` to match doc references
5. Commit with `docs:` prefix

**Files Involved:**
- `README.md`
- `CONTRIBUTING.md`
- `src/resources/server-architecture-content.ts`
- `src/CAPABILITIES.md`
- `public/*.png`

**Example:**
```
docs: update README with gateway architecture diagram
```

---

### Agentic Test Infrastructure Update
**Trigger:** When adding/updating agentic tests for MCP tools  
**Command:** `/add-agentic-test`

1. Create or update `scripts/agentic-test.ts`
2. Update `package.json` and `package-lock.json` to add test scripts or dependencies
3. Add or update `tsconfig` for scripts if needed
4. Commit with `feat:` or `fix:` prefix and test-related scope

**Files Involved:**
- `scripts/agentic-test.ts`
- `package.json`
- `package-lock.json`
- `scripts/tsconfig.json`

**Example:**
```typescript
// scripts/agentic-test.ts
import { testToolBehavior } from '../src/tool-registry'
testToolBehavior('gateway')
```

---

### Cleanup and Removal of Obsolete Files
**Trigger:** When cleaning up legacy, deprecated, or unused files/directories  
**Command:** `/cleanup-obsolete`

1. Identify obsolete files (reports, specs, brainstorms, old configs, unused directories)
2. Remove files and directories in a single commit or PR
3. Update `.gitignore` or related configs if necessary
4. Commit with `chore:` prefix and cleanup-related scope

**Files Involved:**
- `AGX_REPORT.md`
- `CONTAINER_USE_INSPIRED_THOUGHTBOX_IDEAS.md`
- `smithery.yaml`
- `specs/*`
- `.claude/skills/**`
- `.spec-orchestrator/**`
- `.spec-validator/**`
- `.specification-suite/**`
- `.swarm/**`
- `ideas/**`

**Example:**
```
chore: remove deprecated specs and brainstorm files
```

---

### Gateway Architecture Transition
**Trigger:** When centralizing tool access through a gateway handler  
**Command:** `/enable-gateway`

1. Add or update `src/gateway/gateway-handler.ts` and related files
2. Update `src/server-factory.ts` to remove individual tool registrations and register only the gateway
3. Update `src/tool-descriptions.ts` and `src/tool-registry.ts` to reflect gateway-only pattern
4. Update documentation to explain gateway usage and progressive disclosure
5. Remove retry/delay logic now handled by gateway
6. Commit with `feat:` or `refactor:` prefix and gateway-related scope

**Files Involved:**
- `src/gateway/gateway-handler.ts`
- `src/gateway/index.ts`
- `src/server-factory.ts`
- `src/tool-descriptions.ts`
- `src/tool-registry.ts`
- `README.md`
- `CONTRIBUTING.md`

**Example:**
```typescript
// src/server-factory.ts
import { gatewayHandler } from './gateway/gateway-handler'
// Only register gatewayHandler, remove individual tool registrations
```

---

## Testing Patterns

- Use **vitest** as the testing framework.
- Test files follow the `*.test.ts` pattern and are placed alongside or near the code under test.

**Example:**
```typescript
// src/sessions/sessionManager.test.ts
import { describe, it, expect } from 'vitest'
import { getSession } from './sessionManager'

describe('getSession', () => {
  it('returns a session by id', () => {
    expect(getSession('abc')).toBeDefined()
  })
})
```

## Commands

| Command             | Purpose                                                              |
|---------------------|----------------------------------------------------------------------|
| /new-feature-phase  | Start a new feature or architectural phase                           |
| /update-docs        | Update documentation and architecture diagrams                       |
| /add-agentic-test   | Add or update agentic test scripts and infrastructure                |
| /cleanup-obsolete   | Remove obsolete, deprecated, or unused files and directories         |
| /enable-gateway     | Transition to gateway-only architecture for tool access              |
```
