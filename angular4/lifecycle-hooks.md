#Lifecycle Hooks of Angular Component
Angular allows us to define some functions for a component that it will invoke at various major milestones of the component's life cycle as it gets created, changed or destroyed. Below are the lifecycle hooks that Angular allows us to define:

### 1. ngOnChanges:
This function would be called whenever there is change detected in one of the input data-bound property. 
To get a data passed on from its parent component, the child component class would have some properties declared with  `@Input` decorator. `ngOnChanges` is invoked in the child component, whenever a change occurs to the value of these input bound properties on the parent component.

This hook would also be called before the data property is initialized i.e. before the `ngOnInit` hook. 

The callback function for this hook would receive a `SimpleChanges` object that contains the **previous** and **current** values of the inputs properties. 

As this hook gets called very often, you should keep the code in this hook at minimum possible to not let the performance of the app impacted.

### 2. ngOnInit:
This hook is called after the first `ngOnChanges`, when the component is ready with its initial state and has received initial values of its input data-bound properties.

This hook is used to add any code that should execute once the component has initialized.

This hook is fired only once

This hook is fired before any of the child directive properties are initialized.


| Hook | Purpose and Timing |
|----|----|
| ngOnChanges()| Respond when Angular (re)sets data-bound input properties. The method receives a SimpleChanges object of current and previous property values. Called before ngOnInit() and whenever one or more data-bound input properties change.|
| ngOnInit()| Initialize the directive/component after Angular first displays the data-bound properties and sets the directive/component's input properties. Called once, after the first ngOnChanges().|
|ngDoCheck()|Detect and act upon changes that Angular can't or won't detect on its own.Called during every change detection run, immediately after ngOnChanges() and ngOnInit().|
Respond after Angular projects external content into the component's view. Called once after the first ngDoCheck(). A component-only hook.
ngAfterContentChecked()	
Respond after Angular checks the content projected into the component.
Called after the ngAfterContentInit() and every subsequent ngDoCheck().
A component-only hook.
ngAfterViewInit()	
Respond after Angular initializes the component's views and child views.
Called once after the first ngAfterContentChecked().
A component-only hook.
ngAfterViewChecked()	
Respond after Angular checks the component's views and child views.
Called after the ngAfterViewInit and every subsequent ngAfterContentChecked().
A component-only hook.
ngOnDestroy	
Cleanup just before Angular destroys the directive/component. Unsubscribe Observables and detach event handlers to avoid memory leaks.
Called just before Angular destroys the directive/component.
