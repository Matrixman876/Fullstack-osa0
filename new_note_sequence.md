# Kaavio: Uuden muistion luominen 

```mermaid
sequenceDiagram
 participant browser
 participant server

    selain->>palvelin: GET https://studies.cs.helsinki.fi/exampleapp/notes
 aktivoi palvelin
 palvelin-->>selain: HTML-dokumentti
 deaktivoi palvelin

    selain->>palvelin: GET https://studies.cs.helsinki.fi/exampleapp/main.css
 aktivoi palvelin
 palvelin-->>selain: CSS-tiedosto
 deaktivoi palvelin

    selain->>palvelin: GET https://studies.cs.helsinki.fi/exampleapp/main.js
 aktivoi palvelin
 palvelin-->>selain: JavaScript-tiedosto
 deaktivoi palvelin

    Huomaa selaimen oikealla puolella: JS suoritetaan selaimessa ja odotetaan lomakkeen lähettämistä.

    selain->>palvelin: POST https://studies.cs.helsinki.fi/exampleapp/new_note lomakkeen tiedoilla
 aktivoi palvelin
 palvelin-->>selain: Uudelleenohjaus osoitteeseen /notes
 deaktivoi palvelin.

    selain->>palvelin: GET https://studies.cs.helsinki.fi/exampleapp/notes
 aktivoi palvelin
 palvelin-->>selain: Päivitetty HTML uudella muistiinpanolla
 deaktivoi palvelin
