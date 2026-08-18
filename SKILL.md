---
name: website-copy-audit
description: Audit and, when explicitly requested, minimally fix user-facing English and Italian website copy. Use for website copy audits, bilingual EN/IT reviews, page-level language checks, or full-site final reviews covering native naturalness, semantic consistency, marketing copy, UX microcopy, and AI/translation-like phrasing while protecting business meaning, legal text, SEO, prices, claims, variables, and code.
---

# Website Copy Audit (English and Italian)

Audit user-facing English and Italian website copy without redesigning the content strategy or rewriting text that is already effective.

## Core objective

Find wording that genuinely needs attention, explain why, and recommend the smallest safe improvement. Preserve the site's business intent, information architecture, brand voice, and technical behavior.

Do not treat stylistic preference as an error. If the original and an alternative are equally natural and effective, mark the original `OK` and leave it unchanged.

## Supported modes

Choose one mode from the user's request and available project context.

### `PAGE` — light page or module audit

Use when the user mentions a page, route, component, current page, recently changed section, or asks for a quick language check.

- Limit the audit to the named page, route, component, or changed files and their directly referenced locale entries.
- Include shared copy only when it appears on the audited page, such as header, footer, cookie banner, or form validation.
- Focus on `P0` and `P1` findings. Include `P2` only when it offers a clear, meaningful improvement.
- Keep the result compact and suitable for use while site structure is still evolving.

If no exact page is named, infer the narrowest reasonable scope from the current task, open files, or recent changes. State the assumption. Ask a question only when the scope cannot be determined safely.

### `FULL` — full-site final audit

Use when the user asks for a complete, final, launch, production, whole-site, or all-pages audit.

- Inventory every discoverable public route and all shared user-facing surfaces.
- Audit English and Italian independently and as aligned locale pairs.
- Include navigation, header, footer, forms, validation, errors, success states, empty states, modals, cookie/privacy UI, accessibility labels, image alt text, emails or transactional messages stored in the project, metadata, and social-sharing copy when present.
- Produce a coverage summary so omitted or unavailable surfaces are visible.
- Deduplicate repeated strings and report the canonical translation key or source location once, then list affected surfaces.

For a full-site audit, default to reporting findings without editing files unless the user explicitly asks to apply fixes.

## Edit authorization

Determine whether the request is `AUDIT_ONLY` or `AUDIT_AND_FIX`.

- `AUDIT_ONLY`: inspect and report; do not change project files.
- `AUDIT_AND_FIX`: the user explicitly asks to fix, apply, implement, rewrite, or update the findings.

When authorized to edit:

| Classification | Default action |
| --- | --- |
| `P0` or `P1`, non-sensitive, high-confidence fix | Apply the smallest safe correction and report it. |
| `P0` or `P1`, sensitive or ambiguous | Do not edit. Recommend exact wording and request confirmation. |
| `P2` | Never auto-apply. Recommend only. |
| `OK` | Do not edit or include in the issue list. |

Never interpret a general request to "audit" or "review" as permission to modify files. Never silently edit copy.

## Protected content

Treat the following as sensitive. Preserve them exactly unless the user has supplied an authoritative replacement or explicitly approves a proposed change:

- prices, currencies, taxes, discounts, percentages, quantities, dates, deadlines, stock, delivery estimates, return periods, and warranty periods;
- legal, privacy, cookie, consent, accessibility, regulatory, contractual, warranty, returns, shipping, and compliance language;
- product specifications, service scope, eligibility, exclusions, obligations, guarantees, certifications, performance claims, sustainability claims, and comparative claims;
- SEO target phrases, metadata strategy, campaign terminology, tracking labels, and paid-search language;
- brand names, product names, trademarks, slogans, named methods, partner names, and approved terminology;
- contact details, addresses, URLs, route paths, email addresses, phone numbers, and social handles.

For protected content:

1. Report language defects and EN/IT discrepancies precisely.
2. Do not guess the intended fact or legal effect.
3. Separate a wording recommendation from the factual or legal decision it depends on.
4. Mark the finding `CONFIRM` and identify the required owner when apparent, such as legal, SEO, product, or commercial.

