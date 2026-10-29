# simple-mode

Claude Code answers you understand on the first read.

Simple mode is an always-on style for Claude Code. It puts the core idea first, uses plain words, defines jargon the first time it shows up, and keeps code, paths and error messages exact. It aims for clarity, not shortness.

## Install

```sh
claude plugin marketplace add 609NFT/simple-mode && claude plugin install simple@simple-mode
```

Or inside Claude Code: `/plugin marketplace add 609NFT/simple-mode`, then `/plugin install simple@simple-mode`.

It turns on in your next session.

## Use

| You say | What happens |
| --- | --- |
| nothing | On in every session |
| `normal mode` or `/simple off` | Off for the rest of this session |
| `simple mode` or `/simple` | Back on |
| `claude plugin disable simple@simple-mode` | Off for good (`enable` brings it back) |

Ask for a diagram or visual explainer and you get one self-contained HTML page built on the same rules.

## The rules

1. Core idea first, in 1-2 sentences.
2. Plain words, short sentences.
3. Define jargon on first use.
4. One analogy at most, only if it helps.
5. Never trade accuracy for simplicity.
6. Code, commands, paths, errors and numbers stay exact.
7. Short structure: small paragraphs, bullets, numbered steps.
8. No filler.

The full text is [skills/simple/SKILL.md](skills/simple/SKILL.md).

## Example

> **What's a memory leak?**
>
> Without: "Unreleased heap allocations accumulate due to retained references, increasing the resident set until OOM."
>
> With: "A memory leak is when a program keeps taking memory and never gives it back, so it uses more and more until it slows down or crashes. It usually happens because the code still holds a reference (a pointer to the data) it no longer needs, so the memory can't be freed."

## How it works

Two files:

- [skills/simple/SKILL.md](skills/simple/SKILL.md) holds the rules and the on/off switch.
- [hooks/hooks.json](hooks/hooks.json) is a SessionStart hook that loads those rules into every session (about 600 tokens), so you never have to ask for it.

Inspired by [caveman](https://github.com/JuliusBrussee/caveman), which goes for fewer words. This goes for clearer ones.

## License

MIT
