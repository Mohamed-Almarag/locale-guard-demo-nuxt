# Locale Guard demo: Nuxt

A small Nuxt travel site in English, Arabic, French and German, translated with
[@nuxtjs/i18n](https://i18n.nuxtjs.org). It shows what
[Locale Guard](https://github.com/Mohamed-Almarag/locale-guard) reports on real
pull requests.

## Setup

| | |
|---|---|
| Framework | Nuxt 4 |
| Translation library | `@nuxtjs/i18n` (vue-i18n messages) |
| Locale files | `i18n/locales/{locale}.json`, one file per language |
| Base locale | `en` |

The whole setup is one workflow file,
[.github/workflows/translations.yml](.github/workflows/translations.yml):

```yaml
- uses: Mohamed-Almarag/locale-guard@v1
  with:
    files: i18n/locales/{locale}.json
    format: '@nuxtjs/i18n'
```

## Pull requests to look at

| Pull request | What it shows | Result |
|---|---|---|
| [#1 Add booking checkout](https://github.com/Mohamed-Almarag/locale-guard-demo-nuxt/pull/1) | A new page with translation mistakes: missing keys, a typo in a placeholder, a link to a key that does not exist, an empty value, untranslated text, an extra key and a broken plural | ❌ Fails |
| [#2 Add trip details](https://github.com/Mohamed-Almarag/locale-guard-demo-nuxt/pull/2) | The first commit forgets French and German, the second one adds them, and the same comment turns green | ✅ Passes |
| [#3 Style the header](https://github.com/Mohamed-Almarag/locale-guard-demo-nuxt/pull/3) | A change that touches no translation file, so the check finishes in seconds | ✅ Passes |

The `main` branch already has two old issues: a key German never got, and a key
French still has after it was removed from English. Locale Guard lists them
apart from the issues each pull request adds, collapsed, and they do not fail
the check.

## Run the site

```bash
npm install
npm run dev
```