## Technical invariants

Do not translate, rename, remove, or alter:

- translation keys, object keys, component names, variables, function names, IDs, CSS classes, data attributes, analytics events, or test selectors;
- URLs, file paths, route slugs, query parameters, API values, enum values, or database values unless they are explicitly localized display strings;
- interpolation tokens and placeholders such as `{name}`, `{{count}}`, `%s`, `%1$s`, `${value}`, `:value`, or `[[token]]`;
- ICU MessageFormat plural/select syntax, HTML/JSX tags, Markdown structure, entities, escaping, or whitespace with functional significance;
- code examples, command-line text, user-generated content, third-party content, or vendor-provided legal text.

Keep placeholders identical across the original and recommendation unless the underlying framework requires a documented locale-specific structure. Preserve capitalization when it is technically significant.

Do not refactor the i18n architecture, consolidate keys, rename files, change routes, redesign components, or alter business logic during a language audit unless the user separately asks for that work.

## Establish project context

Before judging copy:

1. Read the repository guidance files and relevant project documentation.
2. Identify the framework, routing system, i18n library, locale codes, fallback behavior, and source of truth for translations.
3. Determine the site's audience, offer, brand voice, and existing English convention (`en-GB`, `en-US`, or another variant). Do not switch English variants without explicit instruction.
4. Treat Italian as natural contemporary Italian for Italy (`it-IT`) unless the project specifies another audience or register.
5. Identify which locale is the business source of truth. If this is not documented, compare both languages without assuming that English is primary.
6. Check whether copy is local, CMS-managed, generated, or fetched remotely. Do not claim full coverage of content that is unavailable.

## Discover user-facing copy

Search the repository systematically. Prefer fast text and file search tools and inspect references before opening many files.

Common sources include:

- locale dictionaries: JSON, YAML, TOML, PO, XLIFF, CSV, JavaScript, TypeScript, and framework-specific message files;
- HTML, templates, JSX/TSX, Vue, Svelte, Astro, Markdown/MDX, and server-rendered views;
- page metadata, manifests, structured data, Open Graph, social cards, email templates, notifications, and form schemas;
- validation libraries, toast messages, empty/loading/error states, consent tools, and accessibility attributes;
- content collections, local CMS exports, fixtures intentionally used as production copy, and configuration files containing display labels.

Exclude dependencies, generated output, caches, minified bundles, lockfiles, snapshots, test fixtures that do not ship as copy, and version-control metadata unless project guidance says otherwise.

When the site can be run safely, inspect rendered pages as well as source files. Rendered review catches concatenated fragments, truncation, context errors, wrong locale fallbacks, and strings hidden behind interactions. If the site cannot be run, continue with a source-only audit and disclose that limitation.

## Review dimensions

Evaluate every in-scope string against the following dimensions.

### 1. English native naturalness

Check:

- grammar, articles, prepositions, agreement, tense, word order, punctuation, and spelling;
- idiomatic wording, collocations, concision, rhythm, and natural information order;
- consistent English variant, terminology, capitalization, and register;
- professional tone appropriate to the audience rather than literal translation from Italian;
- fragments that work in their UI context rather than only as standalone sentences.

Do not replace clear, natural English merely to make it sound more elaborate.

### 2. Italian native naturalness

Check:

- grammar, articles, articulated prepositions, gender/number agreement, pronouns, tense, mood, and punctuation;
- idiomatic contemporary Italian and natural syntax rather than English-shaped sentence structure;
- consistent use of `tu`, `voi`, impersonal forms, or formal address;
- appropriate terminology, register, capitalization, and use of loanwords;
- concise UI language that sounds written for Italian users, not translated word by word.

Do not make Italian more bureaucratic, formal, or verbose unless the site's established voice requires it.

### 3. EN/IT semantic consistency

Compare locale pairs for:

