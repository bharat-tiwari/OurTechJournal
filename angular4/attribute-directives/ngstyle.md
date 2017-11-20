#ngStyle directive

```js
import { Component, Input } from '@angular/core`;

@Component({
    selector: 'ngStyle -example', 
    template: `<div>
        <h2>ngStyle Example</h2>
        <!-- 👇 note the use of ngStyle with ng expressions -->
        <div [ngStyle]="{'color': resultColor, 'background-color': resultBG}">
            {{result}}
        </div>
    <div>`,
    
})
export class NgStyleExample implements OnInit {
    @Input result;
    resultColor: string = 'green';
    resultBG = '#ddd';
    
    ngOnInit(){
        if (result < 40){
            this.resultColor = 'red';
        }
    }
}
```



