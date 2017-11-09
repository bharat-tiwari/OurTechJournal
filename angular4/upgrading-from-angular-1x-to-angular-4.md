# Upgrading from Angular 1.x to Angular 4/5

Reference:  https://vsavkin.com/migrating-angular-1-applications-to-angular-2-in-5-simple-steps-40621800a25b


Use Angular 4's **UpgradeModule**

Steps:

1. Create an Angular 4 root component with empty body and in its template, have an empty `<div>` element attributed with Angular 1.x's `ng-view`:

_src/modules/app/components/app.component.ts_
```ts
import {Component} from '@angular/core';

@Component({
  selector: 'root-cmp',
  template: `
    <div class="ng-view"></div>
  `,
})
export class RootCmp {}
```

2. Create a root Angular 4 module that instantiates Angular 4's **UpgradeModule** utility and bootstraps the above component.


_src/modules/app/app.ts_
```ts
import {NgModule} from '@angular/core';
import {BrowserModule} from '@angular/platform-browser';
import {UpgradeModule} from '@angular/upgrade/static';

@NgModule({
  imports: [
    BrowserModule,
    UpgradeModule,
  ],
  bootstrap: [RootCmp],
  declarations: [RootCmp]
})
export class Ng2AppModule {
  constructor(public upgrade: UpgradeModule){}
}
```



Next:
* in the app's `main.ts`, start the app on the browser bootstrapping from the above root ng2+ app module. 
* once the ng2 app module is bootstrapped, call UpgradeModule's bootstrap as below:

```ts
  

 