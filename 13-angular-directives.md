# Directives

Directives är (HTML-)attributer specifika till Angular som hjälper dig som utvecklare att lägga till funktionalitet på element. Typiskt sätt så börjar directives med `ng`. Några exempel är: `ngClass`, `ngFor` och `ngIf`.

Säg att du har en array med nummer som du vill lista upp med HTML:

```typescript
import { Component } from "@angular/core";

@Component({
  selector: "app-my",
  templateUrl: "./my.component.html",
  styleUrls: ["./my.component.css"],
})
export class MyComponent {
  numbers: number[] = [1, 2, 3];
}
```

Använd `ngFor` för att loopa genom nummer och skapa en `div` för varje:

```html
<div *ngFor="let item of numbers">{{ item }}</div>
```

Det finns två typer av directives: attribute och structural.

## Attribute directives

Attribute directives är till för att lyssna på, eller ändra på, beteenden av andra element, attributer, egenskaper och komponenter. De vanligaste är: `ngClass`, `ngStyle` och `ngModel`. Dessa directives skrivs med `[]` runtom namnet.

### NgClass

NgClass är till för att applicera en eller flera HTML-klasser på ett element. Det kan se ut såhär:

```html
<div [ngClass]="theme === 'dark' ? 'dark-theme' : 'light-theme'">
  This div changes it appearance based on the theme applied.
</div>
```

För att applicera flera klasser:

```typescript
import { Component } from "@angular/core";

@Component({
  selector: "app-test",
  templateUrl: "./test.component.html",
  styleUrls: ["./test.component.css"],
})
export class TestComponent {
  classes: Record<string, boolean> = {
    firstClass: true,
    secondClass: false,
    thirdClass: true,
  };
}
```

```html
<div [ngClass]="classes"></div>
```

Varje egenskap i objektet `classes` är en klass. Värdet (`true` eller `false`) bestämmer om klassen appliceras eller inte. `firstClass` och `thirdClass` kommer därför finnas med, medans `secondClass` skippas eftersom den har värdet `false`.

### NgStyle

NgStyle är till för att applicera inline-styling på element. Det kan se ut såhär:

```typescript
import { Component } from "@angular/core";

@Component({
  selector: "app-test",
  templateUrl: "./test.component.html",
  styleUrls: ["./test.component.css"],
})
export class TestComponent {
  styling: Record<string, string> = {
    background: "blue",
    display: "flex",
    "font-size": "24px",
  };
}
```

```html
<div [ngStyle]="styling"></div>
```

### NgModel

NgModel är till för att visa och uppdatera data. Den brukar användas med inputfält och formulär. Det kan se ut såhär:

Man måste först importera FormsModule för att få in formulär:

```typescript
import { NgModule } from "@angular/core";
import { FormsModule } from "@angular/forms";
import { BrowserModule } from "@angular/platform-browser";

import { AppComponent } from "./app.component";
import { InputsComponent } from "./inputs.component";

@NgModule({
  declarations: [AppComponent, InputsComponent],
  imports: [BrowserModule, FormsModule],
  providers: [],
  bootstrap: [AppComponent],
})
export class AppModule {}
```

... och sedan kan man skriva

```typescript
import { Component } from "@angular/core";

@Component({
  selector: "app-inputs",
  templateUrl: "./inputs.component.html",
  styleUrls: ["./inputs.component.css"],
})
export class InputsComponent {
  value: string = "";
}
```

```html
<input [(ngModel)]="value" />
```

... vilket gör så att `value` alltid har samma text som skrivs in i `input`. Egenskapen speglar alltså inputten och det är så du hanterar inputfält.

## Structural directives

Structural directives är till för att ändra på DOM struktur och layout, eller med andra ord manipulera element. De vanligaste är: `ngFor`, `ngIf` och `ngSwitch`. Dessa directives skrivs med `*` som prefix.

### NgFor

NgFor är till för att loopa i en lista. Den fungerar som en for-each loop i JavaScript och ser ut såhär:

```html
<ul>
  <li *ngFor="let food of favoriteFoods">
    <a href="{{ food.url }}">{{ food.name }}</a>
  </li>
</ul>
```

... denna kod hade resulterat i ett `li` element per maträtt i `favoriteFoods` listan, var den nu är. Om `favoriteFoods` innehåller sju maträtter så kommer det att finnas sju `li` element.

### NgIf

NgIf är till för att rendera element baserat på ett villkor. Den fungerar som en if-sats i JavaScript och ser ut såhär:

```html
<div *ngIf="hero === 'Ironman'">My favorite hero!</div>
```

... där `hero` är en variabel som kommer från komponenten.

NgIf kan också kombineras med `else` satser, men det är ofta enklare att köra på bara `ngIf`, genom att flippa villkor. Säg att du vill skriva "A good hero, but not my favorite" om hjälten inte är "Ironman" så kan du, istället för att använda en else sats, skriva:

```html
<div *ngIf="hero !== 'Ironman'">A good hero, but not my favorite</div>
```

Detta fungerar för alla villkor eftersom alla `true` har en `false` motsats.

### NgSwitch

NgSwitch är till för att rendera element baserat på ett villkor. Den fungerar som en switch-sats i JavaScript och ser ut såhär:

```html
<div [ngSwitch]="hero">
  <div *ngSwitchCase="'Ironman'">My favorite hero!</div>
  <div *ngSwitchCase="'Batman'">I am batman!</div>
  <div *ngSwitchCase="'Superman'">A very strong hero!</div>
  <div *ngSwitchCase="'Thor'">God of Thunder!</div>
</div>
```

... där `hero` är en variabel som kommer från komponenten.
