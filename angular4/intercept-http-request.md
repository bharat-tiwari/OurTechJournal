#Intercept HTTP Requests

The new HTTP client introduced in Angular 4.3.1 introduces `HTTP_INTERCEPTORS` module that helps us to easily intercept outgoing HTTP requests sent from our application or incoming responses to our application.

To implement an HTTP Interceptor for our Angular App, we simply create a service that implements `HttpInterceptor` interface

```ts
import { Injectable } from '@angular/core';
import { HttpRequest, HttpResponse, HttpInterceptor, HttpEvent,
   HttpHandler, HttpErrorResponse } from '@angular/common/http';

import { Observable } from 'rxjs/Observable';
import 'rxjs/add/operator/do';
import 'rxjs/add/operator/catch';
import 'rxjs/add/observable/throw';

@Injectable()
export class AppHttpInterceptor implements HttpInterceptor {
  intercept(request: HttpRequest<any>, next: HttpHandler): Observable<HttpEvent<any>> {
    
    const appRequestHeaders = new HttpHeaders({
      'Content-Type': 'application/json',
      'x-api-key': AppSettings.API_KEY
    });
    
    //we have to clone the original HttpRequest object as its immutable

    const httpRequest = request.clone({ headers: appRequestHeaders });

    return next
      .handle(httpRequest)
      .do((ev: HttpEvent<any>) => {
        if (ev instanceof HttpResponse) {
          console.log('processing response', ev);
        }
      })
      .catch(response => {
        if (response instanceof HttpErrorResponse) {
          console.log('Processing http error', response);
        }

        return Observable.throw(response);
      });
  }
}
```