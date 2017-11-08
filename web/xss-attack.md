#XSS Attack

XSS Attack = Cross-site scripting attack

A user enters some malicious scripting code like below in one of the input fields on your website form.

```html
<script>
 $http.post("\transferMoney", {amount: 1000000, toAccount: "111AttackersAccount"});
</script>
```

To avoid such XSS attacks, all MVC Controller's actions **by default** don't process the request and send back error if any HTML code is sent in the request.

In case you want some Controller action to allow HTML in the requests, use the decorator `ValidateInput(false)` on the action method:


```cs
    class MoneyTransactionController: Controller 
    {
        [ValidateInput(false)]
        public ActionResult Transfer()
        {
            //business logic to handle money transfer
            return View();
        }
    
    }
```


And in case you want to allow HTML for some specific field in a form instead of the whole Controller Action, use `AllowHTML` at the property level in the Model of the data.


```cs
namespace MyMVCApplication.Models 
{
    public class CodeSample
    {
        public string SubmittedBy { get; set; }
        
        [AllowHTML]
        public string Code { get; set; }
    
    }

}
```
