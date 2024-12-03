# Projektstruktur

Det finns oändligt många sätt att strukturera projekt på. Vad som följer är ett exempel på hur du kan strukturera dina Angular appar. Det viktiga att tänka på när det kommer till att strukturera ett projekt är att alltid vara konsekvent. Bestäm regler och mönster i förväg och håll till dem.

Det finns tre saker att planera vid ett projekt när det kommer till struktur:

1. Mappar och filer (var filer ska ligga och vilka mappar ska finnas)
2. Namngivning (i kod och filer)
3. Indentering och formatering (på if-satser, funktioner o.s.v)

Delarna beskrivs nedanför.

## Mappar och filer

I de flesta projekt finns det typiskt sätt följande delar: komponenter, sidor (views eller pages), API kod, hjälpkod och styling. Därför så kan ett projekt följa en mappstruktur som ser ut som följande:

| Mapp         | Beskrivning                                                                                                                         |
| ------------ | ----------------------------------------------------------------------------------------------------------------------------------- |
| services     | Här läggs all kod som ansluter din kod med utsidan och andra generella tjänstobjekt. Detta innebär API-anropp exempelvis.           |
| components   | Här läggs alla generella komponenter såsom knappar, titlar och headers.                                                             |
| modules      | Här läggs alla moduler om man har några.                                                                                            |
| pages, views | Här läggs alla "sido"-komponenter. Alltså komponenter som bygger upp hela webbsidor, som exempelvis en startsida eller kontaktsida. |
| utils        | Här läggs alla hjälp- klasser och funktioner. All kod som är generell och kan användas lite överallt.                               |

## Namngivning

Många saker behöver namn i Angular: komponenter, filer, funktioner, variabler och mer. Det är bra att bestämma regler i början av ett projekt och följa dem, som exempelvis:

1. `camelCase` för funktioner
2. `camelCase` för variabler
3. `PascalCase` för klasser
4. `snake_case` för filnamn
5. `PascalCase` för filer med komponenter
6. `snake_case` för mappar

Vilka regler som ett projekt består av är helt och hållet preferens. Det som är viktigt är att alla i projektet alltid följer samma mönster.

## Indentering och annan formatering

Indentering och annan generell formatering är viktig. Bestäm i förväg hur många mellanslag en "indent" ska bestå av (exempelvis 2, eller 4 som är vanligast). Bestäm också i förväg hur spacing och måsvingar ska hanteras. If-satser som innehåller en rad kod kan skippa måsvingar exempelvis, men hur bör det skrivas? Det finns många olika sätt att skriva på, som visas i följande exempel:

```
// Det vanliga
if (x > 5) {
  console.log("x > 5 = true");
}

// Utan måsvingar
if (x > 5)
    console.log("x > 5 = true");

// Utan måsvingar, på samma rad
if (x > 5) console.log("x > 5 = true");
```

Samma sak gäller för loopar. Liknande saker gäller för funktioner och klasser.

Kommentarer är också en del som bör bestämmas. Vad skall kommenteras, och hur mycket?
