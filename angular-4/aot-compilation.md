# AOT Compilation

Angular allows you to organize your application code into various modules, components, templates, services, pipes and other various other parts which are tied together with life-cycle hooks, event-emitters and change-detection \(ngZone\) events. For the browser to be able to understand your code and render the application, these various parts, hooks and events of the Angular code must be converted to an browser executable code. This conversion of Angular framework based code to browser-executable code is done by module called Angular compiler.

With Angular, we have two options to compile our application:

* Just-in-Time \(JIT\) compilation 
* Ahead-of-Time \(AOT\) compilation

## Just-In-Time compilation\(JIT\):

With JIT, the application code is sent to the browser along with the Angular compiler module and some framework/library code. Angular compiler would then compile the application at runtime and then that compiled code would get loaded and rendered by the browser. Its obvious with this JIT approach, we are sending some extra code \(Angular compiler module\) on top of our application code. This would bloat the bundle size which impacts the performance, especially in low network latency cases like of mobile or IOT devices. Also, because the application has to be compiled on the browser side before it can be rendered, this adds to the initial page rendering time.

## Ahead-of-Time compilation\(AOT\):

With AOT, the Angular code is pre-compiled on the server side at the time of building application. Thus the code sent to the browser is a browser executable code. With AOT, we save on the network latency by not requiring to send the Angular compiler + library code along with the application code. Also because the code is pre-compiled, the application loads and renders fast.

## JIT vs AOT

[https://stackoverflow.com/a/41744331](https://stackoverflow.com/a/41744331)

| JIT | AOT |
| :--- | :--- |
| - Compile TypeScript just in time for executing it. - Compiled in the browser. - Each file compiled separately. - No need to build after changing your code and before reloading the browser page. - Suitable for local development. | - Compile TypeScript during build phase. - Compiled by the machine itself, via the command line \(Faster\). - All code compiled together, inlining HTML/CSS in the scripts. - No need to deploy the compiler \(Half of Angular size\). - More secure, original source not disclosed. - Suitable for production builds. |

## AOT Benefits

* **Smaller Application JS Bundle size** = less burden on network, application can perform good even in low network latency like for mobile or IOT devices
* **Faster rendering** : precompiled code saves browser's time on compiling the application
* **Fewer asynchronous requests**: AOT would inline the HTML templates/CSS within the application javascript bundle, this would save browser from making additional ajax requests to get those resources.
* **Template errors get detected earlier** : With AOT, any errors in the template bindings would get detected at the time of building process by the AOT compiler before user sees those.
* **More secured** : AOT compiles HTML templates and components into JavaScript files long before they are served to the client. With no templates to read and no risky client-side HTML or JavaScript evaluation, there are fewer opportunities for injection attacks.

## How to compile with AOT

[https://angular.io/guide/aot-compiler\#compile-with-aot](https://angular.io/guide/aot-compiler#compile-with-aot)

