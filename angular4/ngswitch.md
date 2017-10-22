# *ngSwitch

```html
<div [ngSwitch]="paymentOptionSelected">
  <div *ngSwitchCase="'creditCard'">
      <CreditCardDetailsForm />
  </div>
  <div *ngSwitchCase="'check'">
      <BankAccountDetailsForm />
  </div>
  <div *ngSwitchCase="'paypal'">
      <PayPalAuth />
  </div>
  <div *ngSwitchDefault>
      <span> Please select one of the supported payment options </span>  
  </div>
</div>
```
