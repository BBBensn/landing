# landing — CLAUDE.md

Projekt-spezifischer Kontext. Ergänzt `~/.claude/CLAUDE.md`.
Ablageort: `~/Documents/Coding/bensn-hub/landing/CLAUDE.md`

---

## Projekt-Basics

- **Name:** landing
- **Domain:** bensn.me
- **Version:** v1.3.0
- **Status:** active
- **Stack:** Vanilla HTML + CSS + JS (reines Static-Frontend, kein Backend)

---

## Lokale Struktur

```
~/Documents/Coding/bensn-hub/landing/
├── index.html          ← aktuelle Landing-Page
├── logo/                ← Favicons, App-Icons, Original-Design-Datei (.af)
├── docs/changelogs/
├── CLAUDE.md
└── .gitignore
```

---

## Remote-Struktur

```
/var/www/bensn.me/
└── index.html                ← Landing-Page
```

Shared Assets (CSS/JS) liegen unter `/var/www/shared/` und werden von allen
bensn.me-Projekten gemeinsam genutzt (nginx-Alias `/shared/` → `/var/www/shared/`).

---

## Services & Ports

Kein Backend, kein systemd-Service. Pure static file über nginx.

| Dienst | Details |
|--------|---------|
| nginx  | `/etc/nginx/sites-enabled/bensn.me` · SSL via Let's Encrypt |

---

## Deploy

```bash
scp ~/Documents/Coding/bensn-hub/landing/index.html bensn:/var/www/bensn.me/index.html
```

Kein Service-Restart nötig (statisch). Shared Assets (`bensn.css`, `bensn.js`) werden
aus dem `bensn-meta`-Repo deployed (`bensn-meta/snapshots/.../shared/`).

---

## Git

- **Repo:** `https://github.com/BBBensn/landing`
- **Remote:** `git@github.com:BBBensn/landing.git`

---

## Auth

- Öffentlich — kein Auth (bensn.me ist public zugänglich)

---

## Projekt-spezifische Konventionen

- Alles in einer `index.html` — kein separates CSS/JS-File
- Shared Styles/Scripts via `/shared/bensn.css` und `/shared/bensn.js`
- Service-Cards zeigen: Domain, Name, Beschreibung, Tech-Tag (z.B. `Flask · Port 5001`)
- Farben der Cards sind pro Service definiert (CSS-Klassen `card-feed`, `card-wt`, etc.)
- Animationen: `intro-fade` mit gestaffelten `animation-delay`-Werten
- Neue Services bekommen eine Card, sobald sie live sind (z.B. demnächst `health.bensn.me`)

---

## Roadmap

| Version | Feature | Status |
|---------|---------|--------|
| v1.0.0–v1.2.4 | Frühe Iterationen | ✅ deployed |
| v1.3.0 | 6 Service-Cards, Meta-Footer, shared assets | ✅ deployed |
| — | Card für `health.bensn.me` ergänzen, sobald live | ⬜ geplant |

Details zur vollständigen Versionshistorie: `docs/changelogs/CHANGELOG.md`.

---

## Obsidian-Doku

- Projekt-MD: `03_Projects/Coding PC/Bensn-Hub/Landing/Landing.md`
- Changelogs: `03_Projects/Coding PC/Bensn-Hub/Landing/Changelogs/`
