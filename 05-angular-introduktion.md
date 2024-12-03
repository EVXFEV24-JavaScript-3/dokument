# Introduktion till Angular

JavaScript, HTML och CSS är bra verktyg för att bygga webbsidor, men det krävs ofta mycket repetetiv kod för att skapa större projekt. Det finns mycket snabbare, och för många också roligare, sätt att utveckla webbsidor på. Angular är ett ramverk som ändrar på hur du utvecklar webbsidor. Det finns även andra bibliotek och ramverk som är liknande, som exempelvis React, Svelte och Vue.

Angular är utvecklat med programmeringsupplevelse i baktanken. Poängen med biblioteket är att göra utveckling och testning av webbsidor smidigare, snabbare och roligare. Angular är väldigt populärt &#8212; ett av de mest populära ramverken för webben &#8212; och har också därför ett stort antal tillägg (som i sig är bibliotek och ramverk.)

Ett ramverk är en kod som är skriven för att flera skall kunna använda. De ger utvecklare tillgång till funktioner och klasser som kan vara hjälpsamma vid utveckling. Det som skiljer Angular från exempelvis React är att Angular styr mycket mer av flödet i en applikation. I React har du mer kontroll. Detta kommer med fördelar och nackdelar. Fördelen med Angular (ramverk, mindre kontroll) är att det är enklare, och det går snabbare, att implementera saker eftersom mycket redan hanteras av ramverket. Nackdelen är att du inte kan göra vad du vill för att du måste följa vissa mönster.

## Hur Angular fungerar

Angular är ett komponent-baserat ramverk (likt React.) I ett komponent-baserat ramverk byggs alla UI-komponenter upp med återanvändbara delar kod. En knapp, exempelvis, är en komponent som förekommer ofta på de flesta webbplatser, och med Angular skapar du typiskt sätt en knapp-komponent. Man kan tänka att Angular tillåter en att skapa egna HTML tags med egen styling och funktionalitet. Även om knappar, som exempel igen, redan finns i HTML, så brukar man vilja ha extra funktionalitet och styling, vilket Angular hjälper till med. Detta gäller även för andra vanligt förekommande komponenter, såsom sidebars, navbars, grafer, input-fält och så vidare. Ett simpelt exempel på hur en knapp-komponent kan se ut är:

```typescript
import { Component, EventEmitter, Input, Output } from "@angular/core";

@Component({
  selector: "app-button",
  templateUrl: "./button.component.html",
  styleUrls: ["./button.component.css"],
})
export class ButtonComponent {
  @Input()
  title: string = "";
  @Output()
  onClick = new EventEmitter<void>();

  handleClick() {
    this.onClick.emit();
  }
}
```

```html
<button (click)="handleClick()">{{ title }}</button>
```

Angular delar upp alla komponenter i tre delar: funktionalitet (TypeScript), struktur (HTML) och design (CSS). Varje del har typiskt sätt en egen fil (.ts, .html och .css). Alla dessa tre delar tillsammans bildar en helt fungerande komponent.

Typiskt sätt delas komponenter in i ett hierarki. Det börjar med små komponenter som exempelvis knappar och titlar, som kombineras för att skapa större komponenter såsom navbars och sidebars, som kombineras för att skapa hela sidor (ofta kallade 'pages' och 'views'.) Det finns dock inga regler för hur komponenter ska se ut eller vad de ska göra &#8212; det är något som utvecklaren bestämmer själv.
