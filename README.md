# Nyhedsmonitor — projektcase

**Læs casen her: https://jonathanfribert.github.io/nyhedsmonitor-case/**

[![Delekort for casen](og-image.png)](https://jonathanfribert.github.io/nyhedsmonitor-case/)

Et personligt værktøj til nyhedsovervågning, bygget og sat i drift på fem dage
til en medarbejder i Statsministeriet under en uge på standby. Casen gennemgår
arkitektur, test og drift med faktiske driftstal. Selve monitorens kildekode er
privat, fordi værktøjet blev bygget til en konkret arbejdsopgave.

Kontakt: fribert6@gmail.com

---

## Intern dokumentation (for redigering af siden)

Dette repo indeholder casens ene HTML-fil og delekortet; resten af denne
README er arbejdsdokumentation. Én selvstændig HTML-fil, ingen build-trin.

**Hosting:** GitHub Pages fra dette repo (branch `main`, rod). Selve
monitorens kildekode ligger i det PRIVATE repo `JonathanFribert/nyhedsmonitor`
og skal forblive privat.

## Publicering (efter ændringer i index.html)

```
git add -A && git commit -m "beskrivelse"
git push origin main        # remote = det offentlige nyhedsmonitor-case-repo
```

Pages bygger automatisk ved push (typisk live inden for 1-2 min). Verificér:
`curl -sI https://jonathanfribert.github.io/nyhedsmonitor-case/ | head -1`

OBS (set 13. juli 2026): Pages-konfigurationen kan forsvinde fra repoet, så
siden svarer 404, selv om push lykkes og koden er på main. Tjek med
`gh api repos/JonathanFribert/nyhedsmonitor-case/pages` og genaktivér med:
`gh api -X POST repos/JonathanFribert/nyhedsmonitor-case/pages -f "source[branch]=main" -f "source[path]=/"`

## Indhold og principper

- **Sandfærdighed er sidens valuta.** Alle tal stammer fra rigtige kørsler og
  logs (tragten: produktionskørslen 7. juli kl. 16.25; pålidelighed: målingen
  8.-11. juli). Det konstruerede journey-eksempel er eksplicit markeret som
  illustrativt. Lav ALDRIG tal eller citater om uden at opdatere kilden.
- **Statsministeriet nævnes bevidst** (hero, case-brief) med en tydelig
  disclaimer om, at værktøjet er personlig støtte, ikke et officielt system.
  Ingen modtagernavne eller mailadresser må optræde på siden.
- **Sprogniveau:** hovedsporet skrives til en ikke-teknisk læser; tekniske
  detaljer bor i den foldbare "Se de tekniske detaljer". Terminologi:
  "fund" bruges som fast begreb efter første, selvforklarende brug. Udadtil
  siges "alvorlige fund" (ikke det interne "høj alvor"), "uafhængig
  overvågning" (ikke "driftsmonitor") og "alvorsgrad" som feltnavn; undgå
  kancelli-vendinger og ordgentagelser (sprogpas 12. juli efter brugerens
  feedback om spøjst sprog).
  De synlige emnelinjer er forenklede, læsevenlige eksempler. De bevarer
  rækkefølgen af alvorsgrad, antal fund og driftsstatus, men gengiver ikke de
  oprindelige forkortelser ordret.
- **Design ("Morgenavisen", besluttet 13. juli 2026):** fladt redaktionelt
  udtryk uden skygger/pills/hover-løft, nu i avis-palet: varmt papir #FAF7F0,
  blæk #1B1A17, avisblå accent #1F4E79, rustrød #A6301F KUN som alarmfarve,
  grøn #2F6B44 til levering (mørk tilstand: kul #141210, blæk #ECE7DC, lys
  avisblå #8FB4D9 — findes i TO CSS-blokke, der skal holdes i sync).
  Identitetsmotiv: avishoved med udgavelinje og klassisk dobbeltstreg (tyk
  over tynd) øverst; samme dobbeltstreg lukker siden over footeren.
  Sektionslabels er nummererede (01–08) i mono. Newsreader til overskrifter,
  IBM Plex Mono til etiketter og tal, lys/mørk via `prefers-color-scheme` +
  manuel knap. Alle tekst/baggrund-par er kontrolleret mod WCAG AA.
  `og-image.png` (1200x630) er delekortet til LinkedIn m.m.; den redigerbare
  kilde er `og-template.html` (bruger sidens rigtige skrifter Newsreader og
  IBM Plex Mono via Google Fonts; et tidligere SVG-udkast udgik, fordi det
  faldt tilbage på Georgia/Menlo). Regenerér PNG-filen, hvis titel, nøgletal
  eller palet ændres:

  ```sh
  "/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" --headless \
    --screenshot=og-image.png --window-size=1200,630 --hide-scrollbars \
    --virtual-time-budget=8000 "file://$PWD/og-template.html"
  ```
- **Identitet og kontakt (besluttet 12. juli 2026):** siden er starten på
  Jonathans portfolio. Topbar og `<title>` bærer navnet Jonathan Fribert;
  hero-eyebrow siger "Projektcase". Kontakt er
  fribert6@gmail.com (primær, synlig i CTA og footer) plus GitHub; bevidst
  ingen LinkedIn. Den foldbare teknikblok samler sprog, værktøjer, kilder,
  test og drift ét sted; døgnrytme-diagrammet i "Opgaven" viser overvågning
  24/7, levering kl. 8-17, fund gemt til morgenmailen og hastemails.

## Historik

Bygget 12. juli 2026 i tre lag: Claude skrev første udgave (commit 313aa0b),
Codex redesignede til det nuværende flade udtryk med beslutningstræ og
takeaways, Claude bidrog med typografi-skala, sprogpas (jargon ud af
hovedsporet), og-image/delekort og publicering. 12. juli (senere samme dag):
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

13. juli 2026, "Morgenavisen"-redesign (Claude, efter brugerens valg af
retning): (A) avis-paletten ovenfor erstattede den kølige teal-palet i begge
temaer; theme-color, favicon, print og JS-tema-synk fulgte med; alle tekstpar
kontrastkontrolleret. (B) hero omkomponeret som avishoved (udgavelinje +
dobbeltstreg, eyebrow-elementet udgik), sektionslabels nummereret 01–08 i
mono, footer fik samme dobbeltstreg. (C) figursprog ensrettet: mail-mock med
avisblå toplinje, figurtitler med ens underlinje, tragt i avisblå med rød
slutrække. (D) og-image regenereret i avis-stil med den aktuelle rubrik.
Codex' sprogpas fra samme formiddag blev committet separat forinden og er
fuldt bevaret.

13. juli: Et samlet sprogpas gjorde nøgletallene til hele sætninger, oversatte
interne driftsord i hovedsporet og omskrev driftsfejlenes løsningsbeskrivelser.
Tekniske begreber blev enten forklaret eller flyttet til teknikfolden. De
mindste diagramtekster blev samtidig gjort større på desktop.

Et afsluttende læsbarhedspas erstattede de rå, forkortede emnelinjer med tydeligt
markerede eksempler og ændrede blandt andet "fravalg", "samme kørsel" og
"systemet set ovenfra" til mere almindeligt dansk.
