

# Kommentarer til kravene

Det følgende er bare noen anbefalinger og kommentarer og ikke en beskrivelse av selve kravene. 

Det meste som står her er mulig å leses på DIFI sine nettsider. Noen av kravene er subjektive og andre er avhengig av spesiell kompetanse. Tilgjengelighet er vanskelig og gode intensjoner kan føre til at en *vennlig* løsning for en spesifikk gruppe ødelegger opplevelsen for andre. 

Noen av forslagene her er til spesifikke krav, mens andre er generelle forslag som bør vurderes.

---

# Mulig å oppfatte

## [1.1.1: Ikke tekstlig innhold](https://uu.difi.no/krav-og-regelverk/wcag-20-standarden/111-ikke-tekstlig-innhold-niva) {#111}

Alt innhold som ikke er tekst må tolkes av støttemidler som skjermlesere. Basert på kontekst og behov må man vurdere hvordan elementen skal oppleveles. Dekorative elementer eller elementer som ikke presenteres for brukere skal det implementeres slik at det blir ignorert av skjermlesere.

###Anbefalinger

* Alt-tekster skal beskrive funksjonen til bilde/elementet og vanligvis ikke være en beskrivelse å bilde i seg selv.
* Ikke start alt-tekst med "bilde av", dette leses opp av skjermleseren
* Alt-attributet er avhengig av kontekst. Hvis det samme bilde bruke to steder hvor det betyr forskjellige ting bør alt-teksten være forskjellig.
* Dekorative elementer skal ha et tomt alt-attribut
* Hvis et bilde også er en lenke burde lenketeksten være deskriptiv og erstatte behovet for alt-teksten til bildet
* Det er anbefalt å bruke en [.visually-hidden utility class i css](http://www.scottohara.me/blog/2017/04/14/inclusively-hidden.html) for å skjule innhold som alikevel kan nås av skjermlesere. Dette kan brukes for å gi kontekstuell informasjon til skjermlesere.
* Kontrollelementer som skjemafelter har navn som beskriver hva det er og gjør. Hvis det er mulig bruk et standard html element. Skjermlesere og andre støtteverktøy kjenner til vanlige html-elementer og kan gi korrekte instrukser.
Hvis man benytter et ukjent alternativ kan bruke [aria-roller](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/ARIA_Techniques)


---

## [1.2.1 Bare lyd og bare video](https://uu.difi.no/krav-og-regelverk/wcag-20-standarden/121-bare-lyd-og-bare-video-forhandsinnspilt-niva) og [1.2.2 Teksting (forhåndsinnspilt)](https://uu.difi.no/krav-og-regelverk/wcag-20-standarden/122-teksting-forhandsinnspilt-niva) {#121}

Informasjon skal være tilgjengelig for personer med hørsel og synsvansker. Det betyr at video bør tekstes og at innhold ikke bare finnes i lydformat. Media bør være tilgjengelig i tekst som en skjermleser kan nå. 

---

## [1.3.1 Informasjon og relasjoner](https://uu.difi.no/krav-og-regelverk/wcag-20-standarden/131-informasjon-og-relasjoner-niva) {#131}

> Ting skal være kodet som det ser ut som

Det beste er i blant det enkleste. Kravet er litt vagt men betyr i praksis at man følger html standarden og unngår å komplisere løsninger. Ikke finn opp kruttet. Presentasjonen av noe skal ikke påvirke det underliggende enkelhenten i html. Hvis noe ser ut som en liste bør det også være en liste i html.

###Anbefalinger

Vær varsom med tabeller :

* Forsøk å lage å enkle tabeller
* Tilgjengelige tabeller trenger caption og titler for rader og kolonner. Les mer om [tilgjengelige tabeller på the a11y project](https://a11yproject.com/posts/accessible-data-tables/)
* Vurder om tabell egentlig er det du trenger
* Splitt store tabeller i flere mindre tabeller om det er mulig å bevare informasjonen

Vær varsom med skjema:

* Bruk standardelementer

**La lenker være lenker og knapper være knapper** se [Marcy Sutton artikkel om forskjellen mellom lenker og knapper](https://marcysutton.com/links-vs-buttons-in-modern-web-applications/)

---

## [1.3.2 Meningsfylt rekkefølge](https://uu.difi.no/krav-og-regelverk/wcag-20-standarden/132-meningsfylt-rekkefolge-niva) {#132}

> Når rekkefølgen som innholdet presenteres i, påvirker meningsinnholdet, kan en korrekt leserekkefølge bestemmes programmeringsmessig.

Tabrekkefølge og opplesningen via skjermlesere skal stemme overens med det som presenteres visuelt. 

Dette skal testes manuelt ved å gå gjennom tabrekkefølgen og sjekke at innholdet leses opp med korrekt rekkefølge. Vanligvis er dette uproblematisk med god html.

###Anbefalinger

* Unngå å bruke tabindex = "1" eller høyere
* Velg om ting skal kunne nås med tabindex = "0" eller ikke nås med tabindex="-1". Mer om dette på [webaims sider om tabindex](https://webaim.org/techniques/keyboard/tabindex).

---

## [1.3.3 Sensoriske egenskaper](https://uu.difi.no/krav-og-regelverk/wcag-20-standarden/133-sensoriske-egenskaper-niva) {#133}

Grafiske symboler er sjeldent nok for å forstå innhold. Nielsen Norman groups forskning viser at [ikoner burde presenteres i sammenheng med tekst](https://www.nngroup.com/articles/icon-usability/). 

###Icon-fonts
Teknikker som å bruke unicode/icon-fonter for ikoner er også problematisk for skjermlesere. Dette skyldes at font-glyph symbolet blir opplest. Et eksempel er å bruke unicode u+2360 "☰" for en meny. Problemet er at det blir lest opp som "trigram for heaven" på engelsk. Hvis man bruker ikon-fonter må de overstyres ved hjelp av ARIA.

###Visuell plassering
Plassering på siden er ikke mulig å vite for de som bruker skjermlesere. God html med landmarks og regions kan gjøre det lettere å finne innhold. Men det bør ikke refereres til innhold basert på visuell-plassering, f.eks oppe til høyre. 

###Anbefalinger
* Bruk SVG-ikoner med alt-tekst for ikoner
* Ikke bruk hamburger-meny uten tekst som vises selv på mobil-størrelser
* Ikoner burde stå i sammenheng med en tekst

---

## [1.4.1 Bruk av farge (Nivå A)](https://uu.difi.no/krav-og-regelverk/wcag-20-standarden/141-bruk-av-farge-niva) , [1.4.3 Kontrast (minimum, Nivå AA)](https://uu.difi.no/krav-og-regelverk/wcag-20-standarden/143-kontrast-minimum-niva-aa) og [1.4.5 Bilder av tekst](https://uu.difi.no/krav-og-regelverk/wcag-20-standarden/145-bilder-av-tekst-niva-aa) {#141}

Farge skal ikke benyttes som det eneste visuelle virkemiddelet for å formidle informasjon. Kravet omhandler persepsjon av meningsbærende visuelt innhold. En god måte å teste dette på er å skru på svart/hvitt visning.

Tekst og bilder av tekst skal ha en kontrast som oppfyller AA-kravet. Dette innebærer at kontrastforholdet er minst 4.5, med unntak av stor skrift som skal ha minst kontrast på 3.0.

Uvesentlige elementer (dekorasjon) trenger ikke å oppnå kontrastkravet. Dette er subjektivt, men f.eks logoer, eller tekst i et illustrasjonsfoto.

###Anbefalinger

Tekst på bilder:

* Sjekk bakgrunner som tekst legges over
* Bruk teknikker som [scrim](https://material.io/guidelines/style/imagery.html#imagery-ui-integration) hvis det skal legges tekst på bilder
* Test tekst på bilder nøye, det er laveste kontrast som gjelder (unntak for visuell effekt)
* Unngå helst bilder av tekst, et eksempel på dette er tabellen med kravene øverst. Det er ikke god praksis :) 

Størrelse:

* Bruk stor skrift som utgangspunkt: 1 rem = 16 eller 18.
* Unngå å bruke liten skrift under 16px, eller fotnoter på 14px
    -   Designet burde ikke trenge liten skrift i det hele tatt

Farge på tekst:

* Unngå lys tekst med unntak av deaktivert/skjult tekst
* Bruk en mørk variant av svart for all tekst. For eksempel #222222 eller #333333 

---

## [1.4.4: Endring av tekststørrelse](https://uu.difi.no/krav-og-regelverk/wcag-20-standarden/144-endring-av-tekststorrelse-niva-aa) {#144}

>Tekst skal kunne endres til 200% størrelse uten tap av innhold eller funksjon

Websidene bør designes til å være responsive og kunne tåle en betraktelig endring med zoom.

### Anbefalinger
* Bruk relative enheter for størrelse på tekst
* Vurder å bruke relative enheter for å tillate at teksten i grensesnittet tar dobbelt så stor plass

---

## Mulig å betjene

## [2.1.1 Tastatur](https://uu.difi.no/krav-og-regelverk/wcag-20-standarden/211-tastatur-niva), [2.1.2 Ingen tastaturfelle](https://uu.difi.no/krav-og-regelverk/wcag-20-standarden/212-ingen-tastaturfelle-niva), og [2.4.3 Fokusrekkefølge](https://uu.difi.no/krav-og-regelverk/wcag-20-standarden/243-fokusrekkefolge-niva) {#211}

>All funksjonalitet skal kunne brukes kun ved hjelp av tastatur.

> Unngå tastaturfeller
 
>  Presenter innholdet i en logisk rekkefølge.

Krav 2.1.1-2 og 2.4.3 er omfattende og krever betydelig testing av nettsidene. Kravet gjør det viktig å forenkle, gjenbruke og teste elementer.

###Anbefalinger

* Bruk a11y støttede elementer og teknikker om mulig:
    -   [videavspillere](http://videojs.com/)
    -   datovelgere
* Kompliserte interaktive elementer bør testes
* Sjekk [ARIA dokumentasjonen](https://www.w3.org/TR/wai-aria-practices-1.1/#aria_ex) for deres anbefalinger for forskjellige elementer 

---

## [2.4.1 Hoppe over blokker](https://uu.difi.no/krav-og-regelverk/wcag-20-standarden/241-hoppe-over-blokker-niva) {#241}

> Gi brukeren mulighet til å hoppe direkte til hovedinnholdet.

Det enkleste kan være å bruke skip links som vises når man tabber inn i siden. Skip-linken hopper direkte til hovedinnholdet.

###Anbefalinger

* I html marker opp om hva slags del av siden vi er på. Se [aria-landmarks beskrivelsen](https://www.w3.org/TR/WCAG20-TECHS/ARIA11.html) for mer informasjon.
* Bruk [hopp til hovedinnhold lenker](https://webaim.org/techniques/skipnav/) på toppen av siden. Lenken trenger ikke å vises hele tiden men de må være synlig for de som navigerer med tastatur. 

---
 
## [2.4.2 Sidetitler](https://uu.difi.no/krav-og-regelverk/wcag-20-standarden/242-sidetitler-niva) {#242}

>Bruk nyttige og tydelig sidetitler

Alle websidene vi har bør ha sidetitler som gir en kjapp innsikt i hva siden inneholder. Det er ganske enkelt en tittel.

Det er den spesifikke siden som skal være en del av tittelen og ikke løsningens navn. En artikkel skal ha artikkelens tittel som sidetittel.

---

## [2.4.3 Fokusrekkefølge](https://uu.difi.no/krav-og-regelverk/wcag-20-standarden/243-fokusrekkefolge-niva) {#243}

>Presenter innholdet i en logisk rekkefølge

Navigeringssekvens bør være logisk både for de som navigerer med tastatur og de som navigerer med skjermleser. Som oftest vil de være DOM-strukturen som påvirker navigasjonen her. 

###Anbefalinger

* Unngå å hoppe over headinger i rekkefølgen. F.eks ikke hopp fra h1 til h3.
* Ha stålkontroll over dok-strukturen og hvordan den påvirker navigasjonen. 

---

## [2.4.4 Formål med lenke (i kontekst)](https://uu.difi.no/krav-og-regelverk/wcag-20-standarden/244-formal-med-lenke-i-kontekst-niva) {#244}

Alle lenkers mål og funksjon fremgår tydelig av lenketeksten.

Å skrive tekst til lenker er ikke lett, men det er ofte verd å ta ekstra tid for å forsikre at lenker er lette å skjønne og at det er lett å skjønne hva som er konsekvensen av å trykke på en lenke.

###Eksterne lenker

Heydon Pickering anbefaler å bruke en *selector* for *href* som vises til alle lenker til eksterne nettsider. Hvis jeg er på minside.no så:
```html
[href^="http"]:not([href*="minside.no"])
```

Kombinert med en pseudo-klasse og et svg ikon

```html
[href^="http"]:not([href*="minside])::after { display: inline-block;
width: 1em;
height: 1em;
background-image: url('path/to/external-icon.svg'); background-repeat: no-repeat;
background-position: center;
background-size: 75% auto;
}
```

###Anbefalinger

* Unngå tekster som pdf, les mer, klikk her på lenker
* Omformuler setninger slik at lenkene blir lettere å forstå
* Det bør også fremgå hvor lenker leder til enten med kontekst eller eksplisitt
* Bruk ARIA label for å gi kontekst til lenker om nødvendig

---

## [2.4.6 Overskrifter og ledetekster](https://uu.difi.no/krav-og-regelverk/wcag-20-standarden/246-overskrifter-og-ledetekster-niva-aa) og [3.3.2 Ledetekster eller instruksjoner](https://uu.difi.no/krav-og-regelverk/wcag-20-standarden/332-ledetekster-eller-instruksjoner-niva) {#246}

Titler, ledetekster skal være kontekstuelle og beskrive emne eller meningen.

Dette kravet er viktig for å utforme skjemaer og flyter som er lette å forstå og huske. Når man bruker en skjermleser er overskrifter og ledetekster helt sentrale for å danne en oppfatning av hva som forventes og kreves.

Restriksjoner, krav og annen sentralt informasjon bør kommuniseres til skjermleseren på riktig tidspunkt. Det betyr ikke at alt informasjon som presenteres visuelt må være med. 

###Anbefalinger

* Heydon Pickering anbefaler å bruke ARIA-describedby for å beskrive ledeteksten til et passordfelt. Det er mange alternative teknikker. Det viktigste er at teksten ikke bare er mulig å forstå hvis den er presentert visuelt
* Labelledby er også viktig om et felt ikke har en tittel

---

## [2.4.7 Synlig fokus](https://uu.difi.no/krav-og-regelverk/wcag-20-standarden/247-synlig-fokus-niva-aa) {#247}

>Sørg for at alt innhold får synlig fokus når du navigerer med tastatur.

At et element er i fokus må være synlig, enten ved å bruke nettleserstandarden eller en bedre versjon. Hvis man designer en egen løsning bør man ta høyde for at det er synlighet og ikke astestiske behov som har presendens her. Et godt eksempel på synlig fokus er [gov.uk retningslinjer for skjemafelter](https://govuk-elements.herokuapp.com/form-elements/#form-focus-states). Her brukes en sterk gulfarge som bakgrunn for fokuserbare elementer. For interaktive objekter får de en utvendig ramme i samme farge.

###Anbefalinger

Heydon Pickering anbefaler tre ting:

* Sjekk at elementet kan få *focus*
* Sjekk at elementet er synlig
* Sjekk at *fokus*-staten er synlig


---

## Forståelig

## [3.1.1 Språk på siden](https://uu.difi.no/krav-og-regelverk/wcag-20-standarden/311-sprak-pa-siden-niva), [3.1.2 Språk på deler av innhold](3.1.2 Språk på deler av innhold) {#311}

>Sørg for at språket til innholdet på alle websider er angitt i koden.

> Sørg for at alle deler av innholdet som er på et annet språk enn resten av siden er markert i koden.

Skjermlesere støtter flere språk, om en bruker har standard språk som norsk men også engelsk stemme installert vil skjermleseren bytte språk for innhold men ikke meta-informasjon som type felt.

---

##[3.2.2 Inndata](https://uu.difi.no/krav-og-regelverk/wcag-20-standarden/322-inndata-niva) {#322}

> Endring av verdien til et skjemafelt medfører ikke automatisk betydelige endringer i siden.

Automatikk som skjer uventet bør unngås. Det er derfor anbefalt å ha "submit" knapper for skjemaer. Felter som forsvinner og kommer frem er også problematisk for skjermlesere. Hvis en del av siden er "live" bør det brukes teknikker for å opplyse om dette til skjermlesere. Aria-live regions gjør det mulig å ha endringer på siden som opplyses. Et godt eksempel er (Mozilla sin artikkel om live-regions for en combo-box)[https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/ARIA_Live_Regions].

---

##[3.3.1 Identifikasjon av feil ](https://uu.difi.no/krav-og-regelverk/wcag-20-standarden/331-identifikasjon-av-feil-niva), [3.3.3 Forslag ved feil](https://uu.difi.no/krav-og-regelverk/wcag-20-standarden/333-forslag-ved-feil-niva-aa), og [3.3.4 Forhindring av feil (juridiske feil, økonomiske feil, datafeil)](https://uu.difi.no/krav-og-regelverk/wcag-20-standarden/334-forhindring-av-feil-juridiske-feil-okonomiske-feil-datafeil-niva-aa) {#331}

> For feil som oppdages automatisk må du vise hvor feilen har oppstått og gi en tekstbeskrivelse av feilen


Reverserbarhet: Innsending kan reverseres om mulig
Kontroll: Sjekk for feil i dataene som brukeren angir om mulig
Bekreftelse: Informasjon bør kunne gjennomgås, bekreftes og redigeres før informasjonen sendes inn.

###Anbefalinger

Interaktive elementer og brukerflyter må testes med skjermlesere. Det er et av de mer kompliserte stegene i å tilrettelegge for skjermlesere. Det anbefales å gjøre seg kjent med live-regions og 

* For meldinger som ikke skal avbryte flyt kan man gjøre som anbefalt i [w3 artikkel Live-regions og role=alert for feilmeldinger](https://www.w3.org/TR/WCAG20-TECHS/ARIA19.html)
* Legg til om et felt har blitt fylt feil for skjermleser[aria Invalid attribute](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/ARIA_Techniques/Using_the_aria-invalid_attribute)

For skjemafelter hvor valideringen sjekkes live bør de brukes en teknikk for å unngå å fyre validering ved hvert tastetrykk. Heydon Pickering anbefaler å bruke [LoDash.debounce "wait" parameter](https://lodash.com/docs/4.17.4#debounce) til å vente med å validere i f.eks 150 millisekunder etter siste tastetrykk.

´´´

´´´
---

