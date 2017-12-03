# XHR

```js
var xhr = new XMLHttpRequest();
  xhr.onreadystatechange = () => {
    if (xhr.readyState === 4) {
      if (xhr.status === 200) {
        console.log('Success', xhr.responseText);
      } else {
        console.log('Error', xhr.responseText);
      }
    }
  };
  xhr.open('GET', '/api/stuff', true);
  xhr.send();
```
