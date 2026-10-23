# PhotoCloud: Android Photo Frame — AGENTS.md

## What this is

Just sit back and watch your photos with your family; convert your old Android tablet to a digital photo frame; browse your cloud photos, hassle-free.
The only digital frame application which supports your own OwnCloud/NextCloud servers, with self-signed https certificates.

This repo is the app's public face only — the home page, FAQ, privacy policy and the issue
tracker; the app's source lives elsewhere.

## Promises

- **Your photos stay yours.** PhotoCloud only reads photos; it never changes, uploads or deletes them, and self-hosted sources are first-class.
- **Does one thing, simply.** It is a slideshow and photo browser, not an editor or a gallery replacement.

## Design docs

| File | Owns | Loaded |
|---|---|---|
| `README.md` | the pitch, where to file bugs and ask questions | — |
| `AGENTS.md` (this) | promises, the site map, conventions, commands | every turn |

Every fact lives in exactly one of these; the others link to it.

## Module map

- `docs/` — the GitHub Pages site at www.android-photo-frame.eu (`CNAME`), Jekyll theme `leap-day` (`_config.yml`).
- `docs/index.md` — home page: sources, features, pricing, permissions, supported devices.
- `docs/faq.md` — the FAQ, one `##` heading per question.
- `docs/privacy_policy.md` — the privacy policy, linked from Google Play.
- `docs/images/` — screenshots and the Google Play badge.
- `.github/ISSUE_TEMPLATE.md` — the text prefilled into every new GitHub issue.

## Conventions

- **The site describes the current Google Play build.** The home page's sources, features, pricing and permissions match the Play listing and the latest manifest.
- **Older behaviour is named by version**, e.g. "PhotoCloud 1.15.8 and older", never "previously".
- **A dropped feature leaves a FAQ answer saying why**, e.g. "Streams which are no longer supported".
- **Links between pages use the built name** (`faq.html`, `privacy_policy.html`); images are relative (`images/x.jpg`).
- **The author's voice is first person singular** — "I", not "we".

## Commands

- No build or preview here: GitHub Pages builds `docs/` on every push to `master` (legacy build, no workflow file).

## Maintenance of this file

Loaded every turn; cap 34 KB, a module's own `AGENTS.md` 10 KB. Over it, in this order:
delete what has no home — status, history, class lists, what the code already says; trim
each line to its fact plus one clause and send the explanation home — why →
`design/decisions.md`, how across symbols → `design/architecture.md`, how in one symbol →
its doc comment, what upstream does → `design/research.md`; only then a module's own
`AGENTS.md`, peripheral modules first, never the core. Never paraphrase a lazy entry into a
line here.
