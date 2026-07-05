# Marion Frei — Psychosoziale Beratung (Hugo)

Statische Website (Hugo) für die psychosoziale Beratungspraxis von Marion Frei.

## Voraussetzungen

- [Hugo](https://gohugo.io/installation/) (Extended nicht zwingend nötig) — empfohlen ≥ 0.128

## Lokal starten

```bash
hugo server
```

Dann im Browser http://localhost:1313 öffnen. Änderungen werden live aktualisiert.

## Produktion bauen

```bash
hugo --gc --minify
```

Das fertige Resultat liegt anschliessend im Ordner `public/` und kann auf jeden
statischen Host (Netlify, GitHub Pages, eigenes Webhosting …) hochgeladen werden.

## Projektstruktur

```
hugo.toml                 # Konfiguration (Titel, baseURL …)
content/                  # je eine Seite (Front Matter steuert das Layout)
  _index.md               # Startseite
  angebot.md  ueber.md  kontakt.md  impressum.md  datenschutz.md
layouts/
  _default/baseof.html    # Grundgerüst (Head, Header, Footer)
  index.html              # Startseite
  _default/*.html         # je ein Layout pro Unterseite
  partials/               # head, header, footer, leaf, scripts
static/
  css/style.css           # gesamtes Styling
  images/                 # Bilder + Logo (leaf-white.svg)
```

## Inhalte ändern

**Alle Texte stehen in `content/` — nicht im Layout.** Die Layouts unter
`layouts/` enthalten nur noch Struktur/Markup und lesen die Inhalte aus.

- **Startseite:** `content/_index.md` — Texte als Front-Matter-Felder
  (`hero`, `intro`, `themes`, `quote_band`, `cta`).
- **Angebot / Kontakt:** `content/angebot.md`, `content/kontakt.md` — Überschriften,
  Listen (Themen, Kontaktangaben, Tarife) als Front-Matter-Felder.
- **Über mich:** `content/ueber.md` — Eckdaten als Front Matter, der Biografie-Text
  als ganz normaler Markdown-Text unter dem `---`.
- **Impressum / Datenschutz:** `content/impressum.md`, `content/datenschutz.md` —
  kompletter Text als Markdown (Überschriften mit `##`, Listen mit `-`).

Neue Themen/Stationen/Tarifzeilen fügst Du einfach als weiteren Listenpunkt hinzu —
Nummerierung und Layout passen sich automatisch an.

Bilder liegen in `static/images/` — einfach gleichnamig ersetzen.

**Farben & Schriften:** zentral in `hugo.toml` unter `[params.theme]` — Hex-Farben
und Google-Fonts-Namen eintragen, kein CSS nötig. Neue Schrift auch in die Liste
`googleFonts` eintragen, damit sie geladen wird.

## Deploy auf Netlify

Dieses Repo enthält `netlify.toml`. In Netlify einfach das Git-Repo verbinden —
Build-Command `hugo --gc --minify` und Publish-Verzeichnis `public` sind bereits
hinterlegt. Das Kontaktformular ist für **Netlify Forms** vorbereitet
(`data-netlify="true"`, Formularname „kontakt").

## Inhalte pflegen ohne Technik-Kenntnisse (Decap CMS)

Unter `static/admin/` liegt eine Editor-Oberfläche (Decap CMS), erreichbar
nach dem Deploy unter `https://<domain>/admin/`. Dort lassen sich alle Texte
und Bilder über Formulare bearbeiten — jede Änderung erzeugt automatisch
einen Commit im Git-Repo, Netlify baut die Seite danach neu.

**Einmalige Einrichtung in Netlify (durch Dich/Entwickler:in):**

1. Site Settings → **Identity** → „Enable Identity“.
2. Identity → Registration auf **Invite only** stellen.
3. Identity → Services → **Git Gateway** aktivieren.
4. Identity → **Invite users** → E-Mail-Adresse der Redakteurin einladen.
   Sie erhält eine E-Mail, setzt ein Passwort und kann sich danach unter
   `/admin/` einloggen.

Danach ist keine weitere technische Handhabung nötig — Login, Text ändern,
Speichern („Publish"/„Veröffentlichen") genügt.

## Hinweis

Impressum und Datenschutzerklärung sind sorgfältig erstellte Vorlagen, jedoch
keine Rechtsberatung. Bitte vor dem Aufschalten prüfen (insb. vollständige
Adresse).
