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

Tietokanta (localStorage tai käyttäjän .json-tiedosto) on versiota 2: `yhteiset` (huoltamot, kaupat, luokat, polttoaineet) ja `autot[]`, joilla jokaisella `asetukset`, `tankkaukset`, `huollot`, `osat`, `maksut`. `load()` muuntaa vanhan version 1 (yksi auto) automaattisesti. Älä riko vanhojen tiedostojen avaamista.
