#Angular 4 Routing

## Specify base href in index.html:

```html
<base href='/'>
```


Add a `<base>` tag in the `<head>` section of index.html as below:

```html
<!doctype html>

<html lang="en">
<head>
  <meta charset="utf-8">
  <title>Momentz4ever</title>
  <base href="/">

  <meta name="viewport" content="width=device-width, initial-scale=1">
  <link rel="icon" type="image/x-icon" href="favicon.ico">
</head>

<body>
  <app-root>Loading...</app-root>
</body>
</html>
```


## Setting up Basic Routes Array:

```ts
...
import { Route, RouterModule } from '@angular/router';
...

const ROUTES: Route[] = [
  { path: '', component: LoginComponent},
  { path: 'home', component: HomeComponent},
  { 
    path: 'albums', 
    component: UserAlbumsComponent
  },
  { 
    path: 'albums/:id', 
    children: [
      { path: '', component: AlbumDetailsComponent },
      { path: '/photos', component: AlbumPhotosComponent },
      { path: '/photos/:id', component: PhotoDetailsComponent },
    ]
  }
];

@NgModule({
  declarations: [
    ...
  ],
  imports: [
    ...
    RouterModule.forRoot(ROUTES)
  ],
  providers: [
    ...
  ],
  bootstrap: [AppComponent]
})
export class AppModule { }
```

Above, we imported `Route` and `RouterModule` from `@angular\router`.

Next, we set a const ROUTES of type `Route[]` , an array of type `Route`

Note the setting up of `children` routes for the path `albums/:id`.

Finally, in the AppModule's metadata in `@NgModule` decorator, we specify below inside `imports` array:
```ts
RouterModule.forRoot(ROUTES)
```


