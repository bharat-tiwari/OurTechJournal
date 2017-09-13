#Lazy Loading of modules

In Angular 2 / 4, you can divide the various functionalities / features of your application into modules. Taking the example of our Photo Albums application, Home page/view , where we show the albums of the user, could be the default/too module. The 'Photos' view, that shows photos inside an album doesn't need to be loaded from the starting of the app, it could be loaded lazily later when user selects an album. We can wrap all the components needed for Photos view in a child module of the app's root module . Similarly, the 'User Settings' component could be wrapped in a separate child module. 
And then we can configure our Router to load Photos and User Settings modules lazily.

This helps to bring down the initial size of the application bundle thereby improving performance of the application.

Lets say, we have 2 components used in an album's `Photos` view:
1. PhotosGrid - a grid view of photos in an album
2. PhotoDetails - shows an individual photo along with its details like date and caption for each photo.

In order to have these components loaded lazily, we have to include these components inside a separate module, lets call it 'photos' module created under `photos` folder:

#### 1. First setup the routing for the photos module:

`./app/modules/photos/photos.routes.ts`
```js
import { Routes } from '@angular/router';

import { PhotosGrid } from './photos/grid.component';
import { PhotoDetails } from './photos/details.component';


export const routes: Routes = [
    { path: '', component: PhotosGrid },
    { path: '/:id', component: PhotoDetails }
];
```
#### 2. Next, use this router in the `photos` module:

`./app/modules/photos/photos.module.ts`

```js
import { NgModule } from '@angular/core';
import { RouterModule } from '@angular/router';

import { PhotosGrid } from './photos/grid.component';
import { PhotoDetails } from './photos/details.component';
import { routes } from './photos.routes';


@NgModule({
  imports: [
    RouterModule.forChild(routes)
  ],
  declarations: [PhotosGrid, PhotoDetails]
})
export class LegalModule { }
```

Note the use of `RouterModule's` `forChild` method above.

#### 3. Use `loadChildren` in the root module's route configuration
Finally, use `loadChildren` in the root module's route configuration


```js
import { BrowserModule } from '@angular/platform-browser';
import { NgModule } from '@angular/core';
...
import { Route, RouterModule } from '@angular/router';

import { AppComponent } from './app.component';
import { LoginComponent } from '../../components/login/app-login.component';
import { AlbumComponent } from '../../components/home/app-home.component';

const ROUTES: Route[] = [
  { path: '', component: LoginComponent},
  { path: 'albums', component: AlbumComponent }
  { path: 'photos', loadChildren: './photos/photos.module#PhotosModule' }

]

@NgModule({
  declarations: [
    AppComponent,
    LoginComponent,
    HomeComponent
  ],
  imports: [
    ...
    RouterModule.forRoot(ROUTES)
  ],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule { }
```