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
  "fund" bruges som fast begreb efter første, selvforklarende brug. Udadtil
  siges "alvorlige fund" (ikke det interne "høj alvor"), "uafhængig
  overvågning" (ikke "driftsmonitor") og "alvorsgrad" som feltnavn; undgå
  kancelli-vendinger og ordgentagelser (sprogpas 12. juli efter brugerens
  feedback om spøjst sprog).
- **Design:** fladt redaktionelt udtryk (ingen skygger/pills/hover-løft),
  Newsreader til overskrifter, IBM Plex Mono til etiketter og tal, lys/mørk
  via `prefers-color-scheme`. `og-image.png` (1200x630) er delekortet til
  LinkedIn m.m.; regenerér det hvis titel eller nøgletal ændres.
- **Identitet og kontakt (besluttet 12. juli 2026):** siden er starten på
  Jonathans portfolio. Topbar og `<title>` bærer navnet Jonathan Fribert;
  hero-eyebrow siger "Case 01" (flere cases kan komme til). Kontakt er
  fribert6@gmail.com (primær, synlig i CTA og footer) plus GitHub; bevidst
  ingen LinkedIn. Den foldbare teknikblok samler sprog, værktøjer, kilder,
  test og drift ét sted; døgnrytme-diagrammet i "Opgaven" viser overvågning
  24/7, levering kl. 8-17, natkø og hastemails.

## Historik

Bygget 12. juli 2026 i tre lag: Claude skrev første udgave (commit 313aa0b),
Codex redesignede til det nuværende flade udtryk med beslutningstræ og
takeaways, Claude bidrog med typografi-skala, sprogpas (jargon ud af
hovedsporet), og:image/delekort og publicering. 12. juli (senere samme dag):
det åbne designspørgsmål blev lukket ved at fjerne seks-trins-kørslen fra
"Løsningen" (den overlappede arkitekturdiagrammet); de to unikke detaljer
(X henter kun siden sidste kørsel; dedup på id/link/normaliseret titel) blev
flyttet ind i den tekniske foldeboks. Tankestreger i brødteksten blev erstattet
af kommaer (talintervaller som "kl. 8–17" og den ægte emnelinje med "—" er
bevidst beholdt). Senere samme dag, oprydningspas efter brugerens "siden ser
lidt rodet ud": beslutningstræet fjernet (dubleret af døgnrytme-diagrammet),
stats-labels og sektionsintroer forkortet, quick-head-sideteksten droppet, én
hero-CTA, h2/intro/quote skaleret ned, journey-kortene ensrettet til
accent/rød. Desuden GitHub profil-README oprettet (repo
JonathanFribert/JonathanFribert) med link hertil. Tredje pas: diskret
scroll-reveal (fade-op, staggered pr. søskendegruppe) og tragtsøjler/døgnbånd
der vokser frem ved indsyn; alt gated bag `.js-reveal` på `<html>` (sat af JS)
og `prefers-reduced-motion: no-preference`, så siden er fuldt synlig uden JS og
uden bevægelse for følsomme brugere. Plus ::selection i accentfarve. Fjerde pas: manuel lys/mørk-knap i topbaren.
Mekanik: uden valg følger siden systemet (media query); et klik sætter
`data-theme` på `<html>` og gemmer i localStorage (læses af et lille
head-script før første maling, så intet blink); vælges systemets eget tema,
ryddes valget, og siden følger systemet igen. Dark-variablerne findes derfor
BÅDE i media-queryen (gated med `:not([data-theme="light"])`) og duplikeret
under `[data-theme="dark"]` — hold de to blokke i sync ved farveændringer.
Knappen opdaterer også begge theme-color-metatags.

Femte pas samme dag: mobilnavigationen blev gjort ikke-scrollende med tre
synlige links og en separat 44 x 44 px temaknap. Figurtekster blev hævet til
mindst 14 px på mobil, scrollindikatoren blev fjernet, og scroll-reveal blev
begrænset til fem hovedfigurer uden stagger. Den dobbelte teknikforklaring blev
samlet i én foldbar blok, driftslaget i arkitekturfiguren blev forkortet, og
projektstatus, mailadfærd, auditlog og økonomi blev beskrevet mere præcist.
