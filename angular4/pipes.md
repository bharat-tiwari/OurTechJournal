# Pipes

Pipes in Angular 2+ are equivalent of filters in AngularJS.

It comes built-in pipes like `UpperCase`, `LowerCase`, `Currency`, `Date`. Like filters, Pipes can also be custom defined.

To create a Pipe, define a class that implements `PipeTransform` interface and decorate it with @Pipe as shown in below code:

```js
import { Pipe, PipeTransform } from '@angular/core';

@Pipe ({name: 'SortBy'})
export default class SortByPipe implements PipeTransfrom {
    transform(objArray: any[], sortByKey: string) {
        return objArray.sort((a, b) => b[sortByKey] - a[sortByKey]);
    }
}
```


* The `name` property in the the `@Pipe` decorator's metadata object specifies the name by which we will refer to this Pipe in the rest of the code of the app like below:

```html
<ul>
    <li *ngFor="let book of books | SortBy: 'title'">
        {{book.title}} - <i> by {{book.author}} </i>
    </li>
</ul>
```


* Because the class implements `PipeTransform`, it requires us to implement a `transform` method in the class that will contain our actual code to format the value on which this pipe would be invoked. 
* 1st parameter of the `transform` method is the value which this pipe needs to format or transform. This is the value of the variable that we have before the `|` symbol (in above example, the first parameter to the transform method would be the `books` variable's value.)
* After the 1st parameter, the transform method can have any number of parameters, the values of these parameters are provided by a comma separated list of values after the `:` symbol is the pipe's usage.






  


