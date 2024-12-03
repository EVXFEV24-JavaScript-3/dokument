# @Input

Inputs är ett sätt att få in information från en komponent till en annan komponent. Flödet är: parent -> child. Det är ekvivalent med React props och fungerar likt parametrar (till vanliga JavaScript funktioner.)

Deklarera inputs med:

```typescript
import { Component, Input } from "@angular/core";

@Component({
  selector: "app-hero",
  templateUrl: "./hero.component.html",
  styleUrls: ["./hero.component.css"],
})
export class HeroComponent {
  @Input()
  hero: string = "";
}
```

```html
<!-- Fungerar som en vanlig variabel som kan användas i en template -->
<div>{{ hero }}</div>
```

Skicka in inputs genom:

```typescript
import { Component } from "@angular/core";

@Component({
  selector: "app-root",
  templateUrl: "./app.component.html",
  styleUrls: ["./app.component.css"],
})
export class AppComponent {
  heroName: string = "Ironman";
}
```

```html
<app-hero [hero]="heroName"></app-hero>
```

_Notera: det måste inte vara just `AppComponent` men värdet måste ligga som en egenskap (i detta fallet `heroName`) i komponenten som refererar till den andra komponenten som behöver inputten_

Ibland så vill man veta när en input har ändrats (som en event listener) och då kan man använda `OnChanges`. Se dokumentet om lifecycles för mer information.