- offer, service scope, features, audience, eligibility, and exclusions;
- numbers, prices, currencies, timing, quantities, conditions, and named entities;
- negation, obligation, permission, certainty, urgency, and strength of claims;
- CTA action and destination;
- tone, level of formality, and persuasive intent;
- missing strings, untranslated strings, fallback text, duplicated text, and mixed-language UI.

Semantic equivalence does not require literal translation. Prefer meaning, function, and tone over matching sentence structure.

### 4. Marketing copy

Check whether the copy:

- communicates a clear value proposition and concrete customer benefit;
- is credible, specific, scannable, and appropriate for its position in the page hierarchy;
- avoids unsupported superlatives, inflated promises, generic filler, clichés, and repeated claims;
- maintains the original positioning and conversion intent;
- uses headings, subheadings, proof, objections, and CTAs coherently.

Do not invent benefits, proof, testimonials, differentiators, urgency, or claims. Do not change the content strategy during a language audit; flag structural issues separately as `OUT_OF_SCOPE`.

### 5. UX microcopy

Check navigation, buttons, links, fields, placeholders, helper text, errors, confirmations, status messages, tooltips, banners, modals, and accessibility labels for:

- clarity about the action, consequence, next step, and recovery path;
- consistency between labels and the destination or behavior they trigger;
- brevity without ambiguity;
- respectful, calm, specific error language;
- consistent terminology across the whole interaction;
- accessibility and comprehension without relying only on visual context.

Do not change a label in ways that misrepresent what the interface actually does.

### 6. AI-like or translation-like phrasing

Treat this as a diagnostic signal, not proof of authorship. Flag only when wording harms clarity, credibility, or native naturalness.

Look for:

- generic openings, repetitive sentence shapes, empty intensifiers, excessive parallelism, or stacked adjectives;
- vague claims, inflated polish, unnecessary summaries, and formulaic transitions;
- literal calques, unnatural cognates, misplaced modifiers, and source-language word order;
- repeated constructions that make unrelated sections sound mechanically generated.

Do not flag text merely because it is polished, concise, or uses a common phrase.

## Classification

Assign one classification per distinct issue.

### `P0` — critical

Use only when wording can materially mislead users or create significant business, legal, financial, safety, accessibility, or conversion risk. Examples include opposite meanings between locales, an incorrect price or condition, a CTA that promises a different action, or a missing negation.

### `P1` — should fix

Use for clear grammar errors, distinctly non-native phrasing, mistranslation, material ambiguity, inconsistent terminology, unprofessional wording, missing user-facing translation, or UX copy that makes an action or recovery path unclear.

### `P2` — optional improvement

Use when the original is acceptable but a specific revision would meaningfully improve clarity, tone, scannability, or persuasion. Do not use `P2` for arbitrary synonym swaps or personal taste. Never auto-apply `P2`.

### `OK`

Use internally when copy is natural, accurate, consistent, and fit for purpose. Do not list `OK` strings individually unless the user asks for a clean-copy confirmation or detailed coverage evidence.

### `CONFIRM`

Add this action label to any finding that depends on business, legal, SEO, pricing, product, or brand authority. `CONFIRM` does not replace the severity; use forms such as `P0 · CONFIRM`.

## Over-editing guardrails

Before recommending or applying a change, verify all of the following:

1. There is a concrete defect or meaningful improvement.
2. The proposed text preserves the original factual meaning, promise, scope, tone, and conversion intent.
3. The proposal is more natural or clearer in the target language, not merely different.
4. The change does not introduce a new claim, fact, feature, benefit, urgency, or legal interpretation.
5. The same issue is handled consistently in repeated strings.
6. The recommendation fits the visible UI context and available space.

If any check fails, leave the source unchanged and report the uncertainty.

Prefer a small local correction over a full rewrite. Preserve the author's voice when it is already effective. Do not homogenize every page into generic marketing language.

## Workflow

### 1. Set scope and action policy

- Select `PAGE` or `FULL`.
- Select `AUDIT_ONLY` or `AUDIT_AND_FIX`.
- Record language variants, source-of-truth assumptions, protected content, and unavailable content.

