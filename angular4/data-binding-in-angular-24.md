#Data Binding in Angular 2/4

## One-way binding - from JS(Component) to HTML

<div class="maroon h3">Interpolation</div>

```js
<h1>{{pageTitle}}</h1>
```


<div class="maroon h3">Property Binding</div>


```js
<img [src]="imageLink">
<input type="number" [value]="payment.amount" />
```

## One-way binding  - from HTML To JS(Component)

<div class="maroon h3">Event Binding</div>

```js
<button (click)="onLoginClick">Login</button>
```


## Two-way Binding
```js
<input type="text" [(ngModel)]="email" />
```
