#What is Single Page Application SPA

SPA = a web application that, instead of having multiple HTML pages for its various parts or functionalities,  has only single HTML page where it can render the contents of its various parts in response to navigation actions, without having to make a request to the server to fetch another HTML page.


SPAs can be implemented in two ways :
### 1. Tracking application state using the URL

In this approach, the application uses some sort of path identifier (`pathname`) in the URL (`window.location`) to identify what content is to be rendered on the  screen.
Application Entry URL->  myapp.com/
User Profile -> myapp.com**/user**
shopping Cart -> myapp.com**/cart**


Most of the SPA development frameworks use this approach because with this approach the application can start from a state based on the URL and thus, to share some particular content of the website, the URL can be used.


    
### **2. Tracking application state internally**
In this approach, The URL remains same for all the parts or sections of the application. The application uses some internal state to track what content is to be rendered. 

Application Entry URL->  myapp.com**/**
User Profile -> myapp.com**/**
shopping Cart -> myapp.com**/**

This not used much by the frameworks. With this approach, the application always starts from a root state that acts as an entry point to the application and thus to share some particular content that website displays at some later state, you would have to also explain the steps to go to that state from the root state of the website. 


## `window.location`

SPA's use the various properties provided by `window.location` in javascript to figure out what content is to be rendered on the screen.

![](/assets/1.png)


## Routers

SPA frameworks provide some sort of routing feature to allow you to map the contents to be rendered to `pathname` of the current URL 







    
    
    
