#CSRF 
CSRF = Cross-site Request Forgery


A hacker site sends requests to your server posing itself as a valid authenticated user from another tab in the same browser session where user is logged in.

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

