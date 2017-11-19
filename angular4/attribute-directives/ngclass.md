#ngClass directive

```js
import { Component } from '@angular/core`;

@Component({
    selector: 'ngClass-example', 
    template: `<div>
        <h2>ngClass Example</h2>
        <!-- 👇 note the use of ngClass with ng expressions -->
        <div [ngClass]="{greenText: userPassed, redText: !userPassed, resultBG: true}">
            {{result}}
        </div>
    <div>`,
    styles: [
        .greenText {color: green},
        .redText {color: red},
        .resultBG {background-color: '#ddd'}
    ]
})
export class NgClassExample implements OnInit {
    @Input result;
    userPassed: boolean = false;
    ngOnInit(){
        if (result > 40){
            userPassed = true;
        }
    }
}
```



