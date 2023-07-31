# Bootcamp Workshop i React

Denne Workshoppen er for deg som kan grunnleggende HTML og CSS fra før, og som vil lære deg React og alt det kule rammeverket har å by på.

## Ressurser
[Dokumentasjonen til React](https://react.dev/reference/react)

## Emoji-guide

Du kommer til å se noen emojis i oppgavene. Disse betyr:

- 🏆 Oppgave: Her er hva du skal gjøre.
- 💡 Tips: Litt ekstra info som kan være greit å ha for å løse en oppgave.
- 🚨 Løsningsforslag: Her finner du et eksempel på hvordan du _kan_ løse oppgaven.

## Oppsett

- Klon repoet
    - gå i terminalen din og skriv `git clone git@github.com:bekk/bootcamp-react-ws.git`
- Naviger deg inn i mappa som heter `bootcamp-react-ws` ved å skrive dette i terminalen din: `cd bootcamp-react-ws`.
- Skriv `npm install` for å installere nødvendige avhengigheter for prosjektet.
- Deretter skriver du `npm run dev` for å starte opp nettsiden.

## Oppgaver

I denne workshoppen skal du lage deg din egen personlige bloggside 🎉. Vi skal ta for oss steg for steg hvordan man bygger opp en React-applikasjon, men du har alltid friheten til å gjøre din egen vri på oppgavene!

### Oppgave 1 - komponenter, props og children

La oss begynne med basic setup av React komponenter og et par andre vanlige ting i React.

Gå inn i `App.jsx`-komponenten inne i `src`-mappa, og fjern all koden som er mellom `<>...</>` inne i `return()`-funksjonen – la oss begynne å lagge denne nettsiden mer personalisert til deg og den du er!

🏆 1.1 – I `App.jsx`, returner `Blog`-komponeten som allerede er importert i fila. `Blog.jsx` ligger inne i mappa som heter `Oppgave 1`.

💡 Det er en grei huskeregel at DOM-komponenter starter med liten forbokstav, og React-komponenter starter med Stor forbokstav. `<div />` er med andre ord et HTML-element, mens `<Blog />` er en referanse til Blog-funksjonen vi vil bruke.

🏆 1.2 – Få `Blog.jsx` til å returnere et heading-element med innholdet "MittNavns blogg". Refresh nettsiden slik at du ser resultatet av kodeendringen. 

🏆 1.3 – I samme fil, lag en `Title`-komponent som returnerer heading-elementet ditt som du skrev i forrige deloppgave. Bruk Title-komponenten din inne i Blog-komponenten.

🏆 1.4 – Lag en ny fil i Oppgave1-mappa som du navngir `Title.jsx`. Kopier Title komponenten du laget i forrige oppgave inn til Title.jsx fila og eksporter den slik at den kan brukes i andre komponenter. Importer Title komponenten i `Blog.jsx` og slett samtidig Title definisjonen fra `Blog.jsx`.

💡 I React kan man eksportere komponenter fra en fil, les om `default` og `named`-exports [her](https://react.dev/learn/importing-and-exporting-components#challenges).

🏆 1.5 – I stedet for å hardkode navnet ditt i komponenten, gjør om Title-komponenten din til å ta inn en prop som heter `name`. Da kan du sende inn navnet ditt i Blog.jsx der du bruker Title.jsx

💡 Props kan hete akkurat hva du vil, og kan være akkurat den datastrukturen du vil at den skal være. Les mer om props [her](https://react.dev/learn/passing-props-to-a-component#step-1-pass-props-to-the-child-component).

🏆 1.6 – Inne i Title.jsx, legg til className-prop ‘title’ på h1-elementet. Gå i `App.css` så kan du style komponenten din slik du vil den skal se ut i `.title` selektoren

💡 Ikke vært så mye borti CSS? Les mer om CSS [her](https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web/CSS_basics).

🏆 1.7 – Bonus: Importer `Confetti`-komponenten og bruk den i Blog-komponenten din 🎉

✨ Endre farger, størrelser, spacing, osv slik du vil 💅

<details>
<summary>🚨 Løsningsforslag</summary>

```
// I Title.jsx
export default function Title({ name }) {
    return (
        <h1 className="title">{name}s blogg</h1>
    )
}

// I Blog.jsx
return (
    <>
        <Title name="Caroline" />
    </>
)
```
</details>

### Oppgave 2 - lister og events

I denne oppgava skal vi se litt på dynamisk innhold og rendring av komponenter. 

I `Blog.jsx`, kommenter inn Facts-funksjonen som ligger øverst i fila, og bruk denne under Title-komponenten din i render-funksjonen.

Åpne `Facts.jsx` som ligger i mappa som heter `Oppgave 2`. Her finnes det allerede en liste med tekster som vises, men vi må manuelt legge til hvert element ved bruk av index, f.eks med `facts[0]` som vil vise det første elementet i lista. Vi viser heller ikke alle elementene i lista. Denne løsningen skalerer dårlig. Vi vil derfor skrive om innholdet i `Facts.jsx` til å iterere gjennom hvert element i `facts`-lista dynamisk. La oss gjøre det steg for steg:

🏆 2.1 – Fjern de hardkoda faktaene i renderfunksjonen til `Facts.jsx`, og løp gjennom hvert element i lista og returner et `<li>` element for hvert fakta-element i lista.

💡 Det finnes flere liste-operasjoner i JavaScript, `.map` løper gjennom hvert element i lista og du kan bestemme hva hvert element skal mappes om til. Les mer [her](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map).

💡 Du vil gå en warning i konsollen at hvert element i lista trenger en unik identifikator, dette gjøres ved å bruke attributtet `key` på hvert element.

🏆 2.2 – Det blir litt masete å ha all koden i en fil så la oss dele det opp litt. Gå inn i `Card.jsx`-fila og gjør den om til å returnere et listeelement. Komponenten kan ta inn en prop som f.eks. heter `fact`. Bruk denne komponenten inne i `Facts.jsx` hvor du sender inn hvert fakta inn som prop til komponenten i `.map`. <em>Her kan du legge til `card` som `className` på Card-komponenten.</em>

🏆 2.3 – Card-komponenten kan gjøres mer dynamisk, så i stedet for å bruke en prop ønsker vi nå at den heller skal ta inn `children`. Fjern `fact`-prop'en og ta heller inn `children` som du bruker inne i Card-komponenten. Gjør om bruken i `Facts.jsx`-komponenten til å sende inn hver fakta som children i stedet for props. 

💡 `children` er en fin måte å sette sammen flere komponenter på en dynamisk måte, ved å bruke children så "wrapper" man en komponenten rundt en annen komponent. Les mer om children [her](https://react.dev/learn/passing-props-to-a-component#passing-jsx-as-children).

✨ Legg inn fakta om deg selv i stedet, og style card-komponenten slik du vil med andre farger og animasjoner 💅

<details>
<summary>🚨 Løsningsforslag</summary>

```
// I Facts.jsx

function Facts() {
    return {
        <>
            <h2>Fakta om kjendiser</h2>
            {facts.map((fact) => {
                return (
                    <Card key={fact}>{fact}</Card>
                )
            })}
        </>
    }
}

// I Card.jsx
function Card({ children }) {
    return (
        <li className="card">{children}</li>
    )
}
```
</details>


### Oppgave 3 - useState og conditional rendering

Nå skal vi gjøre nettsiden litt mer interaktiv!

I `Blog.jsx`, kommenter inn CoverPhoto-funksjonen som ligger øverst i fila, og bruk denne under Title-komponenten din i render-funksjonen.

🏆 3.1 – Gå inn i mappa som heter `Oppgave3` og åpne `CoverPhoto.jsx` – Få denne komponenten til å returnere bildet som har stien `"/src/assets/img1.jpg"`. <em>Gi komponenten klassenavnet `"cover-photo"`</em>.

💡 Her kan du bruke `<img>`-element for å vise et bilde.

🏆 3.2 – Gjør det mulig for brukeren å trykke på bildet, i første omgang kan du skriv noe til konsollen når brukeren trykker på bildet.

💡 Du kan wrappe `<img>`-taggen i en `<button>`.

💡 For å logge til konsollen kan du bruke `console.log('din tekst her')`, og for å se konsollen kan du høyre-klikke og trykke på "inspiser" eller "inspect" på nettsiden.

💡 Les mer om events [her](https://react.dev/learn/responding-to-events).

🏆 3.3 – Vi har lyst til å vise et annet bilde når brukeren trykker på bildet – så i stedet for å console.logge trenger vi nå å vite om brukeren har trykket på bildet eller ikke. Lag en `useState` som har verdien `showFirstPicture` og som har en funksjon som heter `setShowFirstPicture`.

💡 useState returnerer alltid en liste på formatet `const [verdi, setVerdi] = useState()`, og du kan kalle disse verdiene hva du vil. 

💡 Vi bestemmer om det skal være bolske verdier, tall eller tekst som verdien i useState'en skal ha, i dette tilfellet trenger vi bare en bolsk verdi som forteller om vi skal vise det første bildet eller ikke. Default-verdien kan derfor være `true` første gangen nettsiden blir lastet. 

💡 Les om useState [her](https://react.dev/reference/react/useState).

🏆 3.4 – Endre slik at når brukeren trykker på bildet så skal setShowFirstPicture oppdatere verdien til showFirstPicture til å være det motsatte. <em>Altså hvis showFirstPicture er true så skal den nye verdien bli false, og motsatt.</em>

🏆 3.5 –I render-funksjonen kan du nå sjekke på verdien `showFirstPicture` og vise bilde 1 eller bilde 2 avhengig om brukeren har trykket på bildet eller ikke.

💡 Dette kalles conditional rendering og ser slik ut: `condition ? ifConditionIsTrue : ifConditionIsFalse`

✨ Legg inn bilde av deg selv eller av en hobby eller noe annet du liker, og style nettsiden slik du vil 💅


<details>
<summary>🚨 Løsningsforslag</summary>

```
// I CoverPhoto.jsx

import { useState } from 'react'

export default function CoverPhoto() {
    const [showFirstPicture, setShowFirstPicture] = useState(true)

    const onButtonClick = () => {
        setShowFirstPicture(!showFirstPicture)
    }

    return (
        <button onClick={onButtonClick}>
            <div className="cover-photo">

            {
                showFirstPicture
                    ? <img src={`/src/assets/img1.jpg`} alt="picture of coffee"/>
                    : <img src={`/src/assets/img2.jpg`} alt="picture of person and a candle"/>
            }
            </div>
        </button>
    )
}
```
</details>

### Oppgave 4 - useEffect og datahenting

Nå skal nettsiden endelig begynne å kommunisere med verden, for nå skal vi nemlig hente litt data! Vi skal vise kollektiv-avganger fra et stoppested som man kan trenge å vite før man forlater hjemmet sitt. La oss ta for oss dette steg for seg.

I `Blog.jsx`, kommenter inn DepartureBoard-funksjonen som ligger øverst i fila, og bruk denne under Title-komponenten din i render-funksjonen.

🏆 4.1 – Skriv en useEffect inne i `DepartureBoard.jsx` som ligger i `Oppgave4`-mappa. Som en oppvarmingsoppgave kan du begynne med å console-logge en vilkårlig tekst til konsollen når komponenten mountes.

💡 Her er dependency-arrayet til useEffect'en viktig. Hvis man dropper lista vil useEffect kjøres på hver render, har man en tom liste vil det si at det som er i useEffect'en bare skal kjøres når komponenten mountes, og en liste med verdier trigger bare useEffevten bare når verdiene i lista får en oppdatert verdi.

💡 OPS! Komponenten din vil mountes 2 ganger i developer mode 🙃 – så useEffect som bare skal kjøres på mount vil bli utført to ganger. Forvirrende greier! Grunnen er at React vil stressteste komponenten din. 

🏆 4.2 – I stedet for å console-logge til konsollen, kan du nå skrive en async funksjon inne i useEffecten som heter `fetchData` som kaller `fetchDepartures` som er en ferdiglaget funksjon som henter noe data <em>(du trenger ikke bry deg om innholdet i denne funksjonen)</em>. Du kan begynne med å console-logge dataen du får tilbake for å se at nettverkskallet fungerer. Husk å kalle fetchData inne i useEffecten din.

<details>
<summary>💡 Et vanlig oppsett av en useEffect som henter data</summary>

```
useEffect(() => {
    const fetchData = async () => {
        ...
    }

    const data = await fetchData()
}, [])
```
</details>

<details>
<summary>💡 Funksjonen `fetchDepartures` henter data fra Entur sine API'er, og returnerer data på dette formatet:</summary>

    {
        stopPlace: string // Navnet på stoppestedet,
        departures: Array<{
            frontText: string, // hva strekningen heter
            departureTime: string, // avgangstidspunkt
        }>
    }
</details>

💡 Les om henting av data med useEffects [her](https://react.dev/reference/react/useEffect#fetching-data-with-effects)

🏆 4.3 – Lag to states i komponenten din, en som tar seg av tittelen på stoppestedet, et annet som lagrer alle avgangene.

💡 De kan f.eks hete `[title, setTitle]` og `[departures, setDepartures]`.

🏆 4.4 – I useEffecten etter du har henta data fra endepunktet så kan du bruke de to set-funksjonene du fikk av useState til å oppdatere verdien til `title` og `departures`.

<details>
<summary>💡 I JavaScript kan du destrukrutere objekter</summary>

```
const { stopPlace, departures } = data
```
</details>

🏆 4.5 – Rendre tittel og avgangsinformasjonen. <em>Her kan du legge til `departures` som `className` på `<ul>`-taggen rundt avgangene, og `departure` på hvert `<li>`-element. Her kan du også legge til et clockImage som et bilde for hver avgang for å gjøre det mer visuelt.</em>

✨ Hent informasjon om et stoppested du kjenner til! 💅
- Gå på https://entur.no/kart.
- Skriv inn et stoppested du kjenner til. 
- Gå i url'en på nettsiden og kopierer id'en som begynner på `NSR:`, f.eks `NSR:StopPlace:58801`.
- Gå i client.js på linje 12 og erstatt den id'en med din egen id for å hente avganger for ditt stoppested!

<details>
<summary>🚨 Løsningsforslag</summary>

```
import { useState, useEffect } from 'react'

import clockIcon from '../assets/Clock.svg'

import { fetchDepartures } from '../client'

export default function DepartureBoard() {
    const [title, setTitle] = useState('...')
    const [departures, setDepartures] = useState([])

  useEffect(() => {
    const fetchData = async () => {
      const { stopPlace, departures } = await fetchDepartures()
      setTitle(stopPlace)
      setDepartures(departures)
    }
    fetchData()
  }, [])

  return (
    <>
      <h2>Avganger fra {title}</h2>
      <ul className="departures">
      {departures.map(({ frontText, departureTime}) => {
        return (
            <li className="departure" key={`${frontText}${departureTime}`}>
              <img src={clockIcon} />
              {frontText} kl. {departureTime}
            </li>
        )
      })}
      </ul>
    </>
  )
}
```
</details>

### Oppgave 5 - Bonusoppgaver

Hva! Har du kommet så langt allerede?! Da har jeg noen bonusoppgaver til deg! Du kan velge mellom disse oppgavene:

🏆 Personaliser bloggsiden din enda mer!

Er det noe mer informasjon eller komponenter som mangler? Slå deg løs!

🏆 Lag en bildekarusell

I stedet for å klikke på bildet for å endre det så kan du lage en karusell der brukeren kan bla seg gjennom bilder.
- Hvis du trenger bilder kan du bruke https://unsplash.com/.

🏆 Datahenting

Lyst til å leke mer med datahenting? Det er brukt GraphQL for å hente data fra Entur sitt JourneyPlanner API i oppgave 4. Sjekk ut [dokumentasjonen på API'et](https://api.entur.io/graphql-explorer/journey-planner-v3?query=%23%20Avgangstavle%20-%20Stavanger%20stadion%0A%0A%7B%0A%20%20stopPlace%28id%3A%20%22NSR%3AStopPlace%3A548%22%29%20%7B%0A%20%20%20%20id%0A%20%20%20%20name%0A%20%20%20%20estimatedCalls%28timeRange%3A%2072100%2C%20numberOfDepartures%3A%2010%29%20%7B%20%20%20%20%20%0A%20%20%20%20%20%20realtime%0A%20%20%20%20%20%20aimedArrivalTime%0A%20%20%20%20%20%20aimedDepartureTime%0A%20%20%20%20%20%20expectedArrivalTime%0A%20%20%20%20%20%20expectedDepartureTime%0A%20%20%20%20%20%20actualArrivalTime%0A%20%20%20%20%20%20actualDepartureTime%0A%20%20%20%20%20%20date%0A%20%20%20%20%20%20forBoarding%0A%20%20%20%20%20%20forAlighting%0A%20%20%20%20%20%20destinationDisplay%20%7B%0A%20%20%20%20%20%20%20%20frontText%0A%20%20%20%20%20%20%7D%0A%20%20%20%20%20%20quay%20%7B%0A%20%20%20%20%20%20%20%20id%0A%20%20%20%20%20%20%7D%0A%20%20%20%20%20%20serviceJourney%20%7B%0A%20%20%20%20%20%20%20%20journeyPattern%20%7B%0A%20%20%20%20%20%20%20%20%20%20line%20%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20id%0A%20%20%20%20%20%20%20%20%20%20%20%20name%0A%20%20%20%20%20%20%20%20%20%20%20%20transportMode%0A%20%20%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%20%20%7D%0A%20%20%20%20%7D%0A%20%20%7D%0A%7D%0A) og se om du kan hente og vise mer nyttig data for et stoppested!

🏆 Context

Bruk [React Context](https://react.dev/learn/passing-data-deeply-with-context) til å lage dark-mode på siden din når brukeren trykker på en knapp. 
- Hint: Bruk CSS-variabler.

