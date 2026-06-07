# Six Shooter

Selvstændig HTML-app. Intet med Gallows Creek-spillet at gøre, men låner
visuelt DNA derfra (pergament, fonte, revolvertromle-animationen).

**Kør:** åbn `sixshooter.html` direkte i en browser — ingen server påkrævet.
UI-sproget er engelsk; appen er mobiloptimeret (portrait, touch-targets
≥ 44 px, ingen hover-afhængighed).

## Funktioner

Bygget videre på Gallows Creek-legeværktøjet `iggy-alma-picker.html` —
tromle-animationen (4 sek spin + zoom på øverste kammer), spin-lyden og
pergament-stilen er bevaret. Ovenpå:

- **To views** (CSS-vis/skjul, intet sideskift):
  - *Hovedside*: "Six Shooter"-titel (BleedingCowboys), tromlen (80 % af
    skærmbredden, kastet skygge), resultatlinje, spin-/fortsæt-knapper og
    footeren "From the Dusty Tales Saloon". Layoutet er fastlåst — tromle,
    resultat og knapper forskydes aldrig ved tilstandsskift (faste
    højde-zoner).
  - *Opsætningsside*: spillere + hold; tilgås via tandhjuls-knappen
    (ægte 8-takket gear-SVG) i øverste højre hjørne. Ved siden af den:
    restart-knap (cirkulær pil) der lægger alle patroner i tromlen igen.
- **Spillere**: navn + farve; hver spiller får én patron i sin farve i
  tromlen (maks 6), resten er tomme kamre. Udfald: 1/6 pr. kammer.
  12 farver: 8 støvede western-toner + 4 metaller (sølv, guld, jern,
  messing — sidstnævnte matcher patronernes egen brass-gradient).
- **Hold**: gem/indlæs/slet navngivne hold (localStorage). Redigér ved at
  indlæse, ændre spillerne og gemme under samme navn.
- **Spin-mekanik**: bang-lyd ved patron, klik-lyd ved tomt kammer.
  Resultat: spillerens navn i title case ("Tuco!") eller "Empty Chamber".
  Efter hvert spin to ikonknapper: fyldt kammer + gentag-pil = spin igen
  med alle patroner; tomt kammer + gentag-pil = fjern vinderens patron og
  spin igen. Tromlen zoomer automatisk smooth ud efter 3 sekunder;
  afbrydes timeren af et nyt spin, sker zoom-ud stadig glidende som del
  af overgangen (kamera-model: animationer starter altid fra aktuel
  viewBox og kan aldrig hoppe abrupt).
- **Default ved første opstart** (tom localStorage): spillerne Blondie
  (guld), Tuco (rust) og Sentenza (sort) + det gemte hold
  "The Good, the Bad & the Ugly".
- **Seneste tilstand gendannes** ved genåbning: spillerne inkl. deres
  aktiv-flag (fjernede patroner forbliver fjernet) og det sidst indlæste
  hold (vises i holdnavn-feltet). Alt i localStorage.

## Assets

| Fil | Oprindelse | Brug |
|---|---|---|
| `assets/BleedingCowboys.ttf` | Gallows Creek `fonts/` | Titel + resultat |
| `assets/OldNewspaperTypes.ttf` | Gallows Creek `fonts/` | Brødtekst, knapper, footer |
| `assets/paper.webp` | Gallows Creek `images/ui/` (pergament-baggrunden fra hjælp-modal/kampUI) | Side-baggrund |
| `assets/spin.mp3` | Gallows Creek `sounds/revolver/` | Tromle-spin |
| `assets/bang.mp3` | Tilføjet manuelt | Patron ramt (spilles ved landing) |
| `assets/klik.mp3` | Tilføjet manuelt (kilde: `387484__cosmicembers__...wav`) | Tomt kammer (spilles ved landing) |

## Android (APK)

WebView-wrapper-projektet ligger i `~/sixshooter-apk/` (udenfor dette repo):
app-navn "Six Shooter", package `dk.dustytales.sixshooter`, portrait-only,
fullscreen immersive, ingen internet-permission. `sixshooter.html` +
`assets/` kopieres ind som Android-assets ved build — kopiér dem ind igen
efter ændringer her, og byg med:

```
cd ~/sixshooter-apk && JAVA_HOME=~/jdk17 ./gradlew assembleDebug
```

Bemærk: WebView'en skal have `setDomStorageEnabled(true)` — localStorage
(hold + seneste tilstand) virker ellers ikke på `file://` i Android.

### Noter / mangler

- **Rye-fonten mangler.** Patronernes "Virtual Relic Ammunition"-stempel
  bruger `font-family="Rye,serif"`. Gallows Creek har heller ikke fonten
  (`fonts/` indeholder ingen Rye), så begge falder tilbage på serif.
  Hent evt. Rye-Regular.ttf (Google Fonts, OFL-licens) til `assets/`
  og tilføj en @font-face.
