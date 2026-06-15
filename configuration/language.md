# Language and Messages

ZaminShop keeps player-facing text in language files so you can change wording without rewriting Java code.

## Default file

```text
plugins/ZaminShop/lang/en_US.yml
```

## What belongs in the language file

This file covers more than chat messages.

It also includes text used by:

- menu items
- help output
- validation summaries
- Overwatcher output
- search, favorites, and recent menus
- sell GUI text
- number formatting labels

## Language metadata

The file begins with metadata such as:

```yaml
LANGUAGE:
  CODE: "en_US"
  NAME: "English"
  AUTHOR: "Zamin"
PREFIX: "&aZaminShop > &f"
```

## Why this matters

Keeping text centralized helps when you want to:

- change branding
- simplify player wording
- translate the plugin
- keep menu text consistent across several GUI files

## Good editing practice

When changing messages:

- keep placeholders intact
- keep color codes intentional
- do not rename keys unless you know the code no longer reads them

Example placeholders include values such as:

- `%item%`
- `%price%`
- `%player%`
- `%shop%`
- `%query%`

## Common mistakes

### Breaking placeholders

If you remove or mistype placeholders, the message may still render but lose important runtime data.

### Editing menu wording in the wrong place

Some menu text lives directly in GUI YAML files, while some reusable text comes from the language file. If the menu uses a `%zaminshop_*%` language-backed placeholder, edit the language file, not just the menu.
