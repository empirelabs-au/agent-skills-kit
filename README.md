# Open Agent Skills Kit

> **Status: WORK IN PROGRESS.** Public launch during Hacktoberfest 2026 (October). This repository is intentionally small, open, and built to teach one thing: how to write a `skills.md` file that agents can actually use.

**Skills are how agents learn new capabilities.** A well-written `skills.md` turns a plain text file into a repeatable, reliable workflow: the agent reads it, recognizes the trigger, follows the numbered steps, and avoids the documented pitfalls.

This kit contains everything you need to write your first open-source skill:

```
agent-skills-kit/
├── guide/
│   └── writing-skills.md      # The how-to: structure, triggers, pitfalls, checklist
├── examples/
│   └── password-strength-checker/
│       └── SKILL.md           # A fully worked example, ready to read and adapt
├── template/
│   └── SKILL.md               # A blank commented template
└── LICENSE                    # MIT
```

## Quick start

1. Read the guide: `guide/writing-skills.md`.
2. Open the worked example: `examples/password-strength-checker/SKILL.md`.
3. Copy the template to your own repo, fill it in, and publish.

## Why skills.md

- **Discoverable:** the description is written to be read by an agent deciding whether to load the skill.
- **Deterministic:** numbered steps turn fuzzy instructions into a checkable procedure.
- **Self-documenting:** pitfalls and verification steps are part of the file, so the skill teaches while it runs.
- **Open:** a skills.md is just a file. No platform lock-in, no runtime required to share it.

## Ecosystem

Skills sit naturally alongside the open agent standards:

- **ACI** (Agent-Commerce Interface): machine-readable contracts describing organizations to agents.
- **AIP** (Agent Interaction Protocol): agent-to-agent negotiation, execution, settlement, and evidence.
- **AJSON** (Agent JSON): a superset of JSON purpose-built for autonomous agent communication.

Skills, contracts, and protocols compose: a skill tells the agent *how to act*, ACI/AIP/AJSON tell it *what is being agreed and proven*.

## Contributing

The kit is a Hacktoberfest 2026 project. Good places to start:

- Improve the guide with a section we missed.
- Add a second worked example (see existing issues for suggestions).
- Fix typos, clarify wording, expand the checklist.

Please read the guide first so the kit stays consistent: one clear voice, no fluff, no em dashes.

## License

MIT. See `LICENSE`.
