#Angular vs React

= buying a branded computer like Dell Computer vs building your own computer from Raspberry Pie.

Which one is good? Depends on your requirements, project timelines, priorities, experience or level of comfort with the two.

With Angular, you get full **framework** to get start with building a Single Page App. AngularJS is based on MVC or rather MV*(Model-View-Whatever) pattern and Angular 2/4 is Component-based. Both AngularJS and Angular 2/4 provide all the standards needed to build SPA -  Templating, Change detection, Dependency Injection, Services, inbuilt modules for Routing and easy Ajax using http/httpClient, observables, Pipes, HTTP interceptors.

With React, you get simple, light-weight library that's easy to learn and get started with. It uses virtual-DOM for change-detection and updating the view. Its component-based. Whenever a change in the component's state is detected, a new virtual DOM is created and compared with previous one; and only the affected component is updated in the browser.  
With react, you have to use and configure external modules for setting up your own project standards , its like setting up your own framework using libraries like React-DOM-Router and usually a Flux-based architecture like Redux is used to setup your Service/Model layer.
For Dependency injection, you use ES6 compilers like Babel or Typescript in React to inject/import external modules in your components. 

📌With ngRx, you can implement Redux in Angular
📌With MobX, you can implement Observables pattern in React

    

