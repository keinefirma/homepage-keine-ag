# Keine AG – Homepage

Statische Landing Page der Keine AG (Nico & Juul). Bewusst minimal gehalten:
**kein JavaScript, keine Cookies, kein Tracking, keine Inhalte von Drittservern**
– darum ist auch kein Cookie-Banner nötig.

## Struktur

| Datei | Zweck |
| --- | --- |
| `index.html` | Landing Page (Logo zentriert, Kontakt-Button oben) |
| `impressum.html` | Impressum (CH, Art. 3 Abs. 1 lit. s UWG) |
| `datenschutz.html` | Datenschutzerklärung (revDSG / DSGVO) |
| `styles.css` | Gesamtes Styling, nur Systemschriften |
| `assets/logo.png` | Logo (siehe unten) |
| `.github/workflows/deploy-staging.yml` | Staging-Deployment auf GitHub Pages |

## Logo ersetzen

`assets/logo.png` ist eine **Nachbildung** des Original-Logos (der
Chat-Anhang konnte nicht als Datei übernommen werden). Original-PNG einfach
als `assets/logo.png` einchecken – sonst ist nichts anzupassen.

## Offene Platzhalter

In `impressum.html` und `datenschutz.html` sind gelb hinterlegte
`[Platzhalter]` zu ergänzen: Adresse, Nachnamen, Kanton des
Handelsregisters, UID-Nummer.

## Sicherheit

- Kein JavaScript und keine Formulare → keine XSS-/Injection-Angriffsfläche,
  keine API-Endpunkte.
- Strikte Content-Security-Policy per `<meta>`-Tag auf jeder Seite
  (`default-src 'none'`; nur eigene Bilder und Styles erlaubt).
- `referrer: no-referrer`, keine externen Requests.
- GitHub Pages erlaubt keine eigenen HTTP-Header. Beim Umzug auf das
  endgültige Hosting zusätzlich als echte Header setzen:
  `Content-Security-Policy` (inkl. `frame-ancestors 'none'`),
  `X-Content-Type-Options: nosniff`, `Referrer-Policy: no-referrer`,
  `Strict-Transport-Security`.

## Staging

Jeder Push auf `claude/eu-ch-landing-page-9kl8tz` oder `main` deployt die
Seite über GitHub Actions auf GitHub Pages (Workflow
`deploy-staging.yml`). Hinweis: Die Pages-URL ist öffentlich erreichbar,
auch wenn das Repository privat ist.