### 2. Build a copy inventory

- Map routes and components to their English and Italian sources.
- Identify shared keys and repeated strings.
- For `FULL`, track coverage by public surface and locale.
- Note dynamic, remote, authenticated, or state-dependent content that cannot be inspected.

### 3. Review in context

- Review rendered UI when practical, then trace findings to source files or translation keys.
- Compare EN/IT pairs and audit each language independently.
- Check headings together with body copy and CTAs; check form messages as complete interaction flows.
- Do not judge isolated fragments without checking where they appear.

### 4. Triage and deduplicate

- Merge duplicate findings caused by shared keys.
- Assign severity conservatively.
- Suppress interchangeable rewrites and low-value preferences.
- Separate language defects from out-of-scope strategy, design, or functional issues.

### 5. Apply only authorized fixes

In `AUDIT_AND_FIX`, apply only high-confidence, non-sensitive `P0` and `P1` changes. Preserve syntax, formatting, placeholders, and locale-file validity. Leave `P2` and all `CONFIRM` items unchanged.

After editing:

- validate the changed file format;
- compare placeholders and markup before and after;
- run the narrowest relevant lint, type, i18n, or build check available;
- inspect the affected UI when practical;
- do not repair unrelated failures or unrelated copy.

### 6. Report

Lead with the outcome, not process narration. Be concise in `PAGE` mode and comprehensive in `FULL` mode.

## Output format

Use the following structure, adapting detail to the selected mode.

### Language audit summary

- **Mode:** `PAGE` or `FULL`
- **Action:** `AUDIT_ONLY` or `AUDIT_AND_FIX`
- **Scope:** routes, components, or files included
- **Coverage:** English, Italian, rendered/source-only, and unavailable surfaces
- **Result:** count of `P0`, `P1`, `P2`, `CONFIRM`, applied fixes, and unresolved items

### Findings

| ID | Severity | Surface | Language | Source | Original | Issue | Recommendation | Action |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| L-001 | P1 | Contact form | IT | `path:line` or `translation.key` | Original text | Specific reason | Recommended text | Apply / Applied / Suggest only / Confirm |

Rules for findings:

- Quote only enough original text to identify the issue.
- Give an exact replacement whenever a safe recommendation is possible.
- Use a precise source reference: file and line, translation key, route, or component.
- Explain the problem specifically: grammar, native usage, semantic mismatch, UX ambiguity, terminology, tone, or translation-like phrasing.
- For EN/IT mismatches, show both relevant strings and state which fact or intent needs confirmation.
- Do not list hundreds of clean strings. Summarize clean coverage instead.

### Applied changes

Include only in `AUDIT_AND_FIX` when files changed.

| Source | Before | After | Reason | Validation |
| --- | --- | --- | --- | --- |

### Needs confirmation

List protected or ambiguous decisions in priority order. Name the decision required and the safest temporary action. Do not bury `P0 · CONFIRM` items among optional suggestions.

### Coverage and limitations

Required in `FULL` mode. List audited routes/surfaces and identify any remote CMS content, authentication-only states, generated text, runtime errors, or unavailable pages that prevented complete coverage.

## Completion criteria

The audit is complete only when:

- the selected scope has been inventoried;
- both English and Italian have been reviewed independently;
- available EN/IT pairs have been checked for semantic consistency;
- marketing copy, UX microcopy, and translation-like phrasing have been considered;
- findings are deduplicated and classified conservatively;
- protected content and technical tokens remain unchanged unless explicitly approved;
- authorized edits, if any, have been validated;
- coverage gaps and confirmation items are clearly disclosed.

## Example requests

- `Audit the language of the current page. Do not change files.`
- `Run a light EN/IT audit on the Services page and apply only high-confidence P0/P1 fixes.`
- `Run a complete website language audit. Report first; do not edit.`
- `Run the final full-site EN/IT audit and apply safe P0/P1 fixes. Leave P2 as suggestions.`

