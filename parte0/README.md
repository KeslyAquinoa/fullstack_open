**0.4 - Novo Diagrama**
```mermaid
sequenceDiagram
    actor user
    participant browser
    participant server

    user->>browser: New note

    browser->>server: o navegador envia a entrada (input) do usuário para o servidor. <br> The browser sends the user's input to the server.
    activate server
    server-->>browser: o servidor pede ao navegador para fazer uma nova requisição HTTP GET <br> para o endereço definido no cabeçalho Localização (Location) — o endereço notes. <br> The server asks the browser to make a new HTTP GET request to the address defined in the Location header — the notes address.
    deactivate server

    browser->>server: O recarregamento faz mais três requisições HTTP (busca o arquivo main.css, main.js e data.json). <br> The reload makes three more HTTP requests (fetching the files main.css, main.js, and data.json).

    activate server

    Note right of browser: o navegador recarrega a página de Notas (Notes). <br> The browser reloads the Notes page.


    server-->>browser: O servidor cria um novo objeto nota e adiciona-o a um array chamado notes. <br> The server creates a new note object and adds it to an array called notes.
    deactivate server

    Note left of server: Os objetos de "Notes" têm dois campos: content, contendo o conteúdo real da nota <br> e date, contendo a data e hora em que a nota foi criada. <br> The "Notes" objects have two fields: content, containing the actual note content, and date, containing the date and time the note was created.

    browser-->>user: O navegador mostra na tela a entrada inserida. <br> The browser displays the entered input on the screen.
```

**0.5 - Diagrama SPA**
```mermaid
sequenceDiagram
    participant User
    participant Browser
    participant Server

    User->>Browser: Acessa a SPA / Accesses the SPA
    Browser->>Server: Solicita HTML + JS / Requests HTML + JS
    Server-->>Browser: Retorna HTML + JS / Returns HTML + JS
    Browser->>Server: Busca notas existentes (GET /notes) / Fetches existing notes (GET /notes)
    Server-->>Browser: Retorna JSON com notas / Returns JSON with notes
    User->>Browser: Adiciona nova nota e clica em enviar / Adds a new note and clicks submit
    Browser->>Browser: Atualiza a lista de notas na tela / Updates the note list on screen
    Browser->>Server: Envia nova nota (POST /new_note_spa) / Sends new note (POST /new_note_spa)
    Server-->>Browser: Confirmação de sucesso (201 Created) / Success confirmation (201 Created)
```

**0.6 - Nova nota no Diagrama SPA**
```mermaid
sequenceDiagram
    participant Usuario as Usuário / User
    participant Navegador as Navegador / Browser
    participant Servidor as Servidor / Server

    Usuario->>Navegador: Digita uma nova nota e clica em enviar / Types a new note and clicks submit
    Navegador->>Navegador: Impede recarregamento da página / Prevents page reload
    Navegador->>Navegador: Atualiza a tela com a nova nota / Updates the screen with the new note
    Navegador->>Servidor: Envia a nova nota (POST /new_note_spa) / Sends the new note (POST /new_note_spa)
    Servidor-->>Navegador: Confirmação de sucesso (201 Created) / Success confirmation (201 Created)
```
