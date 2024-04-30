# FAR Webseite

Die [Webseite](https://alternative-raumfahrt.de) der Forschungsgemeinschaft alternative Raumfahrt e.V.

* [GitLab](https://gitlab.com/glimpse-of-life/far-test)
* [Netlify Test-Umgebung](https://cute-kheer-16d1b4.netlify.app/)

Basiert auf

* [Hugo](https://gohugo.io)
* [Hugo Theme Tailbliss](https://github.com/nusserstudios/tailbliss)
* [Tailwind](https://tailwindcss.com/)

## Voraussetungen

Installation von

* [https://gohugo.io/categories/installation/](https://gohugo.io/categories/installation/)
* [https://nodejs.org/en/learn/getting-started/how-to-install-nodejs](https://nodejs.org/en/learn/getting-started/how-to-install-nodejs)
* [https://docs.npmjs.com/downloading-and-installing-node-js-and-npm](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm)

```
node -v
npm -v
hugo version
```

## Git archiv clonen

Für gemeinames Arbeiten das Git Archiv in ein lokales Verzeichnis clonen:

* [https://gitlab.com/glimpse-of-life/far-test.git](https://gitlab.com/glimpse-of-life/far-test.git)

Ich arbeite mit Visual Studio Code.

```
npm install
```

## Dev server starten

```
npm run dev
```
Der Server ist unter [http://localhost:1313/](http://localhost:1313/) erreichbar, und kann mit `Ctrl+C` beendet werden.

## Webseite kompilieren

* Die Webseite wird im Verzeichnis `public` erzeugt.
* Optional vorher unerwünschte Dateien löschen.
* Vor dem finalen Build ein git commit machen. 
* Das Änderugsdatum wird erst danach wirksam. Das hat einen Einfluss auf die Sortierfolge von Listen haben, wenn nach Datum sortiert oder gefiltert wird.

```
find . -type f -name .DS_Store -delete
npm run build
```

Ein build fügt nur zum `public` Verzeichnis hinzu. Es werden keine Inhalte gelöscht! Deshalb ist es ratsam, das Verzeichnis von Zeit zu Zeit vor dem Build zu löschen.

### Fallstricke

Hugo veröffentlicht keine Inhalte, wenn:

- `draft` value is true
- `date` is in the future
- `lastmod` is in the future
- `publishDate` is in the future
- `The expiryDate` is in the past


Also nicht wundern.

## Schnelles ZIP-Archiv als Backup erstellen (ohne git)

```bash
zip -r far-webseite-backup-$(date +"%Y-%m-%d").zip . -x '/node_modules/**' '/public/**' 'resources/_gen/*' '.git/*' '*.zip'
```

### Check Packages for Updates and update

- https://www.npmjs.com/package/npm-check-updates

```bash
npx npm-check-updates
npx npm-check-updates -u
npm install
```