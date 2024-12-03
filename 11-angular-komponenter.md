# Komponenter

Komponenter är de mest fundamentala byggstenarna i Angular. De kan jämföras med atomer, vilka kombineras för att bilda molekyler, som till sist bildar alla saker vi lever omkring (e.g. bord, datorer, hundar.) I Angular kombineras komponenter på olika sätt för att bygga user interfaces och funktionalitet. Det börjar med små komponenter, som sedan kombineras tillsammans och bygger större komponenter. Det finns egentligen inga regler för hur komponenter ska se ut eller vad de ska bestå av, men typiskt sätt så skapar man komponenter för delbara element som ofta finns på webbsidor. Enkla komponenter (dem minsta delarna) kan exempelvis vara knappar, inputfält, titlar och paragrafer. De kombineras upp för att bilda större komponenter såsom navbars, sidebars, footers och headers. Därefter fortsätter man typiskt sätt att bygga upp page-komponenter (med hjälp av tidigare nämnda komponenter), komponenter som representerar hela webbsidor.

Att skapa komponenter är som att skapa egna HTML-tags som har egen styling och funktionalitet. Komponenter kan skapas genom Angular CLI (se 2-installation.md), eller manuellt, men det är ovanligt.

För att skapa en komponent, skriv följande i terminalen inom projektets mapp:

```
ng generate component <komponentnamn>
```

Komponenter kombineras med andra koncept, såsom directives och events, för att bygga fullständiga webbsidor.

## Delar i komponenter

Angular delar upp sina komponenter i tre delar: styling, struktur och funktionalitet. Varje del har en egen fil.

- `name.component.html` - Detta är struktur-filen, som kallas template, och det är en HTML fil. Innehållet i denna fil bestämmer hur komponenten renderas. Läs dokumentet om templates för mer information.
- `name.component.css` - Detta är styling-filen och det är en CSS fil. Innehållet i denna fil bestämmer all styling för komponenten. Läs sektionen om styling nedanför för mer information.
- `name.component.ts` - Detta är funktionalitet-filen och det är en TypeScript fil. I komponentens klass läggs all funktionalitet, alla egenskaper och alla metoder som kan behövas. Om du exempelvis behöver anropa en funktion vid ett knapptryck så lägger du till funktionen inom denna klass.

En komponent och de tre delarna kan se ut såhär i en ny komponent:

```typescript
// test.component.ts
import { Component } from "@angular/core";

@Component({
  selector: "app-test",
  templateUrl: "./test.component.html",
  styleUrls: ["./test.component.css"],
})
export class TestComponent {}
```

```html
<!-- test.component.html -->
<p>test works!</p>
```

```css
/* test.component.css */
/* CSS filer är tomma från början. */
```

Delarna är kopplade automatiskt så du kan exempelvis referera till egenskaper från klassen i template filen.

Den viktiga delen i TypeScript filen är `@Component`. Den bestämmer hur komponenten ska fungera. `selector` bestämmer namnet på komponenten, vilket används när den ska refereras till i andra komponenter. För att få in `TestComponent` i `AppComponent` exempelvis, så kan man skriva:

```html
<!-- app.component.html -->
<app-test></app-test>
```

`templateUrl` och `styleUrls` länkar till de andra delarna och de behöver oftast inte modifieras.

## Styling

Varje komponent har en egen CSS fil. All CSS som ligger innanför komponentens fil kommer att appliceras på komponentens element, och endast på den komponenten. Alla andra komponenter påverkas inte, även om de har samma klassnamn och id:n på element. Detta kallas "scope". Varje komponent har ett eget "scope".

För att applicera global styling kan den globala `styles.css` filen användas.
