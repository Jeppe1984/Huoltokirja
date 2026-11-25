# Huoltokirja

Sähköinen huoltokirja autoille ja moottoripyörille. Yksi HTML-tiedosto, joka toimii selaimessa ilman palvelinta, tiliä tai asennusta.

**Käytä selaimessa:** https://jeppe1984.github.io/Huoltokirja/

## Mitä sillä tekee

- **Tankkaukset ja kulutus** – keskikulutus (l/100 km), polttoainekulut, kulutuskäyrä
- **Huollot** – huoltohistoria leimoina, tehdyt toimenpiteet, työn hinta, huoltamo
- **Varaosat ja varasto** – yhteinen varasto kaikille autoille, määrät ja yksiköt (kpl, l, kg…), osittainen käyttö ja varastokirjanpito: ostot, käytöt autoittain ja jäljellä olevan varaston arvo
- **Huoltomuistutukset** – huoltovälit kilometreinä ja kuukausina, katsastuspäivä
- **Vakuutukset ja verot** – vuosisumma ja erien määrä tai yksittäinen lasku; tulevat eräpäivät näkyvät muistutuksissa ja erääntyneet erät kokonaiskuluissa
- **Kulut** – kokonaiskulut, kilometrihinta, kuukausikulu ja kuukausittainen kaavio
- **Monta autoa** – jokaiselle omat kirjaukset, huoltovälit ja seurattavat asiat
- **Huoltamot** – yhteinen lista nimineen ja yhteystietoineen
- **CSV-vienti** – tankkaukset, huollot ja varaosat taulukkolaskentaan

Tankkausten, varaosien sekä vakuutusten ja verojen seurannan voi kytkeä pois autokohtaisesti, jos niitä ei tarvitse.

## Missä tiedot ovat

Tiedot eivät lähde koneeltasi minnekään. Sivulla ei ole palvelinta eikä analytiikkaa.

- **Chrome ja Edge:** valitse *Asetukset → Tietokanta → Tallenna uuteen tiedostoon…*. Kaikki kirjaukset tallentuvat automaattisesti valitsemaasi `.json`-tiedostoon. Kun avaat sivun uudelleen, selain kysyy kerran luvan jatkaa samalla tiedostolla.
- **Firefox ja Safari:** tiedot pysyvät selaimen muistissa. Lataa tietokanta tiedostoksi *Lataa tietokanta* -napilla ja avaa se tarvittaessa uudelleen.

Kun pidät `.json`-tiedostoa esimerkiksi OneDrivessa tai Dropboxissa, sama huoltokirja on käytössä kaikilla koneillasi.

## Käyttö ilman verkkoa

Avaa sivu ja tallenna se omalle koneellesi (Ctrl+S, tallennusmuodoksi *Verkkosivu, vain HTML*) tai lataa `index.html` tästä reposta. Avaa tiedosto selaimessa: sivu toimii samoin kuin verkossa.

Sivun alareunassa näkyy käytössä oleva versio. Kun ladattu sivu avataan verkkoyhteyden ollessa päällä, se tarkistaa tiedostosta `version.json`, onko uudempi versio saatavilla, ja kertoo siitä sivun yläreunassa. Päivitä tallentamalla uusi versio vanhan tiedoston päälle. Kirjaukset eivät ole sivutiedostossa, joten ne säilyvät. Tarkistuksessa ladataan vain versiotieto, eikä mitään omia tietojasi lähetetä. Fontit ladataan Google Fontsista, ja ilman verkkoyhteyttä selain käyttää omia fonttejaan.

## Tietokannan muoto

Tietokanta on luettavaa JSON:ia:

```json
{
  "sovellus": "Huoltokirja",
  "versio": 3,
  "yhteiset": { "huoltamot": [], "kaupat": [], "luokat": [], "polttoaineet": [] },
  "varasto": [ { "id": "…", "nimi": "Moottoriöljy 0W-20", "maara": 5, "yksikko": "l", "hinta": 45, "auto": null } ],
  "autot": [
    { "id": "…", "asetukset": { "auto": "Toyota Yaris", "rekisteri": "ABC-123", "huoltovalit": [] },
      "tankkaukset": [], "huollot": [], "osat": [], "maksut": [] }
  ]
}
```

## Kehitysideat ja palaute

Onko sinulla idea, miten huoltokirjasta saisi paremman? [**Ehdota parannusta**](https://github.com/Jeppe1984/Huoltokirja/issues/new?template=kehitysidea.yml). Katso myös [muiden ideat](https://github.com/Jeppe1984/Huoltokirja/issues) ja anna 👍 niille, joita kannatat. Eniten kannatusta saaneet tehdään ensin.

Jos jokin ei toimi, [ilmoita virheestä](https://github.com/Jeppe1984/Huoltokirja/issues/new?template=virhe.yml). Ilmoitukset ovat julkisia, joten älä liitä niihin omia tietojasi.

Ideoiden ja ilmoitusten jättäminen vaatii ilmaisen GitHub-tilin.

## Versiot

- **1.4.0** (25.11.2026) – Yhteinen varaosavarasto, määrät ja osittainen käyttö, varastokirjanpito
- **1.3.0** (25.11.2026) – Versionumero näkyviin ja ilmoitus uudesta versiosta
- **1.2.0** (25.11.2026) – Vakuutukset ja verot eräpäivineen; huoltamon valinta korjattu
- **1.1.0** (16.11.2026) – Monta autoa, seurattavien asioiden valinta, huoltamot, palautelomakkeet
- **1.0.0** (16.11.2026) – Ensimmäinen julkaisu

## Huomioita

- Kulutus lasketaan olettaen, että jokainen tankkaus on täyteen.
- Oletushuoltovälit ovat tyypillisiä bensa-auton arvoja. Tarkista oman autosi huolto-ohjelma ja muokkaa välit asetuksissa.
