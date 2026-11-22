# LEVEL UP — Student OS

Mobile-first PWA für Uni-Habits, XP, Lernnotizen und Wochenreviews. Keine externen Abhängigkeiten, kein Backend.

## Starten

Lokal: `python3 -m http.server 8080` im Projektordner ausführen, danach `http://localhost:8080` öffnen. Für die Installation als PWA auf iOS ist eine HTTPS-Website nötig.

## Kostenlos auf GitHub Pages veröffentlichen

1. Neues öffentliches GitHub-Repository anlegen, beispielsweise `level-up-student-os`.
2. Alle Dateien **aus diesem Ordner** in das Stammverzeichnis des Repositories hochladen.
3. Repository → Settings → Pages → Build and deployment → Deploy from a branch → `main` / `(root)` → Save.
4. Nach Veröffentlichung `https://DEIN-NAME.github.io/level-up-student-os/` in Safari öffnen.
5. Safari → Teilen → Zum Home-Bildschirm.

Die App verwendet relative Pfade und funktioniert auch unter GitHub-Pages-Unterverzeichnissen. Das Offline-Caching wird nach dem ersten erfolgreichen HTTPS-Laden aktiviert.

## Daten

Daten liegen in `localStorage` unter `levelup-student-os-v1`. Unter Setup kann ein JSON-Backup exportiert und importiert werden. **Backups regelmäßig extern sichern**: Browserdaten können gelöscht werden und werden nicht zwischen Geräten synchronisiert.

## Anpassung

Habits und XP: `baseTasks` in `app.js`; Wochenablauf: `schedule`; Fächer und Lerntipps: `subjects`. Woche A ist über Setup auf einen konkreten Montag einstellbar. A/B-Termine sind als Orientierung gedacht und müssen mit dem Stundenplan abgeglichen werden.

## Hinweise

Die App enthält keine externe Video-API. Die Videolinks öffnen YouTube-Suchanfragen, keine kuratierten oder geprüften Videos. XP werden nur einmal pro Datum und Habit vergeben; erneutes Abhaken entfernt sie. Keine künstlichen Streak-Strafen.


## Update v1.1 – Lifestyle

Neue Navigation **Lifestyle** mit Gewicht (wöchentlich oder täglich, Grafik, 7-Tage-Schnitt), Supplement-Checkliste, 13 Rezepten und eingebetteter Original-PDF `mealplan.pdf`. Gym und Gewicht sind bewusst nicht an Uni-XP gekoppelt. Neue Einträge werden im bisherigen lokalen Datensatz gespeichert und im JSON-Backup exportiert. Ältere Backups bleiben importierbar.

**Wichtig beim Update:** Alle Dateien inklusive `mealplan.pdf` hochladen und vorher ein JSON-Backup exportieren. Der Service Worker hat einen neuen Cache-Namen; ggf. die PWA nach dem Update einmal neu öffnen. Die Rezept-Kalorien sind ungeprüfte Näherungen aus der PDF. Das neue Gulasch hat bewusst keinen errechneten Kalorienwert. D3/K2 wird nach einem frei einstellbaren Startdatum alle zwei Tage angezeigt.


## v1.2: Abhakbare Tages-Timeline

Die Startseite und Wochenansicht enthalten jetzt einen Tagesablauf mit manuell abhackbarer Checkliste (ohne XP), groben Uhrzeiten, automatischer Markierung der laufenden Aktivität und A/B-Wochen. Die Zeiten sind **Richtwerte**, keine verbindlichen Kalendertermine. Die Fortschritte werden im bestehenden lokalen Backup unter `routineDone` gespeichert.

### Push-Benachrichtigungen

Noch **nicht implementiert**. iOS unterstützt Web Push für zum Home-Bildschirm hinzugefügte PWAs (ab iOS 16.4). Für zeitgesteuerte Benachrichtigungen bei geschlossener App benötigt man zusätzlich einen Push-Versanddienst/Server (z. B. einen kleinen Cloudflare Worker plus Scheduler), Push-Subscription, VAPID-Schlüssel und eine explizite Erlaubnis des Nutzers. GitHub Pages allein reicht nicht.
