# Events

Registrera event listeners i Angular med attributer:

```html
<button (click)="myFunction()">Click Me!</button>
```

Innanför citat `""` går ett template statement. Det vanligaste är att anropa funktioner, som du kan se i exemplet ovanför.

Om du behöver komma åt `event` objektet så kan du skriva `$event`:

```html
<button (click)="logInfo($event)">Click Me!</button>
```

Detta gäller för andra events också, det gäller bara att sätta `()` runtom, såsom `(change)`, `(keyup.enter)` och `(focus)`. Se [dokumentationen](https://angular.io/guide/event-binding) för mer information och länk till en lista på events.
