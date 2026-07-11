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
| `assets/logo.svg` | Original-Logo (Vektor, alle Schriften als Pfade) |
| `.github/workflows/deploy-staging.yml` | Staging-Deployment auf GitHub Pages |

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

Das Deployment auf GitHub Pages läuft über den Workflow
`deploy-staging.yml` (Actions → «Deploy staging (GitHub Pages)» →
Run workflow). Voraussetzung: GitHub Pages muss einmalig aktiviert werden
(Settings → Pages → Source: «GitHub Actions»); bei privaten Repositories
setzt Pages einen bezahlten GitHub-Plan voraus. Hinweis: Die Pages-URL ist
öffentlich erreichbar, auch wenn das Repository privat ist.
