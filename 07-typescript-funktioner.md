# Funktioner

I TypeScript måste parametrar och return definieras med datatyper. Se följande exempel:

```typescript
function addNumbers(a: number, b: number): number {
  return a + b;
}
```

Använd `void` för funktioner utan return-värden:

```typescript
function printSomething(): void {
  console.log("Something");
}
```

## Funktioner som typer

För att ta in funktioner som argument till andra funktioner kan man skriva:

```typescript
// Detta kallas en funktion-signatur
function callApi(callback: (a: number, b: number) => string): void {
  // Api code...
}

callApi((a, b) => {
  return "Hello";
});
```

Aliasing (se separat dokument) kan användas för att namnge en funktion-signatur:

```typescript
// Denna är bra för att dokumentera signaturen
type CallbackFunction = (a: number, b: number) => string;

function callApi1(callback: CallbackFunction): any {
  // Api code...
}

function callApi2(callback: CallbackFunction): any {
  // Api code...
}
```
