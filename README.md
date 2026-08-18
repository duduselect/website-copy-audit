# Website Copy Audit (EN/IT)

A Codex Skill for auditing user-facing English and Italian website copy. It finds meaningful language, translation, consistency, marketing, and UX-copy issues while protecting business meaning and technical content.

## What it covers

- English native naturalness and Italian (Italy) naturalness
- EN/IT semantic consistency, terminology, and missing translations
- Marketing copy, CTAs, forms, errors, accessibility labels, and other UX microcopy
- AI-like or translation-like phrasing only when it harms clarity or credibility
- Safe separation of audit-only findings from explicitly authorized fixes

The Skill does not redesign a content strategy, invent claims, change legal or SEO text without confirmation, or alter code tokens and placeholders.

## Install

Clone this repository, then place the Skill folder in your Codex skills directory:

~~~sh
git clone https://github.com/duduselect/website-copy-audit.git
mkdir -p ~/.codex/skills
cp -R website-copy-audit ~/.codex/skills/
~~~

## Use

Example prompts:

- “Use $website-copy-audit to audit this English and Italian website copy. Do not change files.”
- “Run a PAGE audit on the Services page and apply only high-confidence P0/P1 fixes.”
- “Run a FULL-site EN/IT audit and report coverage gaps before editing.”

The Skill definition is in [SKILL.md](SKILL.md), and its Codex display configuration is in [agents/openai.yaml](agents/openai.yaml).

## License

MIT. See [LICENSE](LICENSE).

