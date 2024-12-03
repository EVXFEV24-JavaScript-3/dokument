# Filstruktur

Ett nytt Angular projekt innehåller några filer som kommer från `ng new`. Dessa ger en bra grund att bygga på.

Notera:

- Ett slash (`/`) indikerar att filen är en mapp och kan innehålla fler filer
- Om du har en fil som inte visas här så betyder det att den tillhör något annat än Angular, exempelvis git
- Radera inte filer om du inte vet vad de gör

- **node_modules/** - Innehåller alla bibliotek och ramverk som installeras av NPM. Angular ligger bland annat här.
- **src/** - Huvudmappen som innehåller all Angular kod. Den startar med lite default kod från Angular.
  - **app/** - Huvudfilen som startar igång hela Angular applikationen.
    - **app-routing.module.ts** - Här ligger routes för applikationen. Denna fil finns med om man inkluderar "routing".
    - **app.component.css** - CSS filen för huvudkomponenten.
    - **app.component.html** - HTML filen för huvudkomponenten.
    - **app.component.ts** - TypeScript filen för huvudkomponenten.
    - **app.module.ts** - Huvudmodulen för appen. Oftast behövs bara en modul (default.)
  - **assets/** - En mapp för bilder, videor och andra "assets".
  - **favicon.ico** - En ikon som Angular kommer med.
  - **index.html** - Boilerplate HTML filen för appen.
  - **styles.css** - En fil för globala styles. All styling som läggs in här appliceras på alla komponenter.
  - **main.ts** - TypeScript filen som startar igång hela appen.
- **package.json** - Innehåller information om lite allt möjligt, exempelvis paket, kommandon och moduler. Du behöver nästan aldrig röra denna fil.
- **package-lock.json** - Håller koll på den exakta versionen på varje paket som installeras. Du behöver nästan aldrig röra denna fil.
