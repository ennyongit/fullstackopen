```mermaid
sequenceDiagram

participant User
participant Browser
participant Server

User->>Browser: Enter note and press button
Browser->>Server:POST https://studies.cs.helsinki.fi/exampleapp/spa-new-note (via JavaScript)

Server->>Browser: Respond with 200 ok
Browser->>Server: GET/https://studies.cs.helsinki.fi/exampleapp/spa/data.json 
Server->>Browser: Send updated Json Data
Browser->>User: Update UI with new note (But no full reload)
```
