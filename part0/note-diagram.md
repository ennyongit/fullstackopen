```mermaid
flowchart TD

A[User] --> B[Input text field]
B --> |new note| C{Submit}
C -->|Server stores new note & responds with 302| D[Browser follows redirect]
D -->|Makes new HTTP GET request| E[Fetch updated notes from server]
E --> F[Render updated notes on the page]
```

```mermaid
sequenceDiagram
  participant browser
  participant server

browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/notes
server->>browser: HTML Document
Note right of browser: The server responds with HTTP status code 200 (OK), sending the HTML document.

browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
server->>browser: CSS file
browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
server->>browser: JavaScript File
browser->>server: GET  https://studies.cs.helsinki.fi/exampleapp/data.json
server->>browser: Json Data
Note right of browser: Browser renders page with the notes  

browser->>server: POST  https://studies.cs.helsinki.fi/exampleapp/notes { new_note_data }
server->>browser: HTTP Status 302 (Redirect to /notes)
Note right of browser: The server instructs the browser to make a new GET request to /notes.

browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/notes
server->>browser: HTML Document
browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
server->>browser: Updated JSON Data
Note right of browser: Browser re-renders the page with the new note.

