# @Output

Outputs är ett sätt att få in information från en komponent till en annan komponent. Flödet är: child -> parent. Output är alltså samma sak som @Input men information skickas istället från child till parent (i jämförelse med parent -> child.) I React så kan information endast skickas nedåt direkt (parent komponent till child komponent) men i Angular så kan man skicka information uppåt direkt också (child till parent). Lösningen i React är att skicka ned en funktion som kan anroppas och referera till funktionen ovanför, och samma princip gäller för @Output i Angular.

Outputs deklareras in en child komponent med:

```typescript
import { Component, EventEmitter, Output } from "@angular/core";

@Component({
  selector: "app-button",
  templateUrl: "./button.component.html",
  styleUrls: ["./button.component.css"],
})
export class ButtonComponent {
  @Output()
  onClick = new EventEmitter<string>();
}
```

`EventEmitter` är en klass som fungerar som en callback. Innanför `<>` så skriver du vilken datatyp funktionens parameter skall ha. Om du vill skicka med ett helt event så kan du skriva:

```typescript
new EventEmitter<Event>();
```

När du har en @Output så kan du anroppa på den för att skicka upp information. Ett färdigt exempel kan se ut såhär:

```typescript
import { Component, EventEmitter, Output } from "@angular/core";

@Component({
  selector: "app-button",
  templateUrl: "./button.component.html",
  styleUrls: ["./button.component.css"],
})
export class ButtonComponent {
  @Output()
  onClick = new EventEmitter<Event>();
}
```

```html
<button (click)="onClick.emit($event)">Click Me!</button>
```

Se dokumentet om events för information om vad `(click)` betyder. Det som skickar upp informationen är `onClick.emit($event)`. Och självklart så måste det hanteras i en parent komponent. Det kan se ut såhär:

```typescript
import { Component } from "@angular/core";

@Component({
  selector: "app-root",
  templateUrl: "./app.component.html",
  styleUrls: ["./app.component.css"],
})
export class AppComponent {
  onClick(event: Event) {
    // Printar ut event variabeln som skickas hela vägen från `ButtonComponent`.
    console.log(event);
  }
}
```

```html
<app-country-table (onClick)="onClick($event)"></app-country-table>
```

_Notera: det måste inte vara just `AppComponent` som hanterar värdet_
