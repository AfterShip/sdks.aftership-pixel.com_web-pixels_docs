### **Item Viewed Event**

To report an event when the customer viewed the product.

**Event Name**

`$item_viewed`

**Function Interface**

`events.itemViewed(eventParameter:ItemViewedEventParameter)`

**ItemViewedEventParameter**

| Parameter | Type | Required | Description |
| --- | --- | --- | --- |
| currency | string | ✔ | Store currency following ISO 4217 standard. |
| total_amount | string | ✔ | The total value of the viewed products |
| items | Item[] | ✔ | The items being viewed. Refer to the Item resource page for the detailed specification. |
| customer_id | string |  | The ID of your customer in your system who associated to the event. |

**Example**

```tsx
ASPixel.events.itemViewed({
  currency: 'USD',
  items: [{...}],
  total_amount: "500.00"
});
```