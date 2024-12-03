# Templates

En template är en ritning för hur en komponent ska se ut, eller med andra ord, hur den skall renderas. De skrivs i HTML, och Angular har en viss syntax som möjliggör fler saker än vanlig HTML. När du skapar en ny komponent så får du med en `.html` fil. I den lägger du alla element som du vill att komponenten skall ha.

Nedanför hittar du information om de koncept som är speciella för Angular (utöver HTML) och de som underlättar vid utveckling.

## Binding

Nedanför hittar du information om text interpolation, template statements och mer. I många av de exempel som visas nedanför så refererar template koden till någon variabel som ligger i komponentens TypeScript kod. Varje template är automatiskt kopplad till komponent-klassen så att du enkelt kan referera till egenskaper och funktioner/metoder. Varje ändring som sker i klassen (ändring av variabel/egenskap exempelvis) uppmärks också automatiskt av Angular. Detta betyder att alla egenskaper i en komponent klass fungerar automatiskt som en React state kan man säga. Se [dokumentationen](https://angular.io/guide/binding-overview) för mer information om detta och exempel.

## Text interpolation

Text interpolation betyder att du kan referera till variabler innanför HTML. Föreställ dig att du har följande klass för en komponent:

```typescript
import { Component } from "@angular/core";

@Component({
  selector: "app-text-interpolation",
  templateUrl: "./text-interpolation.component.html",
  styleUrls: ["./text-interpolation.component.css"],
})
export class TextInterpolationComponent {
  hero: string = "Ironman";
}
```

Du kan rendera ut `"Ironman"` genom att lägga in följande i dens template (`text-interpolation.component.html`):

```html
<div>My favorite hero is {{ hero }}</div>
```

Angular ser `{{}}` och förstår att den skall uppfatta koden som en referens istället för vanlig HTML. Detta är ekvivalent med `{}` i React JSX.

Du kan även använda detta för attributer och annat:

```html
<img src="{{ myImage }}" />
```

... där du får föreställa dig att `myImage` ligger som en egenskap i komponentens klass.

## Template statements

Template statements är (TypeScript-)kod som du kan skriva innanför templates för att exempelvis hantera events och anroppa funktioner. Se [dokumentationen](https://angular.io/guide/template-statements) för information om vilka regler som gäller och vilken syntax som gäller.

## Pipes

Pipes är ett koncept som inte är så viktigt att veta om och förstå, men här är en länk till [dokumentationen](https://angular.io/guide/pipes-overview) om du vill läsa mer ändå då det kan vara användbart ibland.

## Template reference variables

Du kan skapa referenser till element som endast kan användas i HTML genom `#`:

```html
<input #content />
<button (click)="printValue(content.value)">Print the content of input</button>
```

Läs [dokumentationen](https://angular.io/guide/template-reference-variables) för mer information.
