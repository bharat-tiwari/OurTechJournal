# router.navigate

Apart from using `<a routerLink="destinationComponent">`, another option to navigate among components is Angular Router's `navigate` method. This method is usually suitable when we need to pass some dynamic data/params to destination component. 

```js
...
import { Router } from '@angular/router';
...

 
@Component({
   selector: 'product-list',
   template: `<div>
      <ul>
         <li *ngFor="let prod of products" (click)="gotoProdDetails(prod)">
            <span>{{prod.id}} -- {{prod.name}}</span>
         </li>
      </ul>
   </div>`
})
export class ProductListComponent {
   products = [
    {id: 1, name: "Milk"}, 
    {id: 2, name: "Bananas"},
    {id: 2, name: "Almonds"}
   ];
   
   constructor(private router: Router){
   }
   
   gotoProdDetails(product){
      router.naviagte(['/ProductDetails', product.id]);
      // 👆, assume that '/ProductDetails' route is configured as below:
      // { path: '/ProductDetails/:id', component: 'ProductDetailsComponent' }
   }
} 
```

