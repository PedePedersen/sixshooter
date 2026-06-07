# Six Shooter

Selvstændig HTML-app. Intet med Gallows Creek-spillet at gøre, men låner
visuelt DNA derfra (pergament, fonte, revolvertromle-animationen).

**Kør:** åbn `sixshooter.html` direkte i en browser — ingen server påkrævet.

## Udgangspunkt

`sixshooter.html` er en kopi af Gallows Creek-legeværktøjet
`iggy-alma-picker.html` (Iggy/Alma-tromle-picker, mobiloptimeret 9:21) med
asset-stierne omlagt fra indlejret base64 til filerne i `assets/`.
Al funktionalitet er bevaret: 2 grønne + 2 sorte patroner + 2 tomme kamre,
forudbestemt udfald (1/3 hver), 4 sek spin + zoom, spin-lyd, træk-igen.

## Assets

| Fil | Oprindelse | Brug |
|---|---|---|
| `assets/BleedingCowboys.ttf` | Gallows Creek `fonts/` | Overskrifter + resultat |
| `assets/OldNewspaperTypes.ttf` | Gallows Creek `fonts/` | Brødtekst + knap |
| `assets/paper.webp` | Gallows Creek `images/ui/` (pergament-baggrunden fra hjælp-modal/kampUI) | Side-baggrund |
| `assets/spin.mp3` | Gallows Creek `sounds/revolver/` | Tromle-spin |
| `assets/bang.wav` | **Genereret placeholder** (proceduralt: støj-burst + 70 Hz-krop, 0,5 s) | Patron ramt — endnu ikke koblet til i HTML'en |
| `assets/klik.wav` | **Genereret placeholder** (proceduralt: hane-klik + 2,2 kHz-ringen, 70 ms) | Tomt kammer — endnu ikke koblet til i HTML'en |

### Noter / mangler

- **Rye-fonten mangler.** Patronernes "Virtual Relic Ammunition"-stempel
  bruger `font-family="Rye,serif"`. Gallows Creek har heller ikke fonten
  (`fonts/` indeholder ingen Rye), så begge falder tilbage på serif.
  Hent evt. Rye-Regular.ttf (Google Fonts, OFL-licens) til `assets/`
  og tilføj en @font-face.
- **bang.wav/klik.wav er syntetiske placeholders** — Gallows Creeks
  lydbibliotek (bladre-lyde, spin, start-intro) havde ingen passende
  skud-/klik-lyde. Erstat dem gerne med rigtige optagelser.
