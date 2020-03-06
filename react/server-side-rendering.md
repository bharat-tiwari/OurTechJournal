# Server-side Rendering

= ability of a Javascript app on the server side as well

## Why Server-side Rendering is needed

- for search engines to index / find your web pages 

- for faster first page load-time 

- to allow people to share a page of your site via email or on social platforms

With no Server-side rendering, Server would just send the initial HTML along with the bundled script to the browser and then browser would have to compile\(interpret\) the whole script \(including the framework logic\) to render the page, this may take long initial rendering time

\(SSR for a very large, resource-intensive application on a heavily-loaded server may again slow down the initial rendering \)

You can set up SSR using node tools like express 

After Setting up Express app to render your react app's `index.html`

in you React app app, replace the ReactDOM.render\(\) with ReactDOM.hydrate\(\)

```text
ReactDOM.render(<App />, document.getElementById('root'))
```

to

```text
ReactDOM.hydrate(<App />, document.getElementById('root'))
```

and then there is some more setup involved

check this out [https://flaviocopes.com/react-server-side-rendering/](https://flaviocopes.com/react-server-side-rendering/)

