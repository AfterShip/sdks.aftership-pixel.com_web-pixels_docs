### **2.10 Checkout Started Event**

To report an event the checkout process begins.

**Event Name**

`$checkout_started`

**Function Interface**

`events.checkoutStarted(checkoutStarted:CheckoutStartedEventParameter)`

**RefundCompletedEventParameter**

| Parameter | Type | Required | Description |
| --- | --- | --- | --- |
| currency | string | ✔ | Store currency following ISO 4217 standard. |
| total_amount | string | ✔ | The total value of the viewed products |
| items | Item[] | ✔ | The items involved during the checkout. Refer to the Item resource page for the detailed specification. |
| customer_id | string |  | The ID of your customer in your system who associated to the event. |

**Example**

```tsx
ASPixel.events.checkout_started({
  items: [{...}],
  currency: 'USD',
  total_amount: '500.00'
});
```