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
    {id: 3, name: "Almonds"}
   ];
   
   constructor(private router: Router){
   }
   
   gotoProdDetails(product){
      router.naviagte(['/ProductDetails', product.id]);
      // 👆 is based on  the assumption that '/ProductDetails' route is configured as below:
      // { path: '/ProductDetails/:id', component: 'ProductDetailsComponent' }
   }
} 
```


## Reading Route param value in the component using `ActivatedRoute`
Above, we passed `product.id` as route param with the `/ProductDetails` route.
This will take the form `/ProductDetails/1` in the URL for the product 'Milk'.

In the destination component for this route i.e. 'ProductDetailsComponent', the passed route param can be read using `ActivatedRoute` object that angular's router module sets for us as below:

```js
...
import { ActivatedRoute } from '@angular/router'; // 👈
...

@Component({
   selector: 'Product-Details',
   template: `<div *ngIf="selectedProd">
    <h3>{{selectedProd.id}} -- {{selectedProd.name}}</h3>
    <div> {{selectedProd.details}} </div>
   </div>`
})
export class ProductDetailsComponent implements OnInit {
   selectedProd = {};
   ProductsWithDetails = [
      {id: 1, name: "Milk", details: "Milk is rich with Calcium"},
      {id: 2, name: "Bananas", details: "Banana is loaded with fiber and has high content of potassium "},
      {id: 3, name: "Almonds", details: "Almonds is rich with protein and Vitamin E"}
   ]
   constructor(private activatedRoute: ActivatedRoute){}
   
   ngOnInit(){
      let prodId = this.activatedRoute.snapshot.params['id']; // 👈 note how to read route parameters using ActivatedRoute.snapshot.params

      
      [ product ] = this.ProductsWithDetails.filter((prod) => prod.id === prodId); 
      if (product) {
         this.selectedProd = product;
      }
   }
   
}
```





