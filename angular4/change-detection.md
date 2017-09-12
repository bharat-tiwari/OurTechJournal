# Change Detection:
Its the feature of Angular 2/4 that can precisely detect any change in the state of the application at any given point of time and get it reflected on the UI by updating the DOM.

ReactJS uses Redux to keep track of state of the application and updates the Virtual DOM which gets reflected on the UI. React uses the concept of diffing the DOM of the new state vs the previous state and only renders the difference.

Two things framework needs to know when a change happens in Application State:
- what has changed in our model
- whats the affected part in the DOM that needs to be updated

## What causes change:
- Events - click, mouseOver, keyUp, Submit...
- XHR - fetching data from a remote server
- Timers - setTimeout(), setInterval()

All of the above are asynchronous. This means, basically whenever some asynchronous operation happens, its likely that the application state might have changed and now Angular now somehow should update the view/UI.

## Who notifies Angular of the state change?
- Zones

Angular uses its own zone API - called NgZone.

Angular has a class called `ApplicationRef` , which is like a reference to the Application state. It keeps listening to NgZone's `OnTurnDone` event. When this event is fired, a method called `tick()` is called. Inside the `tick()` method, Angular loops through each of the `changeDetectorRefs` in the application and calls its `detectChanges()` method.

```js
// very simplified version of actual source
    class ApplicationRef {  
        changeDetectorRefs:ChangeDetectorRef[] = []; 
        constructor(private zone: NgZone) {    
             this.zone.onTurnDone      
                 .subscribe(() => this.zone.run(() => this.tick());  
        }  
    
       tick() {    
           this.changeDetectorRefs      
               .forEach((ref) => ref.detectChanges());  
       }
    }
```

Each component in the angular application has an instance specific ChangeDetectorRef variable. This allows us to control when to trigger a change detection check for each component individually.

Angular Application is basically a component tree, and because each component has its own `ChangeDetectorRef`, we can view this component tree as a tree of ChangeDetectors with data flowing from top to bottom.

After every change Detection loop, the changeDetection gets stable.
Therefore, if any ChangeDetection causes any additional side effect after the first run, Angular will throw an error.

## Will this impact the performance?
While Angular loops through all the change-detectors every time a changeDetector's `turnDone` event is triggered by any component, it can do it extremely fast.

This is because:
#### 1. Angular generates VM friendly code: 
Angular creates ChangeDetector classes at the runtime for each component.

#### 2. Smart Change Detection 
When a change is triggered in one of the component, Angular application can be made to run the ChangeDetection loop in a smarter way, so that instead of looping thru Change-Detectors of all of the components, it figures out what path of the component tree is affected by the change and only runs those change-detectors.

So, how do we make Angular application smarter for running the ChangeDetection loop only for the affected components?

By using some data patterns that would tell us for sure when something would change or not. These patterns are Immutables and Observables. 

### Using Immutables:
https://blog.thoughtram.io/angular/2016/02/22/angular-2-change-detection-explained.html



```js
    @Component({  
        template: `    
          <h2>{{vData.name}}</h2>    
             <span>{{vData.email}}</span>  
        `,  
        changeDetection: ChangeDetectionStrategy.OnPush
    })
    class VCardCmp {  
       @Input() vData;
    }
```

### Using Observables:

Observables allow us to subscribe to change to some value. Thus we can react to or execute a code when some Observable value changes.

We can inject the component instance's ChangeDetectRef in its constructor via dependency Injector. And the call its API's detectChanges method to trigger ChangeDetection for this component.
We can also call its API's markForCheck() method in which case Angular will loop the ChangeDetection for all and only the components for the path of this one to all the way to the root, but only the components in this path , the other components' ChangeDetection will not be triggered.

Once the ChangeDetection loop run is over, it'll restore the OnPush state for all the components in the tree.
