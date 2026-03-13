<p align="center">
  <img src="https://github.com/weissalexey/ScanApp/blob/main/ScanApp.png" alt="ScanApp" />
</p>


ScanApp von LisIn – Wie zwei Templates die Welt verändern
Manchmal hilft nur eins: selbst Hand anlegen.

Eines schönen Tages kam unser Crossdock mit einem harmlosen Wunsch:
"Könnt ihr anzeigen, ob ein gescannter Artikel bereits im Lager ist?"
Also einfach ein grüner Haken bei WE gescannt.

Klingt einfach? Dachten wir auch.
Aber bei LisIn wurde das zur Odyssee…
Irgendwann hab ich beschlossen: Schluss mit Warten, ich mach's selbst.
Ein bisschen Dateistruktur, ein paar Nächte – und voilà:

🛠️ Es reicht völlig, zwei Templates und die Web.config anzupassen.

🔧 Geändert werden müssen:
ScanSSCCInboundListTemplate.cshtml
MasterStopsListTemplate.cshtml
ScanSSCCListTemplate1.cshtml

Web.config (für die Verbindungsparameter)

Damit lassen sich alle gewünschten Daten ganz flexibel anzeigen – direkt beim Scannen.

---

## 🆕 Neues Feature: Terminkennzeichen-Icons (Fix, Prio, Nextday, HUB-Priorität)

Neu hinzugekommen ist die visuelle Anzeige von Terminkennzeichen direkt in der Sendungsliste.
Das System liest das Feld `InfoSymbol16` aus der Datenbank und zeigt je nach Wert automatisch das passende Icon an:

| Wert | Bedeutung | Icon |
|------|-----------|------|
| `15`, `17`, `18` | Overnight / Nextday | 🌙 `overnight.png` |
| `36` | Prioritätssendung | ⚡ `PRIO.png` |
| `37` | HUB-Priorität | 🏭 `HUBP.png` |
| sonstige Werte | Fix-Termin | 📌 `FIX.png` |

Dabei bleibt die bestehende Logik für `InfoSymbol12` (GCC, Storno) vollständig erhalten –
beide Icons werden gleichzeitig angezeigt, falls beide Felder gesetzt sind.

Die Abfrage läuft über zwei unabhängige SQL-Queries, ohne die vorhandene Systemlogik zu berühren.

---

Falls dir das bekannt vorkommt –
melde dich gern bei mir 😄

Gemeinsam bringen wir ein bisschen Magie in ScanApp!
