# Security Policy / Sicherheitsrichtlinie

[Deutsch](#deutsch) · [English](#english)

This policy applies to every repository of the [OpenEOS-Project](https://github.com/OpenEOS-Project) organization that does not ship its own `SECURITY.md`, and to the hosted service at `openeos.de` (app, shop, API, docs).

---

## Deutsch

### Schwachstelle melden

Bitte melde Sicherheitslücken **nicht** über öffentliche Issues, Pull Requests oder Diskussionen.

1. **Bevorzugt:** über GitHub im betroffenen Repository unter **Security → Report a vulnerability** (Private Vulnerability Reporting). Die Meldung ist nur für dich und die Maintainer sichtbar.
2. **Alternativ per E-Mail** an **hello@openeos.de** mit dem Betreff
   `[SECURITY] <Repository oder Dienst>: <kurze Beschreibung>`
   (z. B. `[SECURITY] openeos-api: Rechteprüfung bei Bestellungen`). Bitte keine Zugangsdaten oder personenbezogenen Daten Dritter mitschicken.

Hilfreich sind:

- betroffenes Repository bzw. betroffener Dienst und Version (Commit, Release oder Datum),
- Beschreibung der Schwachstelle und ihrer Auswirkung,
- Schritte zum Nachvollziehen oder ein Proof of Concept,
- ob die Lücke deines Wissens nach bereits aktiv ausgenutzt wird,
- wie wir dich für Rückfragen erreichen und ob du namentlich genannt werden möchtest.

### Was du von uns erwarten kannst

| Schritt | Ziel |
|---|---|
| Eingangsbestätigung | innerhalb von **72 Stunden** |
| Erste Einschätzung (Schweregrad, betroffene Versionen) | innerhalb von 7 Tagen |
| Behebung | so schnell wie möglich, je nach Schweregrad; wir halten dich auf dem Laufenden |

OpenEOS wird von einer Einzelperson betrieben. Die Zeiten sind Ziele, keine vertraglich zugesicherten Fristen.

### Unterstützte Versionen

| Version | Sicherheitsupdates |
|---|---|
| aktuelle Release-Linie (Branch `main` bzw. neuester Release, z. B. 1.6.x) | ja |
| gehosteter Dienst unter `openeos.de` | ja |
| ältere Versionen, `dev`-Stände, archivierte Repositories | nein – bitte auf die aktuelle Version aktualisieren |

Self-Hoster sollten Sicherheitsupdates zeitnah einspielen. Sicherheitsrelevante Änderungen kennzeichnen wir im Changelog.

### Koordinierte Offenlegung

- Wir bitten dich, Details erst zu veröffentlichen, wenn ein Fix bereitsteht oder **90 Tage** nach deiner Meldung vergangen sind – je nachdem, was früher eintritt. Den Zeitpunkt stimmen wir gern gemeinsam ab.
- Nach der Behebung veröffentlichen wir ein GitHub Security Advisory (bei Bedarf mit CVE) und nennen dich auf Wunsch als Finder:in.
- Wer in gutem Glauben forscht, diese Richtlinie einhält, keine Daten Dritter abruft oder verändert und den Betrieb nicht stört (kein DoS, kein Spam, kein Social Engineering), muss von uns keine rechtlichen Schritte befürchten.
- Teste bitte bevorzugt an einer eigenen Self-Hosting-Instanz oder einem eigenen Testkonto.

### Gesetzliche Meldepflichten

Für Produkte mit digitalen Elementen gelten seit dem 11.09.2026 die Meldepflichten nach Art. 14 des Cyber Resilience Act (VO (EU) 2024/2847). Aktiv ausgenutzte Schwachstellen und schwere Sicherheitsvorfälle melden wir intern geregelt über die ENISA Single Reporting Platform an das zuständige CSIRT. Deine Meldung hilft uns, diese Fristen einzuhalten.

---

## English

### Reporting a vulnerability

Please do **not** report security issues through public issues, pull requests or discussions.

1. **Preferred:** use GitHub in the affected repository under **Security → Report a vulnerability** (private vulnerability reporting). Only you and the maintainers can see the report.
2. **Alternatively by email** to **hello@openeos.de** with the subject
   `[SECURITY] <repository or service>: <short summary>`
   (e.g. `[SECURITY] openeos-api: permission check on orders`). Please do not include credentials or third parties' personal data.

Helpful details:

- affected repository or service and version (commit, release or date),
- description of the issue and its impact,
- steps to reproduce or a proof of concept,
- whether, to your knowledge, the issue is already being actively exploited,
- how we can reach you and whether you would like to be credited.

### What you can expect

| Step | Target |
|---|---|
| Acknowledgement | within **72 hours** |
| Initial assessment (severity, affected versions) | within 7 days |
| Fix | as fast as possible depending on severity; we keep you updated |

OpenEOS is run by a single person. These are targets, not contractual deadlines.

### Supported versions

| Version | Security updates |
|---|---|
| current release line (`main` branch or latest release, e.g. 1.6.x) | yes |
| hosted service at `openeos.de` | yes |
| older versions, `dev` snapshots, archived repositories | no – please upgrade to the current version |

Self-hosters should apply security updates promptly. Security-relevant changes are marked in the changelog.

### Coordinated disclosure

- Please do not publish details before a fix is available or **90 days** after your report, whichever comes first. We are happy to agree on a date together.
- Once fixed, we publish a GitHub security advisory (with a CVE where appropriate) and credit you if you wish.
- We will not take legal action against good-faith research that follows this policy, does not access or modify third parties' data and does not disrupt the service (no DoS, spam or social engineering).
- Please prefer testing against your own self-hosted instance or your own test account.

### Legal reporting obligations

Since 11 September 2026, the reporting obligations of Article 14 of the Cyber Resilience Act (Regulation (EU) 2024/2847) apply to products with digital elements. We report actively exploited vulnerabilities and severe incidents to the competent CSIRT via the ENISA Single Reporting Platform following an internal procedure. Your report helps us meet those deadlines.
