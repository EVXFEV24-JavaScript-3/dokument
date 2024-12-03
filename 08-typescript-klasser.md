# Klasser

Fält (egenskaper) kan definieras i TypeScript klasser:

```typescript
class Hero {
  name: string;
  age: number;
  superpowers: string[];
}
```

Egenskaper initialiseras som vanligt (med constructors):

```typescript
class Hero {
  name: string;
  age: number;
  superpowers: string[];

  constructor(name: string, age: number, superpowers: string[]) {
    this.name = name;
    this.age = age;
    this.superpowers = superpowers;
  }
}
```

Deklarera metoder (funktioner i klasser) som vanligt, men med TypeScript syntax:

```typescript
class Hero {
  name: string;
  age: number;
  superpowers: string[];

  constructor(name: string, age: number, superpowers: string[]) {
    this.name = name;
    this.age = age;
    this.superpowers = superpowers;
  }

  greet(name: string): void {
    console.log("Hello " + name + ", my name is " + this.name);
  }
}
```

## Getters och setters

En getter är en slags funktion som är till för att hämta data från ett objekt. De fungerar egentligen som vanliga funktioner, men de har en speciell syntax. Skillnaden är att man inte måste skriva `()` på en getter:

```typescript
class MyClass {
  myFunction(): string {
    return "Hej!";
  }

  get myGetter(): string {
    return "Hej!";
  }
}

function main() {
  let value = new MyClass();

  // Vanlig funktion syntax
  console.log(value.myFunction());

  // Getter funktion syntax
  console.log(value.myGetter);
}
```

Setters fungerar på samma sätt, men de är till för att ändra på data i ett objekt:

```typescript
class MyClass {
  someVar: number = 5;

  myFunction(someVar: number): void {
    this.someVar = someVar;
  }

  set mySetter(someVar: number): void {
    this.someVar = someVar;
  }
}

function main() {
  let value = new MyClass();

  // Vanlig funktion syntax
  value.myFunction(4);

  // Getter funktion syntax
  value.mySetter = 4;
}
```

Fördelen med getters och setters är att man kan lägga in funktionalitet i dem, medans man samtidigt har variabel-syntax.

## Visibility och access modifiers

Egenskaper och metoder (funktioner) kan ha visibility/access modifiers: `public`, `private` och `protected`. Protected är inte oviktig och förklaras inte här, men titta gärna upp den själv.

Public betyder att alla andra filer kan nå egenskapen eller metoden. I vanlig JavaScript är alla egenskaper och metoder alltid public.

Private betyder att man endast kommer åt egenskapen eller metoden inom samma klass. Se nedanför för ett exempel:

```typescript
// some-file.js
export class MyClass {
  private value: number = 5;

  public printValue() {
    // Ok, man kan alltid komma åt en variabel inom samma klass
    console.log(value);
  }
}
```

```typescript
// some-other-file.js
import { MyClass } from "./some-file.js";

function someFunction() {
  let obj = new MyClass();

  // Inte Ok, då 'value' är private
  console.log(obj.value);

  // Ok, då 'printValue' är public
  obj.printValue();
}
```

## Interfaces

Interfaces liknar klasser: de innehåller egenskaper, funktioner och är till för att skapa objekt. De skiljer dock lite i hur de fungerar. För denna kurs är interfaces oviktiga. Använd interfaces som en slags container till API data.

Om du behöver hämta ett objekt från ett API, skapa ett interface åt det:

```typescript
interface ApiData {
  someProperty: number;
  someOtherProperty: string;
}
```

I interfacet lägger man in alla egenskaper som man vill hämta från API:et. Om du inte vill ha med en viss egenskap utelämnas den från interfacet. Referera till video resurser för exempel i projektbygge videor.
