## Kurssin tehtävät

Arviointi: oppimistehtävät 51 % ja oma soveltava harjoitustyö 49 %.

Kurssilla on 6 oppimistehtävää, yksi tehtävä / opetusviikko ja jokaisen viikon tehtävän palautuspäivämäärä on kuluvan viikon sunnuntai klo 22. Myöhässä oppimistehtäviä voi palauttaa, mutta niistä vähennetään pisteitä kaavalla 10% vähennystä / viikko. Joidenkin tehtävien kohdalla käymme tehtävän haasteellisia kohtia läpi seuraavalla tunnilla ja opintojakson päätteeksi myös mallivastaukset tulevat näkyville. Yhdestä oppimistehtävästä saa max 6 p.  Yhteensä siis 6 x 6 p = 36 p.

[Harjoitustyöstä](https://github.com/Pilvipalvelut/web-kehityksessa/blob/main/harjoitustyo.md) saa parhaimmillaan 34 p ja se palautetaan opintojakson loppuun mennessä 17.5. klo 22.

##

### 1. Tehtävä

GitHub pages -sivuston rakentaminen

#### 1.1. Rekisteröidy GitHub:in käyttäjäksi
- Mene selaimella osoitteeseen: [GitHub Signup](https://github.com/signup)
- Täytä rekisteröitymistiedot lomakkeella
- Lue käyttöehdot ja hyväksy
- GitHub lähettää sähköpostilla vahvistusviestin, jossa on linkki johon täytyy mennä vahvistaaksesi että antamasi sähköpostiosoite on todellinen

#### 1.2. Luo uusi repository 
- Kirjaudu GitHub-tilillesi osoitteessa [GitHub](https://github.com)
- Siirry omalle profiilisivullesi oikeassa yläkulmassa olevasta profiili-ikonista
- Valitse Repositories-välilehti
- Paina Repositories-välilehdellä _New_-painiketta
- Täytä tiedot uudesta repositorysta
- Voit alkuun pitää repositorya Private-näkyvyystilassa kunnes se on valmis. Opintojakson aikana repositoryn tulee kuitenkin olla Public-näkyvyydellä

#### 1.3. Luo sivustolle uusi HTML-sivu
- Siirry repositoryn juureen eli avaa selaimella tyhjä repository
- Paina repositryn juuressa _Create new file_-painiketta
- Nimeä tiedosto nimellä _index.html_, joka on aloitussivun nimi
- Lisää tiedostoon tarvittavat sisällöt, esimerkiksi:
~~~
<!DOCTYPE html>
<html>
<head>
    <title>GitHub Pages Sivuni</title>
</head>
<body>
    <h1>Tervetuloa GitHub Pages-sivustolleni!</h1>
    <p class="container">Tämä on ensimmäinen GitHub Pages -teksti.</p>
</body>
</html>
~~~

#### 1.4. Luo sivustolle CSS-tiedosto, johon viittaat HTML-sivuista
- Tee samaan tapaan kuin edellisessä kohdassa uusi tiedosto
- Nimeä tiedosto nimellä _styles.css_ ja laita tarvittavat sisällöt, esimerkiksi:
~~~
body {
    background-color: #d2e2f2;
    font-family: Roboto, sans-serif;
}

h1 {
    color: #333;
}

.container {
    max-width: 960px;
    margin: 0 auto;
}
~~~
- Tallenna CSS-tiedosto
- Tee muutos HTML-sivulle, jotta määrittämäsi tyylitiedosto tulee käyttöön
~~~
<head>
    <link rel="stylesheet" type="text/css" href="styles.css">
</head>
~~~
#### 1.5. Muuta repository asetuksia
- Siirry repositoryn asetuksiin _Settings_, jossa määritellään GitHub Pages-sivuston asetukset. Ks. ![GitHub asetukset](gh_pages1.png)
- Valitse _Settings_-sivun vasemmasta valikosta _Code and automation_ ja _Pages_-välilehti. Välilehdeltä voidaan merkitä julkaistavaksi _main_ branch, joka on ns. default kehityshaara repositoryssa. Ks. ![Julkaistavan haaran valinta](gh_pages2.png)
- Kun asetus on oikein tehty sivusto on näkyvillä ja linkki sivustoon tulee _Settings_-sivulle näkyviin
- Tarkista toisella selaimella tai incognito-tilassa miltä sivusto näyttää muille käyttäjille. Sivusto on osoitteessa: https://kayttajanimi.github.io/repositoryn-nimi

#### 1.6. Linkkilista etusivulla jokaisen viikon tehtäväsivulle
- Tee aloitussivulle (index) lista linkeistä, joilla pääsee tutustumaan tehtävä palautuksiin.
![Esimerkki tehtävälistauksesta](gh_pages3.png)
##

### 2. Koodikielen ja suunnittelumallien automaattinen tunnistus GitHub Actionsilla

🎯 **Oppimistavoitteet**

Tämän tehtävän suoritettuaan opiskelija osaa:

*   Rakentaa GitHub Actions -workflow ja konfiguroida sen ajastuksen ja/tai tapahtumatriggerin mukaan
*   Kirjoittaa skriptin, joka analysoi GitHub-repositorion sisältöä
*   Tunnistaa koodin ohjelmointikielen (tai kielet)
*   Etsiä yleisiä suunnittelumalleja (design patterns) koodista
*   Tuottaa analyysin workflow’n lokiin ja mahdollisesti artefaktiksi

## 📝 **Tehtävän kuvaus**

Luo GitHub-repositorioon automaattinen analysointijärjestelmä, joka:

1.  **Tunnistaa repositoriossa käytetyt ohjelmointikielet**
2.  **Tarkistaa, esiintyykö koodissa klassisia ohjelmistosuunnittelun malleja**  
    (esim. Singleton, Factory Method, Strategy, Observer, Decorator)
3.  **Tulostaa analyysiraportin** GitHub Actions -workflow’n lokiin  
    – ja valinnaisesti tallentaa sen artefaktiksi.

# 🛠️ **Tekniset vaatimukset**

2.1. GitHub Actions -workflow

Luo hakemistoon `.github/workflows/` tiedosto nimeltä esimerkiksi `analysis.yml`, joka:

*   Ajoitetaan suoritettavaksi aina kun koodia viedään (`push`) tai tehdään `pull_request`
*   Suorittaa opiskelijan kirjoittaman analyysiskriptin

Esimerkki workflow-runnerista (opiskelijat muokkaavat itse tarpeidensa mukaan):

```yaml
name: Repository Analysis

on:
  push:
  pull_request:

jobs:
  analyze:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout repository
        uses: actions/checkout@v4

      - name: Run analysis script
        run: |
          chmod +x analysoi.sh
          ./analysoi.sh

      - name: Upload report
        uses: actions/upload-artifact@v4
        with:
          name: analysis-report
          path: analysis_report.txt
```

2.2. Analyysiskripti

Tee repositorioon tiedosto `analysoi.sh` (tai `analysoi.py`), joka selvittää repositoryssa käytetyt ohjelmointikielet (esim. `.py`, `.js`, `.java`, `.ts` jne.)

Esimerkki yksinkertaisesta shell-tavasta:

```bash
echo "Detected languages:"
find . -type f -name "*.py" | grep -q . && echo "- Python"
find . -type f -name "*.java" | grep -q . && echo "- Java"
find . -type f -name "*.js" | grep -q . && echo "- JavaScript"
find . -type f -name "*.ts" | grep -q . && echo "- TypeScript"
```

### Havaitsee yleisiä suunnittelumalleja

Tuloksen ei tarvitse olla täydellinen, tavoitteena on **heuristiikkapohjainen** tunnistus.

Esimerkki heuristiikoista:

| Suunnittelumalli | Heuristiikka                                                          |
| ---------------- | --------------------------------------------------------------------- |
| Singleton        | Tiedosto sisältää sanan `getInstance` tai `static instance`           |
| Factory Method   | Esiintyy `create*` tai `factory`                                      |
| Strategy         | Luokkanimi *Strategy* tai hakusana `interface` tietyissä tiedostoissa |
| Observer         | Esiintyy sanat `notify`, `subscribe`, `observer`                      |
| Decorator        | Luokkanimissä esiintyy *Decorator*, tai “wrap”-tyyppisiä metodeja     |

Esimerkki shell-heuristiikasta:

```bash
echo "Design patterns detected:" > analysis_report.txt

grep -R "getInstance" -n . && echo "- Singleton" >> analysis_report.txt
grep -R "create[A-Z]" -n . && echo "- Factory Method" >> analysis_report.txt
grep -R "notify" -n . && echo "- Observer" >> analysis_report.txt
grep -R "Strategy" -n . && echo "- Strategy" >> analysis_report.txt
grep -R "Decorator" -n . && echo "- Decorator" >> analysis_report.txt
```

Raportin voi myös generoida markdown-muotoon.

2.3. Raportointi

*   Raportti tulostetaan GitHub Actions -lokiin
*   Raportti tallennetaan tiedostoon `analysis_report.txt` kohdan 2.2. mukaisesti
*   Tiedosto tallennetaan artefaktiksi ja laitetaan viikon 2 linkiksi. Linkin löytää GitHub Actions -lokin lopusta kohdasta (tämä linkin lisääminen on vapaaehtoinen ja sitä ei arvioida)
```
Artifact download URL: https://github.com/{oma_tunnus}/{oma_repo}/actions/runs/23796709182/artifacts/6198870044
```

# 🎓 **Palautettava materiaali**

Palautuksena tehtävästä on Teams-kanavalle **GitHub-repositorion linkki**, jossa on workflow-tiedosto `.github/workflows/analysis.yml`

##

### 3. Tehtävä Vite + React -sovellus Local Storagella

## ✅ Oppimistavoitteet

Opiskelija osaa:

*   Luoda Vite-pohjaisen React-projektin
*   Rakentaa käyttöliittymäkomponentteja modernilla Reactilla
*   Tallentaa ja noutaa dataa Local Storagesta

## 📘 Tehtävänanto

3.1. Projektin luominen

Luo uusi React-projekti käyttäen Viteä:

```bash
npm create vite@latest [Oman-projektin-nimi]
```

Asenna riippuvuudet:

```bash
npm install
```

3.2. Sovelluksen toiminnallinen idea

Tee pieni sovellus, joka:

1.  **Generoi käyttäjälle hauskan koodinimen** (esim. *SneakyPanda42*).
2.  **Tallentaa tämän koodinimen Local Storageen.**
3.  **Kun käyttäjä kirjautuu sisään**, sovellus:
    *   hakee Local Storagesta käyttäjän aiemmin luodun koodinimen (jos olemassa)
    *   jos koodinimeä ei ole, generoi uuden ja tallentaa sen
4.  Näyttää kirjautuneelle käyttäjälle:
    *   sovelluksen generoiman koodinimen

3.3. Koodinimen generointi

Toteuta funktio, joka luo satunnaisen ja hauskan koodinimen.

Esimerkkitoteutus:

```js
function generateCodename() {
  const adjectives = ["Sneaky", "Electric", "Silent", "Hyper", "Cosmic"];
  const animals = ["Fox", "Panda", "Lizard", "Dragon", "Hawk"];
  const number = Math.floor(Math.random() * 3000);

  const adj = adjectives[Math.floor(Math.random() * adjectives.length)];
  const animal = animals[Math.floor(Math.random() * animals.length)];

  return `${adj}${animal}${number}`;
}
```

3.4. Local Storage ‑tallennus

Sovelluksessa tulee olla seuraavat ominaisuudet:

*   Koodinimen tallentaminen Local Storageen:
    ```js
    localStorage.setItem("codename", codename);
    ```
*   Koodinimen hakeminen Local Storagesta:
    ```js
    const cachedName = localStorage.getItem("codename");
    ```

# 🎓 **Palautettava materiaali**

Palautuksena tehtävästä on Teams-kanavalle **GitHub-repositorion linkki**, jossa on Vite-sovellus nähtävissä

##

### 4. Tehtävä Firebase‑projektin luominen

### Firebase Console

1.  Mene osoitteeseen **<https://console.firebase.google.com>**
2.  Valitse **Create project**
3.  Anna projektille nimi (esim. `vite-pilvi`)
4.  Ota Google Analytics **pois päältä**
5.  Luo projekti

✅ Tässä vaiheessa Firebase‑projekti on olemassa, mutta mitään palveluja ei ole vielä käytössä.

4.1. Web‑sovelluksen rekisteröinti Firebaseen

Firebase tarvitsee tiedon siitä, että projektia käytetään **web‑sovelluksesta**.

1.  Firebase Consolessa:
    *   Project Overview → **Add app**
    *   Valitse **Web (\</>)**
2.  Anna sovellukselle nimi (esim. `websovellus`)
3.  Firebase näyttää konfiguraation:

```ts
const firebaseConfig = {
  apiKey: "…",
  authDomain: "…",
  projectId: "…",
  messagingSenderId: "…",
  appId: "…"
};
```

👉 **Tämä konfiguraatio tarvitaan React‑sovelluksessa.**

4.2. Google‑kirjautumisen aktivointi Firebase Authissa

### Autentikaation käyttöönotto

1.  Firebase Console → **Build → Authentication**
2.  Valitse **Get started**

### Kirjautumistavan lisääminen

1.  Authentication → **Sign‑in method**
2.  Valitse **Add new provider**
3.  Valitse **Email/Password**
4.  Vaihda kytkimestä **Enable**
5.  Save

✅ Firebase osaa nyt tunnistaa Google‑käyttäjiä. Tee uusi käyttäjä välilehdellä Users.

4.3. Vite + React ‑sovelluksen luonti (Jos sitä ei ole tehnyt 3. tehtävässä)

Komentorivillä:

```bash
npm create vite@latest [Oman-projektin-nimi]
cd [Oman-projektin-nimi]
npm install
npm run dev
```

4.4. Firebase‑kirjastojen asentaminen

Reactissa käytetään Firebase **SDK:ta**, uusin on versio 12. Aja komentorivillä projektin juurikansiossa:

```bash
npm install firebase
```

4.5. Firebase‑konfiguraation eriyttäminen

Tiedostorakenne (esimerkki)

```txt
src/
 ├─ App.tsx
 └─ main.tsx
 └─ LoginForm.ts
 └─ authService.ts

firebaseConfig.ts
.env
```

Tiedostossa `firebaseConfig.ts` otetaan käyttöön Firebasesta saadut konfiguraatiot:

```ts
const firebaseConfig = {
  apiKey: import.meta.env.VITE_FIREBASE_API_KEY,
  authDomain: import.meta.env.VITE_FIREBASE_AUTH_DOMAIN,
  projectId: import.meta.env.VITE_FIREBASE_PROJECT_ID,
  messagingSenderId: import.meta.env.VITE_FIREBASE_MESSAGING_ID,
  appId: import.meta.env.VITE_FIREBASE_APP_ID,
};

export default firebaseConfig;
```

4.6. Ympäristömuuttujat

`.env` -tiedoston luonti projektin juureen

```env
VITE_FIREBASE_API_KEY=xxxx
VITE_FIREBASE_AUTH_DOMAIN=xxxx
VITE_FIREBASE_PROJECT_ID=xxxx
VITE_FIREBASE_MESSAGING_ID=xxxx
VITE_FIREBASE_APP_ID=xxxx
```

🔹 Vite vaatii `VITE_`‑etuliitteen  
🔹 `.env` -tiedostoa **ei viedä** versionhallintaan. Sen voi laittaa tiedoksi `.gitignore` -tiedostoon.

4.7. Google‑kirjautumisen ohjelmallinen toteutus

Toteuta `src/authService.ts` -palvelu

```ts
import {
  getAuth,
  signInWithEmailAndPassword,
  createUserWithEmailAndPassword,
  signOut,
  User,
  UserCredential
} from "firebase/auth";
import { initializeApp } from "firebase/app";
import firebaseConfig from "../firebaseConfig";

const app = initializeApp(firebaseConfig);
export const auth = getAuth(app);
/**
 * Kirjautuminen sähköposti + salasana
 */
export const loginWithEmail = async (
  email: string,
  password: string
): Promise<User> => {
  const result: UserCredential = await signInWithEmailAndPassword(
    auth,
    email,
    password
  );
  return result.user;
};

/**
 * Käyttäjän rekisteröinti (Ei tässä tehtävässä välttämätön)
 */
export const registerWithEmail = async (
  email: string,
  password: string
): Promise<User> => {
  const result: UserCredential = await createUserWithEmailAndPassword(
    auth,
    email,
    password
  );
  return result.user;
};

/**
 * Kirjautuminen ulos
 */
export const logout = async (): Promise<void> => {
  await signOut(auth);
};
```

4.8. Kirjautumislomake (React + TypeScript)

Toteuta `src/LoginForm.tsx` -lomake

```tsx
import { useState } from "react";
import { loginWithEmail } from "./authService";

const LoginForm = () => {
  const [email, setEmail] = useState<string>("");
  const [password, setPassword] = useState<string>("");
  const [error, setError] = useState<string | null>(null);
  const [loading, setLoading] = useState<boolean>(false);

  const handleSubmit = async (e: React.FormEvent) => {
    e.preventDefault();
    setError(null);
    setLoading(true);

    try {
      await loginWithEmail(email, password);
    } catch (err: unknown) {
      if (err instanceof Error) {
        setError(err.message);
      } else {
        setError("Tuntematon virhe");
      }
    } finally {
      setLoading(false);
    }
  };

  return (
    <form onSubmit={handleSubmit}>
      <h2>Kirjaudu sisään</h2>

      <div>
        <label>Sähköposti</label>
        <input
          type="email"
          value={email}
          onChange={(e) => setEmail(e.target.value)}
          required
        />
      </div>

      <div>
        <label>Salasana</label>
        <input
          type="password"
          value={password}
          onChange={(e) => setPassword(e.target.value)}
          required
        />
      </div>

      {error && <p style={{ color: "red" }}>{error}</p>}

      <button type="submit" disabled={loading}>
        {loading ? "Kirjaudutaan..." : "Kirjaudu"}
      </button>
    </form>
  );
};

export default LoginForm;
```

4.9. Lomakkeen liittäminen App‑komponenttiin

Firebase ylläpitää käyttäjän tilaa **automaattisesti**, mutta React tarvitsee kuuntelijan.
`onAuthStateChanged` voidaan laittaa vaikka `src/App.tsx` -tiedostoon seuraavasti: 

```tsx
import { useEffect, useState } from "react";
import { onAuthStateChanged, User } from "firebase/auth";
import LoginForm from "./LoginForm";
import { auth, logout } from "./authService";

function App() {
  const [user, setUser] = useState<User | null>(null);

  useEffect(() => {
    const unsubscribe = onAuthStateChanged(auth, (firebaseUser) => {
      setUser(firebaseUser);
    });

    return () => unsubscribe();
  }, []);

  return (

    // Paljon muuta renderöitävää

    <div>
      {user ? (
        <>
          <p>👋 Tervetuloa, {user.email}</p>
          <button onClick={logout}>Kirjaudu ulos</button>
        </>
      ) : (
        <LoginForm />
      )}
    </div>
  );

  // Paljon muuta koodia

}

export default App;
```

4.10. Koodinimen hakeminen Local Storagesta

Muuta vielä `src/App.tsx` -tiedostoa niin että kun käyttäjä kirjautuu Firebase Authilla sisään, sovellus hakee tai luo käyttäjälle uniikin koodinimen Local Storagesta käyttäen Firebase UID:tä avaimena ja näyttää sen kohdassa
```Tervetuloa, {codename}```


Arviointikriteerit

| Arviointikohta              | Kuvaus                                                         |
| --------------------------- | -------------------------------------------------------------- |
| **Tekninen toimivuus**      | Projekti käynnistyy, React- ja Firebase-osat toimivat          |
| **Koodin rakenne**          | Selkeät komponentit, ei turhaa logiikkaa renderissä            |
| **Local Storage -logiikka** | Käyttäjän koodinimi käsitellään oikein                         |
| **Firebase Authentication** | Firebase‑kirjautuminen toimii ja käyttäjätiedot näkyvät        |
# 🎓 **Palautettava materiaali**

Palautuksena tehtävästä on Teams-kanavalle **GitHub-repositorion linkki** ja **GitHub Pages -sivuston linkki**, jossa on Vite-sovellus toimivana

##

### 5. Tehtävä Moninpelinä toimiva hintavisa (Vite + React + Firebase)
Voit jatkaa edellisessä tehtävissä aloitettua React + Vite ‑projektia, jossa on
Firebase Authentication (email + password)
Lisänä tulisi peruskomponentit:
*   QuizForm (arvaus)
*   RoundResult (kierroksen tulos)
*   App.tsx, joka yhdistää nämä

Tehtäväsi on laajentaa tästä toimiva 2–4 pelaajan moninpelipeli, jossa arvataan tuotteiden hintoja.

`src/App.tsx` – sovelluksen orkestroija:
*   hoitaa **Firebase Authenticationin**
*   luo **yksittäisen pelisession** (`createSession`)
*   välittää funktiota `submitGuess`
*   renderöi `QuizForm`‑komponentin

📌 Tämä tiedosto on hyvä **lähtöpiste**.
```ts
import { useState, useEffect } from 'react'
import reactLogo from './assets/react.svg'
import viteLogo from './assets/vite.svg'
import heroImg from './assets/hero.png'
import './App.css'
import LoginForm from './LoginForm';
import { auth, logout } from './authService';
import { onAuthStateChanged, type User } from 'firebase/auth';
import { getOrCreateCodename } from './codenameService';
import { QuizForm } from './components/QuizForm';
import { createSession } from './gameSessionService';
import { resolveRound } from './gameController';
import { type Session } from './types/Session';

function App() {
  const [count, setCount] = useState(0);
  const [session, setSession] = useState<Session | null>(null);
  const [codename, setCodename] = useState<string>("");
  const [user, setUser] = useState<User | null>(null);

  // Initialize count from localStorage on mount
  useEffect(() => {
    const storedCount = localStorage.getItem('laskuri');
    if (storedCount) {
      setCount(parseInt(storedCount, 10));
    }

    const unsubscribe = onAuthStateChanged(auth, async (firebaseUser) => {
      setUser(firebaseUser);
      const name = getOrCreateCodename(firebaseUser!.uid);
      setCodename(name);
      setSession(await createSession({ name: name + "n-arvaussessio", creatorName: name }));
    });

    return () => unsubscribe();   
  }, [])

  const handleClick = () => {
    setCount((count) => {
      localStorage.setItem('laskuri', "" + (++count));

      return count;
    })
  }

  function submitGuess(guess: number): void {
    if ( session ) {
      try {
        resolveRound(session, guess);
      } catch (error) {
        console.error("Kierroksen luonti epäonnistui: ", error);
      }  
    }
  }

  return (
    <>
      <section id="center">
        <div className="hero">
          <img src={heroImg} className="base" width="170" height="179" alt="" />
          <img src={reactLogo} className="framework" alt="React logo" />
          <img src={viteLogo} className="vite" alt="Vite logo" />
        </div>
        <div>
          <h1>Heippa maailma!</h1>
          <p>
            Edit <code>src/App.tsx</code> and save to test <code>HMR</code>
          </p>
        </div>
        <button
          className="counter"
          onClick={handleClick}
        >
          Count is {count}
        </button>
        <div>
          {user ? (
            <>
              <p>👋 Tervetuloa, {codename}</p>
              <button onClick={logout}>Kirjaudu ulos</button>
            </>
          ) : (
            <LoginForm />
          )}
        </div>

        <div>
          <QuizForm 
            onSubmitGuess={(guess) => submitGuess(guess)} 
            players={[]} 
            currentUserId={codename}
          />
        </div>
      </section>

      <div className="ticks"></div>

      <section id="next-steps">
        <div id="docs">
          <svg className="icon" role="presentation" aria-hidden="true">
            <use href="/icons.svg#documentation-icon"></use>
          </svg>
          <h2>Documentation</h2>
          <p>Your questions, answered</p>
          <ul>
            <li>
              <a href="https://vite.dev/" target="_blank">
                <img className="logo" src={viteLogo} alt="" />
                Explore Vite
              </a>
            </li>
            <li>
              <a href="https://react.dev/" target="_blank">
                <img className="button-icon" src={reactLogo} alt="" />
                Learn more
              </a>
            </li>
          </ul>
        </div>
        <div id="social">
          <svg className="icon" role="presentation" aria-hidden="true">
            <use href="/icons.svg#social-icon"></use>
          </svg>
          <h2>Connect with us</h2>
          <p>Join the Vite community</p>
          <ul>
            <li>
              <a href="https://github.com/vitejs/vite" target="_blank">
                <svg
                  className="button-icon"
                  role="presentation"
                  aria-hidden="true"
                >
                  <use href="/icons.svg#github-icon"></use>
                </svg>
                GitHub
              </a>
            </li>
            <li>
              <a href="https://chat.vite.dev/" target="_blank">
                <svg
                  className="button-icon"
                  role="presentation"
                  aria-hidden="true"
                >
                  <use href="/icons.svg#discord-icon"></use>
                </svg>
                Discord
              </a>
            </li>
            <li>
              <a href="https://x.com/vite_js" target="_blank">
                <svg
                  className="button-icon"
                  role="presentation"
                  aria-hidden="true"
                >
                  <use href="/icons.svg#x-icon"></use>
                </svg>
                X.com
              </a>
            </li>
            <li>
              <a href="https://bsky.app/profile/vite.dev" target="_blank">
                <svg
                  className="button-icon"
                  role="presentation"
                  aria-hidden="true"
                >
                  <use href="/icons.svg#bluesky-icon"></use>
                </svg>
                Bluesky
              </a>
            </li>
          </ul>
        </div>
      </section>

      <div className="ticks"></div>
      <section id="spacer"></section>
    </>
  )
}

export default App

```

`src/components/QuizForm.tsx` – arvauslomake:
*   sisältää lomakkeen hinnan arvaamiseen
*   käyttää `useState` vain paikalliseen inputtiin
*   kutsuu `onSubmitGuess`

Puuttuu:

*   tuotteen tiedot (vain nimi, ei kuvaa)
*   pelin vaiheiden selkeä käsittely (`guessing` vs `resolved`)

```ts
import { useState } from 'react';
import { type Player } from '../types/Player';
import { RoundResult} from './RoundResult';


interface QuizFormProps {
  players: Player[];
  currentUserId: string;
  correctPrice?: number;        // olemassa vain tulosvaiheessa
  onSubmitGuess: (guess: number) => void;
}

export function QuizForm({
  players,
  currentUserId,
  correctPrice,
  onSubmitGuess
}: QuizFormProps ) {
    
  const [guess, setGuess] = useState("");

  if (correctPrice !== undefined) {
    return (
      <RoundResult
        players={players}
        correctPrice={correctPrice}
      />
    );
  }


    return (
        <><p>Arvattavan tuotteen nimi: </p>
        <form
            onSubmit={e => {
                e.preventDefault();
                onSubmitGuess(Number(guess));
            } }
        >

            <input
                type="number"
                value={guess}
                onChange={e => setGuess(e.target.value)}
                placeholder="Arvaa hinta (€)"
                required />

            <button>Arvaa hinta {currentUserId}</button>
        </form></>
    );
}

export default QuizForm;
```

`src/components/RoundResult.tsx` – kierroksen tulos näyttää:
*   näyttää:
    *   oikean hinnan
    *   kaikkien pelaajien arvaukset ja erot
*   se on puhdas presentaatio
*   ei Firestorea
*   ei React‑statea
```ts
import { type Player } from "../types/Player";

export function RoundResult({
  players,
  correctPrice,
}: {
  players: Player[];
  correctPrice: number;
}) {
  return (
    <div>
      <h3>Kierroksen tulos</h3>

      <p>Oikea hinta: {correctPrice} €</p>

      <ul>
        {players.map(p => (
          <li key={p.id}>
            {p.codename}: {p.guess} €
            (ero {Math.abs(p.guess! - correctPrice)} €)
          </li>
        ))}
      </ul>
    </div>
  );
}
```

5.1: Pelin tietomallit 

👉 Luo TypeScript‑tyypit:

*   `Player`
*   `Game` tai `Session`

Vähimmäisvaatimukset:

```ts
Player:
- uid / codename
- score
- guess

Game / Session:
- status ("waiting" | "playing" | "finished")
- players: Player[]
- currentRound
- correctPrice?
```

📌 **Huom:**  
Firestore EI salli `undefined`‑arvoja – huomioi tämä tietomallissa.

5.2. Firestore‑integraatio

Toteuta Firestore‑logiikka erillisiin tiedostoihin (ei React‑komponentteihin):

*   ✅ pelin luonti
*   ✅ pelin tallennus
*   ✅ pelin haku
*   ✅ reaaliaikainen kuuntelu (`onSnapshot`)

Vaatimus:

*   peli päivittyy samanaikaisesti kaikille pelaajille

5.3. Pelin elinkaaren hallinta

Rakenna peli vaiheisiin:

1.  **Waiting**
    *   pelaajat liittyvät
    *   peli ei ala ennen kuin vähintään 2 pelaajaa

2.  **Guessing**
    *   näytetään tuotteen nimi (ja halutessa kuva)
    *   `QuizForm` aktiivinen

3.  **Finished**
    *   voittaja näytetään

📌 Tämä voidaan toteuttaa:

*   `status`‑kentällä
*   tai yksinkertaisella tilakoneella
```ts
export type SessionStatus = "waiting" | "playing" | "finished";

export type Session = {
    id: string;
    sessionName: string;
    scores: Record<string, number>; // playerId -> score
    currentRound: number;
    currentGame?: string;
    status: SessionStatus;
    createdAt: unknown;
    createdBy: unknown;
    lastActivity?: unknown;
};
```

5.4. Ulkoinen rajapinta (DummyJSON)

Hae jokaiselle kierrokselle:

*   satunnainen tuote osoitteesta  
    👉 <https://dummyjson.com/products>

```ts
async function fetchRandomProduct() {
    const res = await fetch("https://dummyjson.com/products");
    const data = await res.json();

    const products = data.products;
    const randomIndex = Math.floor(Math.random() * products.length);
    const product: Product = products[randomIndex];
    return product;
}
```

Vaatimukset:

*   tuotteen hintaa ei näytetä ennen kierroksen ratkaisua
*   hinta tallennetaan Firestoreen


5.5: Pisteytys

Esimerkiksi:

*   lähin arvaus voittaa
*   tai: `score += max(0, 100 - |arvaus - oikea hinta|)`

| Komponentti         | Rooli tehtävässä               |
| ------------------- | ------------------------------ |
| `App.tsx`           | Orkestroi auth + nykyinen peli |
| `QuizForm`          | Arvausvaihe                    |
| `RoundResult`       | Kierroksen tulos               |
| Firestore‑tiedostot | Pelilogiikka                   |
| Custom hookit       | Reaaliaikaisuus                |

📌 


# 🎓 **Palautettava materiaali**

Palautuksena tehtävästä on Teams-kanavalle **GitHub-repositorion linkki** ja **GitHub Pages -sivuston linkki**, jossa on Vite-sovellus toimivana

##

### 6. Tehtävä
TBD
##