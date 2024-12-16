### **2.4 Added to Cart Event**

To report an event when items are being added to the shopping cart.

**Event Name**

`$added_to_cart` 

**Function Interface**

`events.addedToCart(eventParameter:AddedToCartEventParameter)`

**AddedToCartEventParameter**

| Parameter | Type | Required | Description |
| --- | --- | --- | --- |
| currency | string | ✔ | Store currency following ISO 4217 standard. |
| total_amount | string | ✔ | The total value of the viewed products |
| items | Item[] | ✔ | The items being added to the cart. Refer to the Item resource page for the detailed specification. |
| customer_id | string |  | The ID of your customer in your system who associated to the event. |

**Example**

```tsx
ASPixel.events.addedToCart({
  items: [{...}],
  currency: "USD",
  total_amount: '500.00'
});
```