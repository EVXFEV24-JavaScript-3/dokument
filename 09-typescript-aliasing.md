# Aliasing

Skapa aliases och synonymer i TypeScript med `type` nyckelordet. Här är ett exempel:

```typescript
type MyOwnType = number;
```

Vid användning av `MyOwnType` så kommer det betyda samma sak som `number`. Detta är speciellt användbart för callback signaturer (se dokumentet om funktioner för ett exempel). Det förekommer i andra fall väldigt sällan, men här är ett exempel:

```typescript
let myNumber: MyOwnType = 8;
```
