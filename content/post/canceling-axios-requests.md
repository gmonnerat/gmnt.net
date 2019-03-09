+++
categories = ["javascript"]
date = "2019-03-08T23:06:37+02:00"
description = "You can cancel requests on axios easily"
keywords = ["blog"]
title = "Canceling axios requests"

+++

In [axios](https://github.com/axios/axios) you can cancel requests using `cancelToken`
and this can be useful when you have a lot of interactions and can't control them.

For example,

```
select.addEventListener("change", updateTotalPrice)
```

If every change on select, you make a request and you change this field several times,
you just need the response of the last request.

So, to cancel the current request to make a new, you can do:

```
var cancel,
  cancelToken = axios.cancelToken;

function updateTotalPrice(evt){
  // ... 
  if (cancel) {
    cancel();
  }
  axios.get("/api/get_product_price", {
    cancelToken: new cancelToken(function executor(c) {
      cancel = c;
    }),
    params: {
      id: evt.target.value,
    }
  }).then(function (response) {
    // handle success
    console.log(response);
  })
```

So, if a global `cancel`, every new request to `updateTotalPrice` will cancel the previous one, if exists.
