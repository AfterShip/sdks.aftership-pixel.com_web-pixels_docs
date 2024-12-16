### **2.9 Refund Completed Event**

To report an event when an order refund is completed.

**Event Name**

`$refund_completed` 

**Function Interface**

`events.refundCompleted(eventParameter:RefundCompletedEventParameter)`

**RefundCompletedEventParameter**

| Parameter | Type | Required | Description |
| --- | --- | --- | --- |
| currency | string | ✔ | Store currency following ISO 4217 standard. |
| total_amount | string | ✔ | The total value of the viewed products. |
| items | Item[] | ✔ | The items being refuned. Refer to the Item resource page for the detailed specification. |
| order_id | string | ✔ | The unique identifier of the order. |
| customer_id | string |  | The ID of your customer in your system who associated to the event. |

**Example**

```tsx
ASPixel.events.refundCompleted({
  items: [{...}],
  currency: "USD",
  total_amount: '500.00',
  order_id: "xxxxxxx"
});
```