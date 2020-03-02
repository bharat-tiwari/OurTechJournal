# routerLink and routerLinkActive

```markup
<a routerLink='\userProfile' routerLinkActive='activeMenuOption'> Profile </a>

<a routerLink='\userAlbums' routerLinkActive='activeMenuOption'> Albums </a>
```

In angular app, you should use `routerLink` directive with `a` tag instead of using `href` to navigate to another view in the app. `routerLinkActive` directive allows us to specify the _css class_ that we may want to apply to the link when that link's path is activated/user navigates to that link.

