#Angular Reactive Forms
Two options to build forms in Angular:
- Template Driven Form
- Reactive Form

## Template Driven Form
- Its the default option to build forms in Angular
- It uses Angular provided form template directives to build forms

## Reactive Form
 - We create the model objects of the Form elements in the component code, thus these are also known as model-driven forms. There is very minimal form template in the HTML
 
 - advantages:
  - js object driven form fields and their validations
  - dynamically validate and generate the custom validation messages for the form fields
  
  On Template Side:
  1. Set up a `form` element with a binding named `[formGroup]`:
  
  ```
  <form [formGroup]="userDetailsForm" (ngSubmit)="submitUserDetails(userDetailsForm)" >
     ...
     ...
   </form>
   ```
   
 
 

