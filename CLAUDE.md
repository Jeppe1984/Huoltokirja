# Huoltokirja

Yksi itsenäinen HTML-tiedosto (`index.html`), julkaistaan GitHub Pagesilla osoitteessa https://jeppe1984.github.io/Huoltokirja/. Ei build-vaihetta eikä riippuvuuksia. Käyttöliittymän tekstit ovat suomeksi.

## Julkaisu

Jokaisessa käyttäjälle näkyvässä muutoksessa:

1. Nosta versio `index.html`:ssä: `const VERSIO = "x.y.z", VERSIO_PVM = "VVVV-KK-PP";`
2. Päivitä `version.json` samaan versioon ja päivään. `muutokset`-listan 2–4 lyhyttä riviä näytetään päivitysilmoituksessa.
3. Lisää rivi README:n Versiot-osioon.
4. Viittaa commit-viestissä suljettaviin issueihin (`Closes #n` / `Fixes #n`).

Ladatut kopiot vertaavat omaa `VERSIO`-arvoaan `version.json`-tiedostoon, joten nämä kaksi on pidettävä samassa versiossa.

## Tietomalli

Tietokanta (localStorage tai käyttäjän .json-tiedosto) on versiota 3:
- `yhteiset`: huoltamot, kaupat, luokat, polttoaineet
- `varasto[]`: varaosaostot, yhteisiä kaikille autoille: `nimi, luokka, kauppa, hankinta, hinta` (koko oston hinta), `maara, yksikko`, `auto` (varattu autolle tai `null` = yhteinen)
- `autot[]`: jokaisella `asetukset, tankkaukset, huollot, maksut` ja `osat` = varaston käytöt `{varastoId, maara, asennus, odo}`. Käytön kulu = `hinta * maara / oston maara`; jäljellä = oston määrä − kaikkien autojen käytöt.

`load()` muuntaa vanhat versiot automaattisesti (v1 yksi auto → v2 monta autoa → v3 auton osat ostoiksi ja käytöiksi). Älä riko vanhojen tiedostojen avaamista.
