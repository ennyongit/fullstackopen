```mermaid

sequenceDiagram 

participant User
participant Browser
participant Server


User->>Browser: Open https://studies.cs.helsinki.fi/exampleapp/spa
Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/spa
Server->>Browser: Send HTML File
Browser->>Server: GET /main.css
Server->>Browser: Send CSS File
Browser->>Server: GET /spa.js
Server->>Browser: Send JavaScript File
Browser->>Server: GET /data.json
Server->>Browser: Send Json data (existing notes)
Browser->>User: Render notes UI

```