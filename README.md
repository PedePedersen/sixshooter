# Six Shooter

Selvstændig HTML-app. Intet med Gallows Creek-spillet at gøre, men låner
visuelt DNA derfra (pergament, fonte, revolvertromle-animationen).

**Kør:** åbn `sixshooter.html` direkte i en browser — ingen server påkrævet.

## Funktioner

Bygget videre på Gallows Creek-legeværktøjet `iggy-alma-picker.html` —
tromle-animationen (4 sek spin + zoom på øverste kammer), spin-lyden og
pergament-stilen er bevaret. Ovenpå:

- **Spillere**: navn + farve; hver spiller får én patron i sin farve i
  tromlen (maks 6), resten er tomme kamre. Udfald: 1/6 pr. kammer.
- **Hold**: gem/indlæs/slet navngivne hold (localStorage). Redigér ved at
  indlæse, ændre spillerne og gemme under samme navn.
- **Spin-mekanik**: bang-lyd ved patron, klik-lyd ved tomt kammer. Efter
  hvert spin to ikonknapper: fyldt kammer + gentag-pil = spin igen med alle
  patroner; tomt kammer + gentag-pil = fjern vinderens patron og spin igen.
- **Mobil**: portrait-venlig, touch-targets ≥ 44 px, ingen hover-afhængighed.
  Standard-besætning ved første åbning: Iggy (grøn) & Alma (sort).

## Assets

| Fil | Oprindelse | Brug |
|---|---|---|
| `assets/BleedingCowboys.ttf` | Gallows Creek `fonts/` | Overskrifter + resultat |
| `assets/OldNewspaperTypes.ttf` | Gallows Creek `fonts/` | Brødtekst + knap |
| `assets/paper.webp` | Gallows Creek `images/ui/` (pergament-baggrunden fra hjælp-modal/kampUI) | Side-baggrund |
| `assets/spin.mp3` | Gallows Creek `sounds/revolver/` | Tromle-spin |
| `assets/bang.mp3` | Tilføjet manuelt | Patron ramt (spilles ved landing) |
| `assets/klik.mp3` | Tilføjet manuelt (kilde: `387484__cosmicembers__...wav`) | Tomt kammer (spilles ved landing) |

### Noter / mangler

- **Rye-fonten mangler.** Patronernes "Virtual Relic Ammunition"-stempel
  bruger `font-family="Rye,serif"`. Gallows Creek har heller ikke fonten
  (`fonts/` indeholder ingen Rye), så begge falder tilbage på serif.
  Hent evt. Rye-Regular.ttf (Google Fonts, OFL-licens) til `assets/`
  og tilføj en @font-face.
