# Wie hell ist dein Prompt? – Veröffentlichung mit KI-Prüfung

## Was in diesem Ordner liegt
- `index.html`: die App
- `netlify/functions/check.mjs`: prüft per KI, welche der sechs Bausteine ein Prompt enthält. Gibt nur Ja/Nein-Werte zurück, speichert nichts.
- `netlify.toml`: Einstellungen für Netlify

Ohne erreichbare KI prüft die App automatisch mit Signalwörtern weiter.

## 1. API-Schlüssel anlegen (einmalig, macht Anja selbst)
1. Unter https://console.anthropic.com ein Konto anlegen. Das ist getrennt vom Claude-Max-Abo.
2. Unter Billing ein kleines Guthaben kaufen, etwa 10 Euro. Das Guthaben ist gleichzeitig der Kostendeckel. Automatisches Nachladen ausgeschaltet lassen.
3. Unter API Keys einen Schlüssel mit dem Namen „tag-der-ki“ anlegen und kopieren. Den Schlüssel nirgends in Chats, Mails oder Dateien einfügen.

## 2. Veröffentlichen
Wichtig: Das Hochladen per Drag-and-drop auf netlify.com funktioniert hier nicht, weil dabei keine Funktionen übernommen werden. Zwei Wege:
- **Über Evi:** Netlify-Verbindung in Claude erneuern, dann veröffentlicht Evi den Ordner.
- **Selbst per Kommandozeile:** Im Ordner `npx netlify-cli deploy --prod` ausführen und den Anweisungen folgen.

## 3. Schlüssel bei Netlify hinterlegen (macht Anja selbst)
1. In Netlify die Seite öffnen, dann Site configuration → Environment variables.
2. Neue Variable: Name `ANTHROPIC_API_KEY`, Wert = der kopierte Schlüssel. Als „secret“ markieren.
3. Unter Deploys einmal „Trigger deploy“ auslösen, damit die Funktion den Schlüssel kennt.

## 4. Testen
- Seite am Handy öffnen, Bereich wählen, einen Prompt senden.
- Beim Senden erscheint kurz „Die KI prüft deinen Prompt …“.
- Kontrolle, ob die KI arbeitet: Einen frei formulierten Prompt ohne typische Signalwörter senden, zum Beispiel „Hey, ich bin 16 und spare auf ein neues Handy. Was davon kommt eigentlich von ams OSRAM?“. Erkennt die App Position, Kontext und Auftrag, arbeitet die KI.

## 5. Nach dem Event
- Den Schlüssel in der Anthropic Console löschen.
- Seite bei Netlify offline nehmen oder die App ohne Funktion weiterlaufen lassen.
