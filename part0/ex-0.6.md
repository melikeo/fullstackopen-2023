```mermaid

sequenceDiagram
    participant browser
    participant server

    Note right of browser: User enters note in the text field and clicks save.

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa
    activate server
    server-->>browser: HTML document (HTTP 201)
    deactivate server

    Note right of browser: The browser executes the callback function that renders the notes
