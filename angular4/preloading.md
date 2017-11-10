# Preloading 

Preloading is similar to lazy-loading except that these modules get loaded immediately after the required eager modules are  loaded whereas lazy-loaded modules get loaded only when user navigates to their routes.
Thus Preloading modules can be used to load the modules faster compared to lazy-loaded modules while still giving us the benefit that lazy-loading modules provide i.e. faster initial loading of the app by not having to load those modules during initial rendering of the app.

To Preload all the modules that are configured to be lazy-loaded, use the `PreloadAllModules` as strategy for preloading in the root app module's as shown below: 

```ts

import { BrowserModule } from '@angular/platform-browser';
import { NgModule } from '@angular/core';
import { HttpModule } from '@angular/http';
import { Route, RouterModule, PreloadAllModules } from '@angular/router';

import { AppComponent } from './app.component';
import { LoginComponent } from '../login';
import { HomeComponent } from '../home';   
import { PhotoService, UserService } from '../../services';



const ROUTES: Route[] = [
  { path: '', component: LoginComponent},
  { path: 'home', component: HomeComponent},
  { path: 'photos', loadChildren: './photos/photos.module#PhotosModule' }
]

@NgModule({
  declarations: [
    AppComponent,
    LoginComponent,
    HomeComponent
  ],
  imports: [
    BrowserModule,
    HttpModule,
    RouterModule.forRoot(ROUTES, { preloadingStrategy: PreloadAllModules })
  ],
  providers: [
    PhotoService,
    UserService
  ],
  bootstrap: [AppComponent]
})
export class AppModule { }
```

With `PreloadAllModules` strategy used above, all the lazy-loaded modules would be 'preloaded' thereby saving us from the bit of network latency that lazy-loading would have costed us. 

If you want to have some selected modules, that are not usually used by the user, still lazy-loaded , some custom configuration can be used for configuring few modules to be preloading and few to be lazy-loading.