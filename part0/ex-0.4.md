```mermaid

sequenceDiagram
    participant browser
    participant server

    Note right of browser: User enters something in the text field and clicks on save.

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note
    activate server
    server-->>browser: HTTP Status Code 302 (URL Redirect: Server asks browser to do a new HTTP GET to location, here /exampleapp/notes)
    deactivate server

    Note right of browser: browser reloads the notes page
    browser->>server: GET /exampleapp/notes
    activate server
    server-->>browser: HTML Document

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: the CSS file
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate server
    server-->>browser: the JavaScript file
    deactivate server

    Note right of browser: The browser starts executing the JavaScript code that fetches the JSON from the server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: [ { content: "hi guys", date: "2023-08-20T08:37:40.870Z" }, ...]
    deactivate server

    Note right of browser: The browser executes the callback function that renders the notes
