# Dependency Injection

Dependency Injection är ett design pattern för att skapa och använda olika beroenden (dependencies.) Ett beroende är typiskt sätt ett objekt som håller data. Om man exempelvis har ett objekt med API data så kan detta objekt användas med dependency injection och därför räknas som ett beroende. I Angular så kallas dessa beroenden "services".

Man kan beskriva services som globala states om man tänker React termer. Dessa objekt ("services") kan hämtas in i komponenter så att komponenterna kan använda deras funktioner och egenskaper.

Skapa en service genom följande kommando:

```
ng generate service <namn>
```

En service ser ut såhär när den är ny:

```typescript
import { Injectable } from "@angular/core";

@Injectable({
  providedIn: "root",
})
export class MyService {
  constructor() {}
}
```

Det är egentligen en helt vanlig klass. När appen startar så skapar Angular automatiskt en instans av denna klass vilket du kan använda i komponenter. Hämta in objektet genom att lägga till klassen som parameter till constructorn i komponenten:

```typescript
import { Component, Input } from "@angular/core";

@Component({
  selector: "app-test",
  templateUrl: "./test.component.html",
  styleUrls: ["./test.component.css"],
})
export class TestComponent {
  constructor(private myService: MyService) {}
}
```

... när Angular ser komponenten så märker den av constructorn automatiskt och vet att den skall skicka in instansen av `MyService`. Processen av att hämta en service (eller rättare sagt när Angular skickar in objektet) kallas "injection". Själva service objektet (beroendet) kallas "dependency". Det är därför det heter "dependency injection".

Använd detta som en slags global state. Se nedanför för ett exempel.

_Notera för mer avancerad användning: det finns en till del i dependency injection som inte nämns här. Den delen är mer relevant i OOP och behövs inte för denna Angular kurs._

## Exempel

```typescript
// Service
import { Injectable } from "@angular/core";

class Todo {
  description: string;

  constructor(description: string) {
    this.description = description;
  }
}

@Injectable({
  providedIn: "root",
})
export class TodoService {
  todos: Todo[] = [];

  constructor() {}

  addTodo(description: string): void {
    this.todos.push(new Todo(description));
  }
}
```

```typescript
// Komponent (typescript)
import { Component } from "@angular/core";
import { Todo, TodoService } from "../todo.service";

@Component({
  selector: "app-todos",
  templateUrl: "./todos.component.html",
  styleUrls: ["./todos.component.css"],
})
export class TodosComponent {
  constructor(private todoService: TodoService) {}

  get todos(): Todo[] {
    return this.todoService.todos;
  }

  addTodo(description: string): void {
    this.todoService.addTodo(description);
  }
}
```

```html
<!-- Komponent (html/template) -->
<ul>
  <li *ngFor="let todo of todos">{{ todo.description }}</li>
</ul>

<input #desc placeholder="What do you need to do?" />
<button (click)="addTodo(desc.value); desc.value = ''">Add</button>
```

När `todos` uppdateras i `TodoService` så laddas komponenterna om automatiskt (det fungerar alltså som en global state i React). Om man nu vill använda `TodoService` i en annan komponent så går det bra.

## Tips

1. Spara inte persistent data direkt i komponenter; använd services för det (exempelvis användare, todos, posts m.m).
2. Spara temporär data i komponenter och inte i services (exempelvis inputfält innehåll, toggle knappar m.m).
3. Hämta API data i services; lägg inte fetch anropp direkt i komponenter.
4. Använd services för localStorage; lägg inte localStorage kod i ensamma funktioner.
5. Skapa modell klasser separat om de är lite större (5+ egenskaper). I exemplet ovanför så ligger `Todo` klassen innanför `TodoService` filen eftersom klassen är så liten. Använd istället `ng generate class <namn>` eller `ng generate interface <namn>` när klasserna blir större.

## Inbyggda services

Angular har några inbyggda services, exempelvis: `ActivatedRoute` och `Router` som används vid routing.
