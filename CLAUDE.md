# CLAUDE.md

## Reference Sources

Before building anything new, fixing bugs, or making architectural decisions, check these sources in order:

1. **Epic Stack** — https://github.com/epicweb-dev/epic-stack
   The primary reference for best practices, patterns, and project structure.
2. **Installed skills** — check `.agents/skills/` and `docs/skills/` for relevant skill references. These contain curated, project-specific guidance that takes precedence over external docs.
3. **React Router docs** — https://reactrouter.com
   For routing, data loading, actions, and related APIs.

## Principles

- Prefer simple, platform-native solutions over clever workarounds.
- If the platform (web APIs, React Router, Node.js) provides a way to do something, use it.
- Check existing patterns in the codebase before introducing new ones.

## How to Make Changes

Every change — feature, fix, or refactor — follows this process:

1. **Research** — Check the reference sources above for established patterns before writing code.
2. **Implement** — Make the changes.
3. **Preview** — Verify the result visually in the Claude preview.
4. **Test** — Write tests following the Testing section. Fix failures by correcting the implementation, never by hacking the tests.
5. **Open draft PR** — Push the branch and open a draft PR on GitHub.
6. **CI green** — All GitHub Actions must pass. Fix any failures.
7. **Preview deployment** — Confirm the Fly.io preview deployment succeeds. Then open the deployment URL in the browser and verify the actual page works as expected. Note: the preview can take a few minutes before becoming healthy.
8. **Ready for review** — Mark the PR as ready and assign @MoSattler.

## Testing

Always add tests. Prioritize by the **Testing Trophy** (https://kentcdodds.com/blog/the-testing-trophy-and-testing-classifications):

1. **Integration tests** — the bulk of your tests. Test how units work together (e.g., rendering a route with loaders/actions, API flows).
2. **End-to-end tests** — for critical user flows (e.g., signup, checkout). Fewer but high-confidence.
3. **Unit tests** — for pure logic, utilities, and edge cases. Keep them focused.
4. **Static analysis** — TypeScript and ESLint catch the rest. 

Write more tests in the middle of the trophy (integration), fewer at the extremes.

## CLI Tools

`gh` and `fly` are installed via Homebrew. Set the PATH before using them:

```bash
export PATH="/opt/homebrew/bin:/usr/local/bin:$PATH"
```

- **GitHub CLI:** `/opt/homebrew/bin/gh` — PRs, issues, Actions, API
- **Fly.io CLI:** `/opt/homebrew/bin/fly` — deploy, logs, secrets, status
