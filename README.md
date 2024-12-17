# FAR Webseite

Die [Webseite](https://alternative-raumfahrt.de) der Forschungsgemeinschaft alternative Raumfahrt e.V.

* [Github homepage](https://github.com/cnichte/far-webseite)
* [Netlify Test-Umgebung](https://alternative-raumfahrt.netlify.app/)

Basiert auf

* [Hugo](https://gohugo.io)
* [Hugo Theme Tailbliss](https://github.com/nusserstudios/tailbliss)
* [Tailwind CSS 3](https://tailwindcss.com/)
* [Apline.JS](https://alpinejs.dev/)

## Voraussetungen

Installation von

* [https://gohugo.io/categories/installation/](https://gohugo.io/categories/installation/)
* [https://nodejs.org/en/learn/getting-started/how-to-install-nodejs](https://nodejs.org/en/learn/getting-started/how-to-install-nodejs)
* [https://docs.npmjs.com/downloading-and-installing-node-js-and-npm](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm)

```bash
node -v
npm -v
hugo version
```

## Verzeichnis Struktur

Da hat sich folgendes bewährt, vor allem wenn man WakaTime bzw. ein selfhosted [Wakapi](https://wakapi.dev) zum Zeiten tracken verwendet:

* `projekte/far-webseite/produktion/far-webseite/`
* `projekte/far-webseite/test/far-webseite/`
* `projekte/far-webseite/entwicklung/far-webseite/`
* `projekte/far-webseite/migration/far-webseite/`

## Git archiv clonen

Für gemeinames Arbeiten das Git Archiv in ein lokales Verzeichnis clonen:

* [https://github.com/cnichte/far-webseite.git](https://github.com/cnichte/far-webseite.git)

Ich arbeite mit Visual Studio Code.

```bash
npm install
```

## Dev server starten

```bash
npm run dev
# oder
npm start
```

Der Server ist unter [http://localhost:1313/](http://localhost:1313/) erreichbar, und kann mit `Ctrl+C` beendet werden.

## Webseite kompilieren

* Die Webseite wird im Verzeichnis `public` erzeugt.
* Optional vorher unerwünschte Dateien löschen.
* Vor dem finalen Build ein git commit machen.
* Das Änderugsdatum wird erst danach wirksam. Das hat einen Einfluss auf die Sortierfolge von Listen, wenn nach Datum sortiert oder gefiltert wird.

```bash
# unerwünschte Dateien löschen
find . -type f -name .DS_Store -delete
# gefolgt von einem 
npm run build
# oder
npm run cleanbuild
```

Ein build fügt nur zum `public` Verzeichnis hinzu. Es werden keine Inhalte gelöscht! Deshalb ist es ratsam, das Verzeichnis von Zeit zu Zeit vor dem Build zu löschen, oder `cleanbuild` zu benutzen.

### Fallstricke

Hugo veröffentlicht keine Inhalte, wenn:

* `draft` value is true
* `date` is in the future
* `lastmod` is in the future
* `publishDate` is in the future
* `The expiryDate` is in the past

Also nicht wundern.

## Schnelles ZIP-Archiv als Backup erstellen (ohne git)

```bash
zip -r far-webseite-backup-$(date +"%Y-%m-%d").zip . -x '/node_modules/**' '/public/**' 'resources/_gen/*' '.git/*' '*.zip'
```

## Check Packages for Updates and update

* <https://www.npmjs.com/package/npm-check-updates>

```bash
npx npm-check-updates
npx npm-check-updates -u
npm install
```

VORHER EIN BACKUP VOM VERZEICHNIS MACHEN

### Update und Migration

Falls nach einem Update nix mehr läuft, bitte im Verzeichnis `migration` ein aktuelles Tailbliss aufsetzen und die Inhalte aus der Produktion mit der App BeyondCompare rüber migrieren...

### Aktuelles Tailbliss aufsetzen

* <https://github.com/nusserstudios/tailbliss>

Bitte NICHT der Anleitung dort folgen:

```bash
# Install to VS Code with:
git clone git@github.com:nusserstudios/tailbliss my-folder
```

Das führt zu einem Fehler der Art:

```bash
git@github.com: Permission denied (publickey).
fatal: Could not read from remote repository.

Please make sure you have the correct access rights
and the repository exists.
```

SONDERN: `Clone using the web URL` in VS-Code verwenden:

* <https://github.com/nusserstudios/tailbliss.git>

![VS-Code Welcome Screen](images-readme/VS-Code-Willkommen.png?raw=true "Title")
