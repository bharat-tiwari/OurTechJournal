# CSS3 Transitions

CSS3 Transitions allows us to change the value of another CSS property from one value to another over a specified duration of time.

The `transition` property takes below format:

```css
.myClass { 
    transition: [transition-property] [transition-duration] [transition-timing-function] [transition-delay] 
}
```

For example, to have the background color property value of a div transitioned from its original value to a new value, we can have something like below:

```css
.myClass {
  background-color: #eeeeee;
  transition-property: background-color 10s ease 1s;
  &:hover{
    background-color: #ff9900;
  }
}
```

Above is short-hand for specifying below 4 transition related properties:

```css
.myClass {
  transition-property: background-color; 
  transition-duration: 10s; 
  transition-timing-function: ease; 
  transition-delay: 1s;
}
```

| Tables        |
| ------------- |
| [JSFiddle](https://jsfiddle.net/tiwarib/u35vg0o1/#tabs=html,css,result) |


















