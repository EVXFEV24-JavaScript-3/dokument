# Lifecycles

Alla Angular komponenter har en livscykel, precis som i React. Den börjar när en komponent renderas första gången och slutar när komponenten försvinner från DOMen. Under livstiden så håller Angular koll på alla ändringar som görs och detta räknas också in i livscykeln.

Man kan lyssna på lifecycle events genom hook interfaces. Om du exempelvis vill lyssna efter `OnInit` events så kan du skriva:

```typescript
import { Component } from "@angular/core";

@Component({
  selector: "app-my",
  templateUrl: "./my.component.html",
  styleUrls: ["./my.component.css"],
})
export class MyComponent implements OnInit {
  // implement OnInit's `ngOnInit` method
  ngOnInit() {
    console.log("Component was initialized.");
  }
}
```

Detta fungerar samma för alla lifecycles. Referera till [dokumentationen](https://angular.io/guide/lifecycle-hooks) för en lista på alla livscyklar.
