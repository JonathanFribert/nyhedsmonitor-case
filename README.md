# Case-side: Nyhedsmonitor (portfolio)

Offentlig portfolio-side om nyhedsmonitor-projektet, målrettet fremtidige
arbejdsgivere. Én selvstændig HTML-fil, ingen build-trin.

**Live:** https://jonathanfribert.github.io/nyhedsmonitor-case/
**Hosting:** GitHub Pages fra det offentlige repo `JonathanFribert/nyhedsmonitor-case`
(branch `main`, rod). Selve monitorens kildekode ligger i det PRIVATE repo
`JonathanFribert/nyhedsmonitor` og skal forblive privat.

## Publicering (efter ændringer i index.html)

```
git add -A && git commit -m "beskrivelse"
git push origin main        # remote = det offentlige nyhedsmonitor-case-repo
```

Pages bygger automatisk ved push (typisk live inden for 1-2 min). Verificér:
`curl -sI https://jonathanfribert.github.io/nyhedsmonitor-case/ | head -1`

## Indhold og principper

- **Sandfærdighed er sidens valuta.** Alle tal stammer fra rigtige kørsler og
  logs (tragten: produktionskørslen 7. juli kl. 16.25; pålidelighed: målingen
  8.-11. juli). Det konstruerede journey-eksempel er eksplicit markeret som
  illustrativt. Lav ALDRIG tal eller citater om uden at opdatere kilden.
- **Statsministeriet nævnes bevidst** (hero, case-brief) med en tydelig
  disclaimer om, at værktøjet er personlig støtte, ikke et officielt system.
  Ingen modtagernavne eller mailadresser må optræde på siden.
- **Sprogniveau:** hovedsporet skrives til en ikke-teknisk læser; tekniske
  detaljer bor i den foldbare "Se præcis, hvad der sker teknisk". Terminologi:
  "fund" bruges som fast begreb efter første, selvforklarende brug.
- **Design:** fladt redaktionelt udtryk (ingen skygger/pills/hover-løft),
  Newsreader til overskrifter, IBM Plex Mono til etiketter og tal, lys/mørk
  via `prefers-color-scheme`. `og-image.png` (1200x630) er delekortet til
  LinkedIn m.m.; regenerér det hvis titel eller nøgletal ændres.

## Historik

Bygget 12. juli 2026 i tre lag: Claude skrev første udgave (commit 313aa0b),
Codex redesignede til det nuværende flade udtryk med beslutningstræ og
takeaways, Claude bidrog med typografi-skala, sprogpas (jargon ud af
hovedsporet), og:image/delekort og publicering. Kendt åbent designspørgsmål:
sektionen "Løsningen" viser både en seks-trins kørsel OG et arkitekturdiagram,
delvist overlappende; kan slankes hvis siden stadig føles tæt.
