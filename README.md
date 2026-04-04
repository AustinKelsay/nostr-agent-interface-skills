# Nostr Agent Interface Skills

Public agent skills for [Nostr Agent Interface](https://github.com/AustinKelsay/nostr-agent-interface).

This repo is a dedicated skills package for the `skills` ecosystem. It intentionally contains only public skill material, trust docs, and validation workflows, rather than the full product source tree.

## Available Skills

- `nostr-agent-interface-cli`
  Teaches agents to discover and invoke `nostr-agent-interface cli` safely, prefer machine-readable output, keep secrets off argv, and ask for extra confirmation before destructive or account-shaping writes.

## Install

GitHub shorthand:

```bash
npx skills add AustinKelsay/nostr-agent-interface-skills --skill nostr-agent-interface-cli
```

Full GitHub URL:

```bash
npx skills add https://github.com/AustinKelsay/nostr-agent-interface-skills --skill nostr-agent-interface-cli
```

List the skills in this package without installing:

```bash
npx skills add AustinKelsay/nostr-agent-interface-skills --list
```

## Prerequisite

The skill assumes one of these execution environments is available:

1. A local installation of `nostr-agent-interface`
2. A checked-out copy of the product repo with `build/app/index.js` present

## Example

Example user request:

```text
Use the Nostr Agent Interface CLI to inspect the profile tool and fetch this user's profile.
```

Expected skill behavior:

1. Discover the current tool contract with `nostr-agent-interface cli list-tools --json`
2. Inspect `getProfile --help` if needed
3. Invoke the tool with `--json` when structured output is useful
4. Keep any sensitive inputs off argv

## Security

1. This repo ships markdown-only skill content. No executable helpers are bundled in the skill package.
2. The skill explicitly prefers stdin for `privateKey` and `authPrivateKey` inputs.
3. The skill distinguishes routine writes from destructive or account-shaping writes and requires extra confirmation for the latter.
4. Review the installed skill before use and pin to known revisions if you need stricter change control.

See [SECURITY.md](SECURITY.md) for disclosure guidance.

## Repository Layout

```text
skills/
  nostr-agent-interface-cli/
    SKILL.md
    agents/openai.yaml
    references/
evals/
.github/
```

## Validation

CI validates the portable skill format and public installability using:

1. `npx skills-ref validate skills/nostr-agent-interface-cli`
2. `npx skills add . --list`
3. A check that no example passes private keys through CLI flags

The evaluation fixtures used to review trigger quality and behavior live in [evals/trigger-cases.md](evals/trigger-cases.md) and [evals/behavior-cases.md](evals/behavior-cases.md).
