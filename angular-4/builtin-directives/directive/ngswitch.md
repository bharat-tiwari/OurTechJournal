# ngSwitch

```markup
<div [ngSwitch]="paymentOptionSelected">
  <div *ngSwitchCase="'creditCard'"> <!-- 👈 Note the use of single quotes inside double quotes -->
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

