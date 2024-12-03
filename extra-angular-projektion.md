# Komponent projektion

Innanför komponent tags kan man lägga in valfria element:

```html
<app-my-component>
  <div>Inner content</div>
</app-my-component>
```

Få in dessa element i en komponent genom `<ng-content></ng-content>`:

```html
<!-- my-component.component.html -->
<ng-content></ng-content>
```

... vilket resulterar i:

```html
<!-- my-component.component.html -->
<div>Inner content</div>
```

Detta koncept är samma som `children` props i React.
