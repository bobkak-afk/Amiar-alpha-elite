# 🍉 Fruit Slash – Komplette App-Store-Anleitung

> Ein vollständiges Arcade-Schneidespiel, bereit für iOS App Store und Google Play Store.

---

## 📁 Projektstruktur

```
fruitslash/
├── src/
│   ├── index.html          ← Das komplette Spiel (HTML5 + Canvas)
│   ├── manifest.json       ← PWA-Manifest
│   └── assets/
│       ├── icon-*.png      ← Alle App-Icons (9 Größen)
│       └── splash-*.png    ← Alle Splash Screens (6 Größen)
├── ios-meta/
│   └── AppIcon.appiconset/ ← Xcode-fertiges Icon-Set + Contents.json
├── store-assets/
│   ├── screenshot-1.png    ← App Store Screenshot 1
│   ├── screenshot-2.png    ← App Store Screenshot 2
│   ├── store-metadata.txt  ← Alle Store-Texte (DE + EN)
│   └── privacy-policy.html ← Datenschutzerklärung (Pflicht!)
├── capacitor.config.json   ← Capacitor Konfiguration
├── package.json
└── README.md               ← Diese Datei
```

---

## 🚀 Schritt-für-Schritt: App Store Veröffentlichung

### VORAUSSETZUNGEN

| Was | Wo herunterladen | Kosten |
|-----|-----------------|--------|
| Node.js 18+ | nodejs.org | Kostenlos |
| Xcode 15+ | Mac App Store | Kostenlos |
| Android Studio | developer.android.com | Kostenlos |
| Apple Developer Account | developer.apple.com | **99 €/Jahr** |
| Google Play Account | play.google.com/console | **25 € einmalig** |

---

### SCHRITT 1 – Projekt aufsetzen

```bash
# In den Projektordner wechseln
cd fruitslash

# Dependencies installieren
npm install

# Capacitor initialisieren (falls noch nicht geschehen)
npx cap init "Fruit Slash" "com.fruitslash.game" --web-dir src
```

---

### SCHRITT 2 – iOS App erstellen 🍎

```bash
# iOS-Plattform hinzufügen
npm run add:ios

# Web-Assets synchronisieren
npm run sync:ios

# Xcode öffnen
npm run open:ios
```

**In Xcode:**
1. Wähle links dein Projekt → `FruitSlash` → `Signing & Capabilities`
2. Wähle dein **Apple Developer Team**
3. Bundle Identifier: `com.fruitslash.game`
4. Ersetze `App/App/Assets.xcassets/AppIcon.appiconset/` mit dem Inhalt aus `ios-meta/AppIcon.appiconset/`
5. Füge Splash Screens hinzu: `LaunchScreen.storyboard` → verwende `assets/splash-*.png`
6. **Product → Archive** → In App Store Connect hochladen

---

### SCHRITT 3 – Android App erstellen 🤖

```bash
# Android-Plattform hinzufügen
npm run add:android

# Web-Assets synchronisieren
npm run sync:android

# Android Studio öffnen
npm run open:android
```

**In Android Studio:**
1. Warte auf Gradle Sync
2. Icons ersetzen: `app/src/main/res/` → `mipmap-*` Ordner mit Icons aus `src/assets/`
3. Version setzen: `app/build.gradle` → `versionCode 1`, `versionName "1.0.0"`
4. **Build → Generate Signed Bundle/APK** → AAB auswählen
5. Keystore erstellen oder vorhandenen verwenden
6. Im Google Play Console hochladen

---

### SCHRITT 4 – Apple App Store Connect 🍎

