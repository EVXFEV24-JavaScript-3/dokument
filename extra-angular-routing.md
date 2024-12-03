# Routing

Det enklaste sättet att komma igång med routing är genom att välja med det när man skapar ett Angular projekt. Det går bra att skapa alla filer manuellt annars också.

I ett projekt med routing så har man en fil som heter `app-routing.module.ts` vilket innehåller all routing information:

```typescript
import { NgModule } from "@angular/core";
import { RouterModule, Routes } from "@angular/router";

const routes: Routes = [];

@NgModule({
  imports: [RouterModule.forRoot(routes)],
  exports: [RouterModule],
})
export class AppRoutingModule {}
```

Innanför `routes` arrayen så lägger man in alla routes som man vill ha, exempelvis:

```typescript
const routes: Routes = [
  {
    path: "",
    component: HomeComponent,
  },
  {
    path: "/about",
    component: AboutComponent,
  },
  {
    path: "/contact",
    component: ContactComponent,
  },
];
```

För att rendera ut alla routes så skriver du följande på valfritt ställe (exempelvis i App komponenten):

```html
<router-outlet></router-outlet>
```

... den borde ligga där redan om du skapade projektet med routing valet.

För att länka till olika routes så kan du använda `routerLink` attributen:

```html
<ul>
  <li>
    <a routerLink="/about">Go to about</a>
  </li>
  <li>
    <a routerLink="/">Go to home</a>
  </li>
</ul>
```

... vilket även fungerar på vanliga tags:

```html
<span routerLink="/about">Go to about</span>
<button routerLink="/">Go to home</button>
```

Om du behöver navigera med TypeScript så kan du använda `Router` som Angular injectar automatiskt:

```typescript
import { Component } from "@angular/core";
import { Router } from "@angular/router";

@Component({
  selector: "app-links",
  templateUrl: "./links.component.html",
  styleUrls: ["./links.component.css"],
})
export class LinksComponent {
  constructor(private router: Router) {}

  navigateSomewhere() {
    // Go to home
    this.router.navigate(["/"]);

    // Go to /contact
    this.router.navigate(["/contact"]);
  }
}
```

## Path variabler

Lägg till en parameteriserad route med `:<namn>` i `app-routing.module.ts`, som i följande exempel:

```typescript
const routes: Routes = [
  {
    path: "",
    component: HomeComponent,
  },
  {
    path: "/profile/:id",
    component: ProfileComponent,
  },
];
```

Hämta path variabeln i en komponent med:

```typescript
import { Component } from "@angular/core";
import { ActivatedRoute } from "@angular/router";

@Component({
  selector: "app-profile",
  templateUrl: "./profile.component.html",
  styleUrls: ["./profile.component.css"],
})
export class ProfileComponent {
  id: string = "";

  constructor(private activatedRoute: ActivatedRoute) {
    activatedRoute.params.subscribe((params) => (this.id = params["id"]));
  }
}
```

Om du behöver navigera med länkar så lägger du in det i attributen:

```html
<span routerLink="/profile/1">View profile 1</span>
```

Och med TypeScript så skriver du:

```typescript
import { Component } from "@angular/core";
import { Router } from "@angular/router";

@Component({
  selector: "app-links",
  templateUrl: "./links.component.html",
  styleUrls: ["./links.component.css"],
})
export class LinksComponent {
  constructor(private router: Router) {}

  navigateSomewhere() {
    // View profile 2
    let profileId = 2;
    this.router.navigate(["/profile", profileId]);
  }
}
```

## Mer information

För mer information och fler exempel, läs [dokumentationen](https://angular.io/guide/routing-overview).
