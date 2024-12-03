# Installera och skapa projekt

Det bästa sättet att installera och skapa Angular projekt är genom Angular CLI. Det kan installeras globalt genom NPM. Om du inte har NodeJS och NPM så behöver du installera dem först.

Installera Angular CLI genom:

```
npm install -g @angular/cli
```

Därefter så kan du skapa projekt med Angular CLI. TypeScript kräver ingen egen installation.

Skapa ett nytt Angular projekt med:

```
ng new <app-name>
```

_Notera: `<app-name>` är en placeholder för ditt app namn. Byt ut det mot ditt egna namn, som exempelvis: `ng new my-awesome-app`_

Du bör alltid se till att du ligger i rätt mapp innan du skapar ett projekt. `ng new` skapar en ny mapp.

För att starta igång en dev server:

```sh
cd <app-name> # Navigera in i projektets mapp
ng serve --open # Starta app
```

Alla ändringar du gör i projektet uppdateras automatiskt i webbläsaren så länge `ng serve` är igång.

## Angular CLI

CLI står för "Command Line Interface". Angular har ett CLI som innehåller flera kommandon.

### Skapa projekt

```
ng new <projektnamn>
```

### Starta app

```
ng serve --open
```

### Skapa en komponent

```
ng generate component <namn>
```

Skapa komponent i en specifik mapp:

```
ng generate component folder-name/<namn>
```

### Skapa en service

```
ng generate service <namn>
```

### Skapa en klass

```
ng generate class <namn>
```

### Skapa ett interface

```
ng generate interface <namn>
```

### Mer information

Varje kommando har en `--help` flag. Testa:

```
ng --help
ng generate --help
```
