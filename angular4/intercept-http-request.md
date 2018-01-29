#Intercept HTTP Requests

The new HTTP client introduced in Angular 4.3.1 introduces `HTTP_INTERCEPTORS` module that helps us to easily intercept outgoing HTTP requests sent from our application or incoming responses to our application.

To implement an HTTP Interceptor for our Angular App, we simply create a service that implements `HttpInterceptor` interface

```ts
import { Injectable } from '@angular/core';
import { HttpRequest, HttpResponse, HttpInterceptor, HttpEvent,
   HttpHandler, HttpErrorResponse } from '@angular/common/http';

import { Observable } from 'rxjs/Observable';


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
      .do((evt: HttpEvent<any>) => {
        if (evt instanceof HttpResponse) {
          //handle response here
        }
      })
      .catch(response => {
        if (response instanceof HttpErrorResponse) {
          //handle response error here
        }

        return Observable.throw(response);
      });
  }
}
```