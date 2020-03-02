# localStorage and SessionStorage

When it comes to store or persist data on the client side, the only option available before HTML5 was cookies.

While cookie is a good option to store data on the client side, it has a limited capacity of only 4kb. Also, issue with cookies is they get sent to server with every request thus adding extra load to each request. Since anyone can add a cookie to the browser, its not very secured, a cookie added manually or by some ill-intended automation code may actually appear to be to be coming from a valid user session to the server.

With HtML5, there are two new options to store data on the client side - `localStorage` and `sessionStorage`

| StorageType | Size Limit | Expiration Period | Readable on |
| :--- | :---: | ---: | ---: |
| **Cookies** | 4KB | set by the code when creating the cookie | any window |
| **LocalStorage** | 10MB | Never \(until user clears out\) | any window |
| **SessionStorage** | 5MB | On Tab close | only the tab where its ceated |

