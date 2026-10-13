# Security-Playbook (intern) – Schwachstellen und Vorfälle

Kurzanleitung für den Umgang mit Sicherheitsmeldungen bei OpenEOS und für die Meldepflichten nach **Art. 14 Cyber Resilience Act** (VO (EU) 2024/2847, gilt seit **11.09.2026**). Öffentliche Richtlinie für Meldende: [SECURITY.md](SECURITY.md).

> Keine Rechtsberatung. Ob und für welche Angebote OpenEOS „Hersteller“ im Sinne des CRA ist (v. a. vermietete Raspberry-Pi-Drucker-Stationen mit `openeos-printer-agent`), ist anwaltlich zu klären. Bis dahin gilt: **im Zweifel melden.**

## 0. Voraussetzungen (einmalig)

- [ ] Zugang zur **ENISA Single Reporting Platform (SRP)** einrichten: <https://portal.cra-srp.enisa.europa.eu/>
- [ ] Postfach `hello@openeos.de` täglich prüfen; Filter auf Betreff `[SECURITY]`.
- [ ] GitHub Private Vulnerability Reporting ist in allen öffentlichen Repos aktiv (Benachrichtigungen für Security Advisories eingeschaltet lassen).
- [ ] Geräteliste der vermieteten Hardware aktuell halten (Seriennummer, Erstvermietung, Software-Stand) – Grundlage für Betroffenheit und Kundeninformation (`rental-hardware` / `rental-assignments` in der API).
- [ ] Kontaktliste der Kunden (Vereine) mit gemieteten Geräten griffbereit.

## 1. Eingang und Triage (Stunde 0)

1. Meldung bestätigen (Ziel: < 72 h, besser sofort). Keine Details öffentlich besprechen; Commits, PRs und Issues neutral formulieren.
2. **Zeitpunkt der Kenntnisnahme notieren** – ab hier laufen die Fristen.
3. Einordnen:
   - **Aktiv ausgenutzte Schwachstelle** (Art. 3 Nr. 42 CRA): verlässliche Hinweise, dass ein böswilliger Akteur die Lücke ohne Erlaubnis ausgenutzt hat?
   - **Schwerer Sicherheitsvorfall** (Art. 14 Abs. 5): beeinträchtigt die Verfügbarkeit, Authentizität, Integrität oder Vertraulichkeit wichtiger Daten/Funktionen oder hat zur Ausführung von Schadcode geführt bzw. kann dazu führen?
   - Betroffenes Produkt: vermietete Drucker-Station / `openeos-printer-agent` (CRA-relevant), API als Datenfernverarbeitung dazu, reiner Browser-SaaS (CRA nicht anwendbar, ggf. DSGVO Art. 33 prüfen).
4. Wenn personenbezogene Daten betroffen sein können: **DSGVO Art. 33** (72 h an LfDI Baden-Württemberg) parallel prüfen.

## 2. Fristen nach Art. 14 CRA

| Frist ab Kenntnis | Aktiv ausgenutzte Schwachstelle (Abs. 2) | Schwerer Sicherheitsvorfall (Abs. 4) |
|---|---|---|
| **24 h** | **Frühwarnung**: betroffene Mitgliedstaaten, soweit bekannt | **Frühwarnung**: Verdacht auf rechtswidrige/böswillige Ursache, betroffene Mitgliedstaaten |
| **72 h** | **Schwachstellenmeldung**: Produkt, Art des Exploits, Schwachstelle, ergriffene Abhilfe, Schutzmaßnahmen für Nutzer, Sensibilität der Informationen | **Vorfallmeldung**: Art des Vorfalls, erste Bewertung, Abhilfe, Schutzmaßnahmen für Nutzer, Sensibilität |
| auf Anfrage | Zwischenbericht | Zwischenbericht |
| **Abschluss** | **spätestens 14 Tage**, nachdem eine Korrektur- oder Abhilfemaßnahme verfügbar ist | **spätestens 1 Monat** nach der Vorfallmeldung |

- Meldeweg: **ENISA SRP** → koordinierendes CSIRT des Mitgliedstaats der Hauptniederlassung (Deutschland, voraussichtlich **BSI**) und zugleich ENISA (Art. 14 Abs. 7, Art. 16).
- **Nutzer informieren** (Art. 14 Abs. 8): betroffene Kunden über die Lücke/den Vorfall und Gegenmaßnahmen unterrichten, ggf. in strukturiertem, maschinenlesbarem Format.
- Kleinst-/Kleinunternehmen werden für eine versäumte **24-h-Frist** nicht mit Bußgeld belegt (Art. 64 Abs. 10 lit. a) – die 72-h-Meldung und alle übrigen Pflichten gelten trotzdem.

## 3. Behebung und Veröffentlichung

1. Privaten Fork über das GitHub Security Advisory anlegen; Fix dort entwickeln und testen.
2. Fix nach `main` (Release), Deployment Produktion; vermietete Geräte aktualisieren.
3. GitHub Security Advisory veröffentlichen (CVE über GitHub anfordern, wenn sinnvoll), Finder:in nennen, sofern gewünscht.
4. Changelog-Eintrag als sicherheitsrelevant kennzeichnen.
5. Abschlussbericht an die SRP (Frist siehe oben).

## 4. Vorlagen (Stichpunkte)

**Frühwarnung (24 h):** Produkt/Version · Zeitpunkt der Kenntnis · Art (Schwachstelle/Vorfall) · aktiv ausgenutzt ja/Verdacht · betroffene Mitgliedstaaten (i. d. R. DE) · Kontakt.

**Meldung (72 h):** wie oben + technische Beschreibung · Ausnutzungsweg · bisherige Abhilfe · Empfehlung an Nutzer · Einstufung der Vertraulichkeit.

**Abschlussbericht:** Ursache · Schweregrad und Auswirkung · Korrekturmaßnahme mit Version/Datum · Informationen zu Angreifern (falls bekannt) · Kundeninformation erfolgt am.

**Kundeninformation:** Was ist passiert · welche Geräte/Dienste · was wurde getan · was müssen Kunden tun · Kontakt.

## 5. Quellen

- VO (EU) 2024/2847 (CRA), insb. Art. 3 Nr. 42, Art. 14, 16, 64, 69, 71 – <https://eur-lex.europa.eu/eli/reg/2024/2847/oj/deu>
- EU-Kommission, Leitlinien zum CRA, C(2026) 5252 – <https://digital-strategy.ec.europa.eu/en/library/commission-publishes-new-guidance-support-timely-cyber-resilience-act-implementation>
- ENISA: CRA Single Reporting Platform – <https://www.enisa.europa.eu/news/the-cra-single-reporting-platform-is-launched> · Portal: <https://portal.cra-srp.enisa.europa.eu/>
- BT-Drs. 21/6134 (Durchführungsgesetz, BSI als CSIRT) – <https://dserver.bundestag.de/btd/21/061/2106134.pdf>
- DSGVO Art. 33/34 – <https://eur-lex.europa.eu/eli/reg/2016/679/oj/deu>
