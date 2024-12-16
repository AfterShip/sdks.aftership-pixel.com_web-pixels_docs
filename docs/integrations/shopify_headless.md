# Integration with Shopify headless store 
## Special Reporting Scenarios：
Some events, such as `checkout started`, need to be reported from within Shopify itself, not just the frontend. Event listeners must be added to Shopify to capture these events.

**How to add listeners in Shopify:**
1. Go to the custom event menu and select Add Custom Pixel.

<img src="https://assets.am-static.com/api_docs_center/web_pixel/a82d67977f844146f5a2670e183ce61b">

2. Initialize the JavaScript Pixel SDK (ensure HTML is excluded from the setup).
```html
<script>
  var scriptElement = document.createElement('script');
  scriptEleent.src = 'https://sdks.automizely-analytics.io/web-pixels/v1/web.js';
  scriptElement.async = true;
  scriptElement.onload = () => {
    var cache = window.methodQueue;
    window.methodQueue = [];
    for (var i = 0; i < cache.length; i++) {
      if (cache[i].prop) {
        window.ASPixel[cache[i].prop].apply(window.ASPixel, cache[i].args || []);
      }
    }
  }
  document.head.appendChild(scriptElement);
  window.methodQueue = window.methodQueue || [];
  window.ASPixel = window.ASPixel || new Proxy({}, {
    get(target, prop) {
        return function () {
            methodQueue.push({ prop, args: arguments });
        };
    },
  })
  
  // Replace AfterShipPixelId
  window.ASPixel.init({
    pixel_id: "<AfterShipPixelId>",
  });
</script>
```

3. Subscribe to customer events with analytics.subscribe() and add event tracking:
```tsx
analytics.subscribe("checkout_started", event => {
    window.ASPixel.events.checkoutStarted({
      items: event?.data?.checkout?.lineItems?.map?.(item => ({
        item_id: item.id,
        item_name: item.title,
        product_id: item.variant.product.id,
        price: item.finalLinePrice.amount,
        quantity: item.quantity
      })),
      currency: event?.data?.checkout?.subtotalPrice.currencyCode,
      total_amount: event?.data?.checkout?.subtotalPrice?.amount,
    })
});

analytics.subscribe("checkout_completed", event => {
    window.ASPixel.events.purchaseCompleted({
      items: event?.data?.checkout?.lineItems?.map?.(item => ({
        item_id: item.id,
        item_name: item.title,
        product_id: item.variant.product.id,
        price: item.finalLinePrice.amount,
        quantity: item.quantity
      })),
      currency: event?.data?.checkout?.subtotalPrice.currencyCode,
      total_amount: event?.data?.checkout?.subtotalPrice.amount,
      order_id: event?.data?.checkout?.order?.id
    })
})

analytics.subscribe("all_standard_events", event => {
   console.log(event)
   ...custom logic...
})
```


