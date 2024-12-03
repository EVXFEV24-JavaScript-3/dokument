# Introduktion till TypeScript

JavaScript är ett bra verktyg för att bygga webbsidor. Ett speciellt problem visar sig dock i större projekt: det blir svårt att förstå kod då det är dynamically typed &#8212; vilket betyder att JavaScript inte behöver definiera datatyper på exempelvis variabler och parametrar. TypeScript är en fortsättning på JavaScript som lägger till static typing vilket betyder att du explicit kan definiera datatyper. Detta är användbart då kod blir mycket tydligare genom att definiera och förklara saker, som exempelvis variabler och funktioner. Med andra ord, det är lättare att förstå TypeScript kod än JavaScript kod.

Det är viktigt att förstå att den enda riktiga skillnaden mellan JavaScript och TypeScript är hur koden skrivs visuellt. TypeScript är fortfarande samma som JavaScript funktionellt. Alla koncept är samma: variabler, datatyper, funktioner och mer. Ta följande exempel.

Variabler ser ut såhär i JavaScript:

```javascript
// JavaScript
let text = "Hello World!";
```

... men de ser ut såhär i JavaScript.

```typescript
// TypeScript
let text: string = "Hello World!";
```

Båda gör exakt samma sak (JavaScript och TypeScript), men i TypeScript så måste du skriva ut datatypen. Återigen, det är bara hur koden ser ut som skiljer, men vad den gör är fortfarande samma.

För att lära dig TypeScript så gäller det bara att komma ihåg vilka syntax regler som gäller. Det finns många resurser för att lära sig TypeScript, och i kommande dokument så finns förklaring och exempel. Läs vidare i detta repository om:

1. Datatyper och variabler
2. Funktioner
3. Klasser
4. Interfaces
5. Aliasing
