# SASS Lists

List in SASS is a data structure similar to arrays of most of the programming languages. Its a series of values assigned to a SASS variable.

```scss
 $myColors = #aaa #bbb #ccc #ddd;
```
  
  

The values in a list can of a single type(e.g. all numeric or all string) or mixed type. The values or items of a list can be  separated by commas or by spaces. 

Also, the values in the list can be specified within quotes or without any quotes. If quotes are used, we have to use `unquote` function when using the value.

```scss
 $awesomeKit = #ccc, 2px '#aaa'; 
```


A value in a list can be accessed by its index using the `nth` function.

```scss
  .awesomeness {
     background-color: nth($awesomeKit, 1);
     border-radius: nth($awesomeKit, 2);
     border-color: unquote(nth($awesomeKit, 3));

  }
```

Like arrays in other languages, Lists are useful to loop through a series of values. However, to access a particular value in a set, SASS Map is better option which is more like a dictionary of key-value pairs that allows to access items using their keys. 






