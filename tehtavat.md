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

Arviointikriteerit

| Arviointikohta              | Kuvaus                                                         |
| --------------------------- | -------------------------------------------------------------- |
| **Tekninen toimivuus**      | Projekti käynnistyy, React- ja Firebase-osat toimivat          |
| **Koodin rakenne**          | Selkeät komponentit, ei turhaa logiikkaa renderissä            |
| **Local Storage -logiikka** | Uusi ja vanha koodinimi käsitellään oikein                     |
| **Firebase Authentication** | Google‑kirjautuminen toimii ja käyttäjätiedot näkyvät          |
# 🎓 **Palautettava materiaali**

Palautuksena tehtävästä on Teams-kanavalle **GitHub-repositorion linkki** ja **GitHub Pages -sivuston linkki**, jossa on Vite-sovellus toimivana

##

### 5. Tehtävä
TBD
##

### 6. Tehtävä
TBD
##