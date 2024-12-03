# Datatyper och variabler

Datatyperna i TypeScript är mestadels samma som datatyperna i JavaScript. TypeScript har:

- string
- number
- boolean
- array
- objekt

Det finns också några speciella typer:

- union
- any
- interface
- void

Egentligen så räknas inte de speciella typerna som "riktiga" datatyper men det kan ibland vara hjälpsamt att behandla dem som datatyper.

Det som är speciellt med TypeScript är att datatyper alltid måste skrivas ut. Datatyper måste exempelvis definieras för variabler och parametrar:

```typescript
let myNumber: number = 1;
let myString: string = "Hello World!";

function addNumbers(a: number, b: number): number {
  return a + b;
}
```

## Variabler

När en en variabel har blivit definierad, med en datatyp, så kan den inte ändras. I JavaScript så är följande möjligt:

```javascript
let someVariable = 5;
someVariable = "Hello World!"; // Ok
someVariable = 6; // Ok
```

Det är inte möjligt i TypeScript:

```typescript
let someVariable: number = 5;
someVariable = "Hello World!"; // Fel
someVariable = 6; // Ok
```

## Arrayer

Arrayer definieras med typen och hakparanteser efter, som följande:

```typescript
number[]

string[]

boolean[]

User[]
```

För att skapa en array-variabel görs följande:

```typescript
let myNumbers: number[] = [1, 2, 3];
```

## Objekt

Objekt(-typer, klasser) definieras genom namnet på typen. Låt säga att du har följande klass:

```typescript
class User {
  name: string;
  password: string;
}
```

_Mer information om klasser finns i ett separat dokument._

Med den klassen hade en `User` variabel definierats med:

```typescript
let user: User = new User();
```

Undvik att skapa anonyma objekt (`{}`) då det förstör poängen med att använda TypeScript. Om du verkligen måste ha det så kan du använda datatypen `any`:

```typescript
let anyObject: any = { name: "Ironman", age: 5 };
```

## Unions, undefined och null

Ibland så vill man kunna ha en variabel som håller ett värde eller null/undefined. I dessa fall kan unions utnyttjas:

```typescript
// Detta tillåter att värdet på variabeln kan vara ett nummer och null, dock inte båda samtidigt.
let myNumOrNull: number | null = null;
```

Ett annat exempel:

```typescript
// Detta tillåter att värdet på variabeln kan vara ett nummer, en sträng och null, dock inte alla samtidigt.
let someValue: number | string | null = "Hello World!";
```
