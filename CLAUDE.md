## HARD RULE: the store is always Willys Sköndal

- The store is always **Willys Sköndal**, Erik's pickup store (click-and-collect, "Hämta").
- Never use store **2110 / Willys Kungsbacka Hede**, not even as a default or fallback.
- If the Sköndal store id isn't configured yet, stop and read it from the account's `homeStoreId` (willys-agent `getCustomer()`, logged in). Don't fall back to a default.

# willys-cli

TypeScript library + CLI for the Willys.se grocery store API.

## Stack

- TypeScript, Node.js (ESM)
- No frameworks, no external HTTP libraries — uses native `fetch`
- `dotenv` for credential loading

## Project Structure

- `src/willys-api.ts` — HTTP client with cookie/CSRF session management. All API methods live here.
- `src/crypto.ts` — AES-128-CBC credential encryption (replicates Willys client-side encryption)
- `src/types.ts` — TypeScript interfaces for all API responses
- `src/cli.ts` — CLI entrypoint with arg parsing and output formatting
- `src/skill.ts` — Embedded Claude Code SKILL.md content
- `src/index.ts` — Library exports
- `src/test.ts` — Integration test (hits live API, requires credentials)

## Build & Test

```
npm run build     # tsc → dist/
npm test          # runs src/test.ts against live API
npm start         # runs CLI via tsx (dev mode)
```

## Credentials

Tests and CLI require `WILLYS_USERNAME` and `WILLYS_PASSWORD` in `.env` (quoted values are stripped automatically).
