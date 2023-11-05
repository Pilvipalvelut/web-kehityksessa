## Autentikointi
Autentikointi tai tutummin tunnistautuminen on prosessi, jonka avulla käyttäjät voivat todistaa henkilöllisyytensä ja osoittaa, että heillä on lupa käyttää tiettyjä sovelluksen resursseja tai toimintoja. Autentikointi on olennainen osa verkkosovelluksia ja verkkopalveluita, ja se auttaa suojaamaan käyttäjien tietoja ja varmistamaan, että vain oikeilla henkilöillä on pääsy tiettyihin resursseihin.

Autentikointiprosessi sisältää seuraavat vaiheet:

1. **Käyttäjätunnistus:** Käyttäjä antaa käyttäjätunnuksensa (yleensä sähköpostiosoitteen) ja salasanan, joka liittyy tiliin. Käyttäjätunnuksen ja salasanan yhdistelmää käytetään yleisimmin käyttäjän tunnistamiseen.

2. **Todentaminen:** Sovellus tarkistaa onko annettu käyttäjätunnus ja salasana oikeat. Jos ne täsmäävät, käyttäjä on onnistuneesti tunnistettu.

### Kaksivaiheinen tunnistautuminen
Kaksivaiheinen tunnistautuminen (2FA tai MFA) on turvallisuuskäytänne, jossa käyttäjän täytyy syöttää kaksi tai useampia eri tekijöitä todistaakseen henkilöllisyytensä ennen kuin hän saa pääsyn tiettyihin järjestelmiin tai palveluihin. Kaksivaiheisen tunnistautumisen käyttö riippuu palvelun tai järjestelmän tarpeista ja käyttötarkoituksesta. Se on suositeltavaa tietojärjestelmissä joissa on käyttäjän henkilökohtaisia tietoja, tällaisia ovat esimerkiksi verkkopankit ja organisaatioiden sisäiset tietojärjestelmät. 
Kaksivaiheinen tunnistautuminen perustuu seuraaviin asioihin:
1. **Tieto** (knowledge factor): Käyttäjän tiedon varmistaminen, kuten salasanan syöttäminen.
2. **Omistus** (possession factor): Käyttäjän oman laitteen tai fyysisen esineen käyttäminen vahvistuksena, esimerkiksi mobiilisovelluksen, puhelimen tai turvallisuustokenin avulla.
3. **Ominaisuus** (inherence factor): Käyttäjän biometriset piirteet, kuten sormenjälki, kasvojentunnistus tai silmän iiriksen tunnistus

2FA voi sisältää kertakäyttöisen salasanan (OTP) lähettämisen käyttäjälle eri tavoilla:
1. **Tekstiviesti (SMS) tai puhelinvahvistus:** Käyttäjälle lähetetään tekstiviestillä tai puhelimitse yksilöllinen koodi, jonka hän syöttää tunnistautuakseen.
2. **Sähköposti:** Käyttäjälle lähetetään sähköpostitse yksilöllinen koodi.

Tai jonkin tiedon perusteella, joka on vain käyttäjällä:

3. **Mobiilisovellukset:** Monet palvelut tarjoavat mobiilisovelluksen kuten Google tai Microsoft Authenticator tai Authy, jotka tuottavat satunnaisen koodin, jonka käyttäjä syöttää kirjautumisessa.
4. **Fyysinen turvallisuustoken:** Käyttäjille annetaan fyysinen laite, joka tuottaa yksilöllisiä koodeja.
5. **Biometriset piirteet:** Käyttäjä voi käyttää sormenjälkeä, kasvojentunnistusta tai silmän iiristä vahvistumiseen.

### Sessioiden hallinta
Kun käyttäjä on onnistuneesti tunnistettu, sovellus luo istunnon, joka mahdollistaa käyttäjän vuorovaikutuksen sovelluksen kanssa. Tämä sessio voidaan ylläpitää evästeiden tai istuntoiden avulla.

### OAuth 2.0
OAuth 2.0 on standardi jonka avulla voidaan toteuttaa autentikointi web-sovelluksille. Se mahdollistaa kolmannen osapuolen sovellusten tietoturvallisen ja rajatun pääsyn käyttäjän henkilökohtaisiin tietoihin tai resursseihin pilvipalvelussa. OAuth 2.0 mahdollistaa käyttäjän tunnistamisen ja valtuutuksen ilman että kolmas osapuoli saa käyttäjän salasanaa. OAuth-autentikointi perustuu pääsyavaimiin (access tokens) ja pätevyystodisteisiin (refresh tokens), jotka ovat voimassa vain tietyn ajan. 
Muutamia hyötyjä OAuth 2.0 käyttämisestä ovat:

1. **Käyttäjällä täysi hallinta:** Käyttäjä päättää mitkä kolmannet osapuolet voivat käyttää hänen tietojaan tai resurssejaan. Käyttäjä voi antaa tai peruuttaa suostumuksensa milloin tahansa.

2. **Yksinkertainen integraatio:** OAuth 2.0 -standardi on laajalti hyväksytty ja tuettu, mikä tekee siitä helpon integroida erilaisten palveluiden ja sovellusten välillä. OAuth 2.0 -kirjastoja ja ratkaisuja on saatavilla useille ohjelmointikielille.

3. **Skalautuvuus:** OAuth 2.0 on skaalautuva ja soveltuu monenlaisille sovelluksille ja käyttötapauksille: yksinkertaisista kirjautumisprosesseista monimutkaisiin käyttöoikeuksien hallintaan.
