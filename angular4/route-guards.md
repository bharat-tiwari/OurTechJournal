# Route Guards

Route Guards are essentially Angular services (@injectables) that you can define and use to control user's access to some routes i.e. to allow or deny a user from navigating to some routes. 

A Route Guard Service need to implement one of the following 4 interfaces:

| | |
|--|--|
|1. CanActivate | To control access to some route|
|2. CanActivateChild | To control access to children of a route|
| 3. CanLoad | to control loading of some lazy-loaded module|
| 4. CanDeactivate | to control if user can leave a route. This can be used to prevent user from accidentally moving to some other part of the app without saving changes in the current view/page. |

How to implement Route Guards - https://alligator.io/angular/route-guards/

