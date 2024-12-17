### **Purchase Completed Event**

To report an event when the customer completes a purchase.

**Event Name**

`$purchase_completed`

**Function Interface**

`events.purchaseCompleted(eventParameter:PurchaseCompletedEventParameter)`

**PurchaseCompletedEventParameter**

| Parameter | Type | Required | Description |
| --- | --- | --- | --- |
| currency | string | ✔ | Store currency following ISO 4217 standard. |
| total_amount | string | ✔ | The total value of the viewed products |
| items | Item[] | ✔ | The items in the cart. Refer to the Item resource page for the detailed specification. |
| order_id | string | ✔ | The unique identifier of the order. |
| customer_id | string |  | The ID of your customer in your system who associated to the event. |

**Example**

```tsx
ASPixel.events.purchase_completed({
  items: [{...}],
  currency: 'USD',
  total_amount: '500.00',
  order_id: 'ORD12345'
});
```