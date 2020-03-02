# Shared Modules

In your Angular app, you might have some services, pipes or directives that you would like to share across your other app modules, be it one of the eagerly-loaded module or lazy-loaded module.

However, with lazy-loaded modules being loaded lazily when user navigates to one of its components, it might happen that the common services, that were already loaded along with the eagerly-loaded modules, get loaded again.

To avoid multiple times loading of your common services, Angular allows us to include all these common services, providers, pipes into a common **shared** module that should return a `forRoot` static method with a return type of `ModuleWithProviders`: `static forRoot(): ModuleWithProviders`

```typescript
import { NgModule, ModuleWithProvides } from '@angular/core';
import { someCommonService } from '../common/services';
import { someCommonPipe } from '../common/pipes';
import { someCommonDirective } from '../common/directives';

@NgModule({
  decloarations: [
    someCommonPipe,
    someCommonDirective
  ],
  exports: [
    someCommonPipe,
    someCommonDirective
  ]
})
export class ASharedModule {

  static forRoot: ModuleWithProviders(){
    return {
      ngModule: SharedModule,
      providers: [someCommonService]
    }
  }

}
```

👆, above, inside the `@NgModule` decorator's metadata, we only specify `declarations` and `exports` to declare and export our common pipes and directives, but no `providers`.

The `providers` are actually returned as part of `ModuleWithProviders` type of object returned by the static `forRoot` method we implemented inside the module class.

## importing shared module in the app's root module

Once we bundle our common service/pipes/directives in a common/shared module as above, we can have this shared module provided by our app's root module by calling its `forRoot` method as shown below:

```typescript
import { BrowserModule } from '@angular/platform-browser';
import { NgModule, HttpModule, RouterModule } from '@angular/core';
import { ASharedModule } from './common/SharedModule;
import { AppComponent } from './app.component'

@NgModule({
  imports:[
    BrowserModule,
    FormsModule,
    HttpModule
    ASharedModule.forRoot(),
    RouterModule.forRoot(routes)
  ],
  exports:[],
  declarations:[
    AppComponent
  ],
  providers:[

  ],
  bootstrap:[AppComponent]
})
export class AppModule {}
```

