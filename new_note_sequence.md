# Sequence Diagram: Uuden muistiinpanon luominen

Tässä kaaviossa esitetään tapahtumien kulku, kun käyttäjä lisää uuden muistiinpanon osoitteessa https://studies.cs.helsinki.fi/exampleapp/notes.

```mermaid
sequenceDiagram
 participant browser
 participant server

    Huomautus selaimen oikealla puolella: Käyttäjä kirjoittaa muistiinpanon ja napsauttaa "Save" (Tallenna).

    selain->>palvelin: POST https://studies.cs.helsinki.fi/exampleapp/new_note lomakkeen tiedoilla
 aktivoi palvelin
 Huomautus palvelimen oikealla puolella: Palvelin tallentaa uuden muistiinpanon ja vastaa uudelleenohjauksella
 palvelin-->>selain: HTTP 302 uudelleenohjaus osoitteeseen /notes
 deaktivoi palvelin.

    selain->>palvelin: GET https://studies.cs.helsinki.fi/exampleapp/notes
 aktivoi palvelin
 palvelin-->>selain: HTML-dokumentti
 deaktivoi palvelin

    selain->>palvelin: GET https://studies.cs.helsinki.fi/exampleapp/main.css
 aktivoi palvelin
 palvelin-->>selain: CSS-tiedosto
 poista palvelin käytöstä.

    selain->>palvelin: GET https://studies.cs.helsinki.fi/exampleapp/main.js
 aktivoi palvelin
 palvelin-->>selain: JavaScript-tiedosto
 deaktivoi palvelin

    Huomautus selaimen oikealla puolella: JavaScript-koodi hakee päivitetyn muistiinpanoluettelon palvelimelta

    selain->>palvelin: GET https://studies.cs.helsinki.fi/exampleapp/data.json
 aktivoi palvelin
 palvelin-->>selain: JSON, jossa on kaikki muistiinpanot (myös uusi)
 deaktivoi palvelin

    Huomautus selaimen oikealla puolella: Selain suorittaa takaisinkutsun ja palauttaa muistiinpanot uudelleen.

Translated with DeepL.com (free version)