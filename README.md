# Countdown-widget for Google Sites

Det har paketet innehaller:

- `index.html` - startsida for GitHub Pages
- `countdown-widget.html` - sjalva widgeten som du bygger in i Google Sites
- `countdown-builder.html` - en visuell byggare for datum, tema, farger och storlek
- `.nojekyll` - gor att GitHub Pages serverar sajten utan Jekyll-bearbetning

## GitHub Pages

Sa publicerar du den pa GitHub Pages:

1. Skapa ett nytt GitHub-repo och ladda upp alla filer i den har mappen.
2. Gaa till `Settings > Pages`.
3. Under `Build and deployment`, valj `Deploy from a branch`.
4. Valj din branch, oftast `main`, och mappen `/(root)`.
5. Spara. GitHub Pages publicerar sedan sajten pa en URL i stil med `https://anvandarnamn.github.io/repo-namn/`.
6. Nar sajten ar live, oppna startsidan eller `countdown-builder.html` pa den publicerade URL:en.

Byggaren kanner automatiskt av GitHub Pages-adressen och fyller i `Hostad bas-URL` at dig.

## Sa anvander du den

1. Publicera filerna pa GitHub Pages eller annan statisk host.
2. Oppna `index.html` eller `countdown-builder.html`.
3. Valj datum, tid, UTC-offset, tema och farger.
4. Kontrollera `Hostad bas-URL`. Pa GitHub Pages fylls den normalt i automatiskt, till exempel `https://anvandarnamn.github.io/repo-namn`.
5. Fyll i `GitHub-repo`, `Branch`, `Konfigurationsfil` och en GitHub-token i byggarens publiceringsdel.
6. Klicka `Publicera till GitHub`.
7. Kopiera den `Publicerad widget-URL` eller `Iframe-kod` som byggaren visar.
8. I Google Sites valjer du `Infoga > Badda in` och klistrar in URL:en.

## Publicering fran byggaren

Byggaren kan nu publicera en JSON-konfiguration direkt till ditt GitHub-repo. Den inbaddade widgeten pa Google Sites pekar da pa en fast URL i stil med:

```text
countdown-widget.html?config=published/default.json
```

Det betyder att du kan behalla samma inbaddade URL i Google Sites och bara publicera om konfigurationen nar du vill uppdatera design, datum eller farger.

For att publicering ska fungera behovs en GitHub-token med `Contents: Read and write` for repot. Ett bra val ar en fine-grained personal access token som bara har access till just detta repo.

## Viktiga parametrar

Widgeten styrs via query-parametrar i URL:en. Exempel:

```text
countdown-widget.html?target=2026-12-31T23:59:59+01:00&theme=soft&accent=%23b7c49f
```

Vanliga parametrar:

- `target` - datum och tid i ISO-format med offset, exempel `2026-12-31T23:59:59+01:00`
- `theme` - `soft`, `glass`, `midnight`, `minimal`, `luxe`, `aurora`, `ember`
- `title` - rubrik ovanfor widgeten
- `subtitle` - underrubrik ovanfor widgeten
- `accent` - siffrornas farg
- `cardColor` - kortens basfarg, till exempel `#ffffff`
- `cardOpacity` - kortens transparens i procent, till exempel `95`
- `card` - valfri avancerad CSS-override for kortens bakgrund, till exempel `linear-gradient(...)`
- `cardBorderColor` - kortkantens basfarg, till exempel `#ffffff`
- `cardBorderOpacity` - kortkantens transparens i procent, till exempel `56`
- `cardBorder` - valfri avancerad CSS-override for kortkanten, till exempel `rgba(255,255,255,0.56)`
- `label` - textfarg for enhetsnamnen
- `separator` - farg pa kolon
- `backgroundColor` - bakgrundens basfarg, till exempel `#3a4031`
- `backgroundOpacity` - bakgrundens transparens i procent, till exempel `100`
- `background` - valfri avancerad CSS-override for hela bakgrunden, till exempel `linear-gradient(...)`
- `image` - bakgrundsbildens URL
- `radius` - kortens rundning i pixlar
- `gap` - avstand mellan blocken i pixlar
- `daysDigits` - minsta antal siffror for dagar
- `showLabels` - `true` eller `false`
- `showSeparators` - `true` eller `false`
- `config` - sokvag eller URL till en publicerad JSON-konfiguration, till exempel `published/default.json`

## Designutgangspunkt

Standardtemat `soft` ar byggt for att ligga nara din referensbild:

- ljusa sifferkort
- mjukt gron sifferfarg
- vita etiketter
- varm, floristisk bakgrundston
- tydliga kolon mellan grupperna

## Tips for Google Sites

- Om din host blockerar iframe med `X-Frame-Options`, byt host eller anvand Google Sites inbaddning via URL om den hosten tillater det.
- Anvand alltid `target` med tidszon eller UTC-offset sa att nedrakningen visar samma sluttid for alla besokare.
