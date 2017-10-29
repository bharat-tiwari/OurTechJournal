#Media Queries

Media Queries allow us to define CSS styling rules for web page elements by querying on on the **device type** and/or certain **features** of the device on which the web content is currently being viewed or rendered.

In a single media style rule, multiple queries for device types or features can be combined using logical operators - `and` , `not` or `only`. 



Syntax for writing a CSS Media rules:
 `@media  <<device type or feature query or comma-separated list of queries>> <<logical operator>> <<device type or feature query or comma-separated list of queries>>....`
 
 
 examples: 
 
 ```css
 @media screen {
  body { background-color: #ddd; }
 }
 ```
 
```css
@media screen, print {
  body { background-color: #ddd; }
}
```


Using CSS media query for Responsive Web Design (RWD):

Below css media rules define how our web content would be rendered on devices of type `screen` and different sizes - usually we target 

```css

#body-container { 
      width: 950px; 
      margin: 0 auto;
}
#section-container { 
      width: 690px; 
      float: left;
}
#side-container { 
      width: 260px; 
      float: left;
}
 
/* media rule for devices for upto max width of 950px */
@media screen and (max-width:950px) {
  #body-container { width: 100%; }
  #section-container { width: 70%; }
  #side-container { width: 30%; }
}

/* for devices having width of 640 or less, make section and side occupy whole width */
@media screen and (max-width:640px) {
  #section-container { width: 100%; }
  #side-container { width: 100%; }
}


/* for devices having width of less than 320px, 
if width of container is made responsive to such 
smaller screen size contents won't be visible properly. 
So set body-container size fixed to 320px & if screen size is less,
then horizontal scroller would be enabled 
to see the contents which are beyond the visible screen area   */

@media screen and (max-width:320px) {
  #body-container { width: 320px; }
}



```


Also note, usually, we add below `viewport` <meta> tag in the header of our page HTML to have it respond to device screen size on phones or tablet:

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

This tells the device that the content of the web page needs to be equal to the device width and keep the contents initial scale to 100% and do not scale it up or down.


 
 
 
 
 