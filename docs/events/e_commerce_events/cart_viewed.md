### **Cart Viewed Event**

To report an event when the customer view the shopping cart.

**Event Name**

`$cart_viewed`

**Function Interface**

`events.cartViewed(eventParameter:CartViewedEventParameter)`

**CartViewedEventParameter**

| Parameter | Type | Required | Description |
| --- | --- | --- | --- |
| currency | string | ✔ | Store currency following ISO 4217 standard. |
| total_amount | string | ✔ | The total value of the viewed products |
| items | Item[] | ✔ | The items in the cart. Refer to the Item resource page for the detailed specification. |
| customer_id | string |  | The ID of your customer in your system who associated to the event. |

**Example**

```tsx
ASPixel.events.cartViewed({
  items: [{...}],
  currency: "USD",
  total_amount: '500.00'
});
```