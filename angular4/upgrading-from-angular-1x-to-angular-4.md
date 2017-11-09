# Upgrading from Angular 1.x to Angular 4/5

Reference:  https://vsavkin.com/migrating-angular-1-applications-to-angular-2-in-5-simple-steps-40621800a25b


## 1. Use Angular 4's **UpgradeModule**

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

Assume that the root Angular 1.x module is named `Ng1AppModule`, import `Ng1AppModule` and the above `Ng2AppModule` in `main.ts` and bootstrap the app:

* in the app's `main.ts`, start the app on the browser bootstrapping from the above root ng2+ app module. 
* once the ng2 app module is bootstrapped, call UpgradeModule's bootstrap as below:

```ts
// import polyfills
import 'core-js/es7/reflect'
import 'zone.js/dist/zone'

// import angular2 dpes
import {platformBrowserDynamic} from '@angular/platform-browser-dynamic';

import {Ng1AppModule} from './ng1_app';
import {Ng2AppModule} from './ng2_app';

/**
 * We bootstrap the Angular 2 module first, and then, once it's done,
 * bootstrap the Angular 1 module.
 */
platformBrowserDynamic().bootstrapModule(Ng2AppModule).then(ref => {
  // bootstrap angular1
  (<any>ref.instance).upgrade.bootstrap(document.body, [Ng1AppModule.name]);
});
```


## 2. In all Angular 1 module, export an empty class decorate with @NgModule({})

And then import all those modules in the Root Angular 2+ module

## 3. Upgrade individual directives to components, filters to pipes and services to Angular 2+ services, one by one

## 4. Divide the routes between the Angular 1 and the Angular 2 routers

## 5. Remove Angular 1 when every module has been migrated
  

 