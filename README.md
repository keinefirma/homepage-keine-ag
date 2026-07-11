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

## Offene Punkte

- Handelsregister-Eintrag (Kanton, UID) ist im Impressum vorerst
  ausgelassen und kann bei Bedarf ergänzt werden.
- Bei den Vertretungsberechtigten sind noch keine Namen genannt; aktuell
  wird auf die E‑Mail-Adresse verwiesen.

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

## Deployment

Live unter https://keinefirma.github.io/homepage-keine-ag/. Jeder Push auf
`claude/eu-ch-landing-page-9kl8tz` deployt die Seite automatisch über den
Workflow `deploy-staging.yml`; er lässt sich zusätzlich manuell starten
(Actions → «Deploy staging (GitHub Pages)» → Run workflow).