1. Gehe zu [appstoreconnect.apple.com](https://appstoreconnect.apple.com)
2. **+ Neue App** → iOS → Infos eingeben:
   - **Name:** Fruit Slash – Schneidespiel
   - **Bundle ID:** com.fruitslash.game
   - **SKU:** fruitslash-001
   - **Sprachen:** Deutsch, Englisch

3. **App-Informationen** ausfüllen (aus `store-assets/store-metadata.txt`):
   - Kategorie: **Spiele → Action & Arcade**
   - Altersfreigabe: **4+**
   - Datenschutz-URL: Hoste `privacy-policy.html` und trage die URL ein

4. **Screenshots hochladen** (aus `store-assets/`):
   - 6,7" Display (1290×2796): screenshot-1.png, screenshot-2.png
   - Optional weitere Gerätegrößen

5. **Preise:** Kostenlos
6. **Review-Informationen** ausfüllen:
   - Tester-Account: *nicht nötig (keine Anmeldung)*
   - Demo-Video: *optional, empfohlen*
7. **Zur Prüfung einreichen** → Apple prüft i.d.R. innerhalb von 1–3 Tagen

---

### SCHRITT 5 – Google Play Console 🤖

1. Gehe zu [play.google.com/console](https://play.google.com/console)
2. **App erstellen** → Android → Kostenlos
3. **Store-Eintrag** ausfüllen:
   - Kurzbeschreibung + Vollständige Beschreibung aus `store-metadata.txt`
   - Screenshots hochladen
   - Feature-Grafik: 1024×500px (eigenes Banner erstellen)
4. **Datenschutz:** Datenschutzerklärung-URL eintragen
5. **Inhaltsbewertung:** Fragebogen ausfüllen → EVERYONE / USK 0
6. **Zielgruppe:** Kinder → Kinder-Richtlinien bestätigen
7. **AAB hochladen** (aus Android Studio)
8. **Zur Prüfung einreichen** → Google prüft i.d.R. in 1–7 Tagen

---

## 🎨 Optional: Marketing-Materialien

### App-Vorschau-Video (sehr empfohlen!)
- Länge: 15–30 Sekunden
- Zeige echtes Gameplay: Früchte schneiden, Combo, Bomben ausweichen
- Tools: QuickTime (iOS-Simulator aufnehmen), dann Schnitt in iMovie/CapCut

### Feature-Grafik für Google Play (Pflicht!)
- Größe: 1024 × 500 Pixel
- Zeige den Spielnamen + Früchte + Gameplay-Screenshot
- Erstelle es in Canva.com oder Figma (kostenlos)

---

## 🔧 App-ID anpassen

Wenn du deine eigene Bundle-ID nutzen möchtest:

1. In `capacitor.config.json`: `"appId": "com.DEINNAME.fruitslash"`
2. In Xcode: Signing & Capabilities → Bundle Identifier anpassen
3. In `android/app/build.gradle`: `applicationId` anpassen

---

## ✅ Checkliste vor Einreichung

- [ ] App läuft auf echtem iPhone/iPad getestet
- [ ] App läuft auf echtem Android-Gerät getestet
- [ ] Datenschutz-URL ist erreichbar (privacy-policy.html hosten)
- [ ] Alle Screenshots hochgeladen
- [ ] Altersfreigabe korrekt gesetzt (4+)
- [ ] Keine Abstürze oder ANR-Fehler
- [ ] Hochformat (Portrait) funktioniert korrekt
- [ ] Sound funktioniert (und kein Sound beim ersten Start ohne Interaktion)
- [ ] Highscore wird gespeichert und beim Neustart geladen

---

## 🌐 Als PWA sofort teilen (ohne App Store!)

Du kannst die App auch direkt als Progressive Web App teilen:

```bash
# Statische Dateien hosten (z.B. mit Netlify, GitHub Pages, Vercel)
# Einfach den Inhalt von /src/ hochladen – fertig!
```

Dann kann jeder die URL auf seinem Handy öffnen und
**"Zum Homescreen hinzufügen"** wählen – sieht aus wie eine echte App!

---

## 📞 Support

Bei Fragen: Erstelle eine Datei `support.html` neben `privacy-policy.html`
und hoste beide auf derselben URL (Pflicht für Apple).

---

*Viel Erfolg im App Store! 🚀🍉*
