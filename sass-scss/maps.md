# SASS Maps

A Map in SASS is a data structure similar to `dictionary` in most of the other programming languages (or Maps in ES6). Its a set of key-value pairs. A very common use case of map is to define a set of theme colors like below:

```scss
$siteThemeColors (
    default: #ccc,
    primary: #3399ff,
    warning: #ff9900,
    success: #33cc33,
    danger: #ff3300 
)
```

To retrieve the a value from the map , you use `map-get` function:

```scss

.primary {
  background-color: map-get($siteThemeColors, primary);
  color: #fff;
}

.success {
  background-color: map-get($siteThemeColors, success);
  color: #fff;
}

```
