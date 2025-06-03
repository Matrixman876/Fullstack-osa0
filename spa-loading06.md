

```mermaid
sequenceDiagram
    participant browser
    participant server

    Note right of browser: User types a note and clicks "Save"

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa with JSON content
    activate server
    server-->>browser: HTTP 201 Created (confirmation response)
    deactivate server

    Note right of browser: JavaScript updates the note list in memory and rerenders it without page reload
