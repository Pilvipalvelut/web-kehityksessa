## Kurssin tehtävät

Arviointi: oppimistehtävät 60 % ja oma soveltava harjoitustyö 40 %.

Kurssilla on 7 oppimistehtävää, yksi tehtävä / lähiopetusviikko ja jokaisen viikon tehtävä palautetaan seuraavan viikon tunteihin mennessä. Tehtävien palautuspäivämäärä on kuluvan viikon sunnuntai klo 22. Myöhässä oppimistehtäviä voi palauttaa, mutta niistä vähennetään pisteitä kaavalla 10% vähennystä / viikko. Joidenkin tehtävien kohdalla käymme tehtävän haasteellisia kohtia läpi seuraavalla tunnilla ja opintojakson päätteeksi myös mallivastaukset tulevat näkyville. Yhdestä oppimistehtävästä saa max 6 p.  Yhteensä siis 7 x 6 p = 42 p.

Harjoitustyöstä saa parhaimmillaan 30 p ja se palautetaan opintojakson loppuun mennessä.

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
- Siirry repositoryn asetuksiin _Settings_, jossa määritellään GitHub Pages-sivuston asetukset. Ks. [kuva1](https://github.com/Pilvipalvelut/web-kehityksessa/blob/main/gh_pages1.png)
- Valitse _Settings_-sivun vasemmasta valikosta _Code and automation_ ja _Pages_-välilehti. Välilehdeltä voidaan merkitä julkaistavaksi _main_ branch, joka on ns. default kehityshaara repositoryssa. Ks. [kuva2](https://github.com/Pilvipalvelut/web-kehityksessa/blob/main/gh_pages2.png)
- Kun asetus on oikein tehty sivusto on näkyvillä ja linkki sivustoon tulee _Settings_-sivulle näkyviin
- Tarkista toisella selaimella tai incognito-tilassa miltä sivusto näyttää muille käyttäjille. Sivusto on osoitteessa: https://kayttajanimi.github.io/repositoryn-nimi


### 2. Tehtävä
Muunna GitHub Pages -sivustosi niin että HTML-sivujen sijaan käytetään md-tiedostoja ja Jekyll-teemaa. Saat lisää tietoa Jekyll-teemojen käyttämisestä [täältä](https://github.com/Pilvipalvelut/web-kehityksessa/blob/main/jekyll.md)

Jekyll-teemoja voi etsiä osoitteista
- [GitHub Themes](https://pages.github.com/themes/)
- [Jekyll Themes](https://jekyll-themes.com/)


### 3. Tehtävä
1. Tee luentomateriaalin ohjeiden  mukainen Firebase-tietokanta ja konfiguraatio sovelluksen käyttämiseksi. 
2. Tee Vite tai React-sovellus paikalliselle koneelle komentorivillä.
- Ohje Vite-sovelluksen muodostamiseta löytyy [täältä](https://vitejs.dev/guide/)
- Ohje React-sovelluksen muodostamisesta löytyy [täältä](https://create-react-app.dev/docs/getting-started)
3. Asenna Firabase-tools paketti paikallisen koneen komentorivillä. Ohjeita voi katsoa [täältä](https://firebase.google.com/docs/cli)
4. Konfiguroi 2. kohdassa tehty sovellus käyttämään Firestore-tietokantaa

Palautuksena Teams:iin kuvankaappaus selaimesta kun Vite + React -sovellus on saatu omalla koneella käyntiin.

### 4. Tehtävä
TBD

### 5. Tehtävä
TBD

### 6. Tehtävä
TBD

### 7. Tehtävä
TBD
