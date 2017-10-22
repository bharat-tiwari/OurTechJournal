# ng-content

`ng-content` in Angular 2/4 is equivalent to transclusion in AngularJS.

When defining a component, if you are anticipating some inner HTML being included in between the component start and closing tags where the component is used, then in order to have angular correctly render that inner HTML content, we need to use `<ng-content>` in the component's template.

Lets say we have a `header` component and we want the views that would use this `header` component to have an ability to provide an image or some font-awesome icon that the view wants to be rendered inside the `header`. In that case, we would define `header` component as below:

```js
@Component({
  selector: 'header',
  template: `
    <div>
      <h1>{{title}}</h1>
      <ng-content></ng-content>
    </div>
  `
})
class HeaderComponent {
...
}
```


The above component can then be used in views as below:

```html
<header title="Settings">
  <image src="images/logo.png" />
</header>
```

The above will render the header component HTML as below:

```html
<div>
<h1>{{title}}</h1>
<image src="images/logo.png" />
</div>
```



