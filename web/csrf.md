#CSRF 
CSRF = Cross-site Request Forgery


A hacker site sends requests to your server posing itself as a valid authenticated user from another tab in the same browser session where user is logged in.

## In ASP.Net MVC
To avoid CSRF, ASP.net MVC uses `AntiForgeryToken` that can be added to a form which user submits to send request. This would create a unique session token and passed as a hidden field's value in the form. 

```html
    ...
    <div>
        <form action="Transfer" method="post">
        Amount: <input type="text" name="Amount" value="" /><br />
        To Account: <input type="text" name="Account" value="" /><br />
    <input type="submit" value="Transfer Money" />
    @Html.AntiForgeryToken("someSecretKey1")
    </div>
    ...
```

        

The MVC controller action that processes the request can be decorated with `[ValidateAntiForgeryToken(salt="someSecretKey1")]` decorator:

```cs
    class MoneyTransactionController: Controller 
    {
        [ValidateAntiForgeryToken(
        public ActionResult Transfer()
        {
            //business logic to handle money transfer
            return View();
        }
    
    }
```

## In AngularJS
AngularJS provides a mechanism to counter XSRF. 
On any ajax($http) request, the `$http` service reads a cookie (which is named  `XSRF-TOKEN` by default) and adds it to the HTTP request headers named as `X-XSRF-TOKEN`. 
Because only the JavaScript that runs on your domain could read the cookie and set the header, the server would be sure that the request came from the valid domain. The header will not be set for cross-domain requests.
For this to work, on the server side, it should set a unique user specific session cookie token called `XSRF-TOKEN` on the first HTTP GET request. And then on the subsequent server requests, the server can verify that the cookie matches `X-XSRF-TOKEN HTTP` header. 

The name of the headers can be specified using the `xsrfHeaderName` and `xsrfCookieName` properties of either `$httpProvider.defaults` at config-time, `$http.defaults` at run-time, or the per-request config object.
