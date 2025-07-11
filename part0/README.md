# Full Stack Open 2025 - Part 0a

## 0.4: New note diagram

sequenceDiagram
    participant browser
    participant server

    Note right of browser: User writes a new note and clicks "Save"

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note
    activate server
    server-->>browser: HTTP redirect to /notes
    deactivate server

    Note right of browser: The browser reloads the page and sends a new GET request

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate server
    server-->>browser: HTML document
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: the css file
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate server
    server-->>browser: the JavaScript file
    deactivate server

    Note right of browser: JavaScript is executed and fetches the JSON data

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: JSON with updated list of notes
    deactivate server

    Note right of browser: Browser renders the updated list of notes


## 0.5: Single page app diagram

sequenceDiagram
    participant browser
    participant server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa
    activate server
    server-->>browser: HTML document
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: the css file
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa.js
    activate server
    server-->>browser: the JavaScript file
    deactivate server

    Note right of browser: JavaScript is executed and fetches the notes data

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: JSON with list of notes
    deactivate server

    Note right of browser: JavaScript renders the notes dynamically without reloading the page


## 0.6: New note in Single page app diagram

sequenceDiagram
    participant browser
    participant server

    Note right of browser: User writes a note and clicks "Save"

    Note right of browser: JavaScript handles the form submission

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa
    activate server
    server-->>browser: 201 Created (or similar success response)
    deactivate server

    Note right of browser: JavaScript updates the local state and re-renders the note list
    Note right of browser: No full page reload occurs