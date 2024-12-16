### **2.3 Item Clicked Event**

To report an event when the customer clicked the product.

**Event Name**

`$item_clicked`

**Function Interface**

`events.itemClicked(eventParameter:ItemClickedEventParameter)`

**ItemClickedEventParameter**

| Parameter | Type | Required | Description |
| --- | --- | --- | --- |
| currency | string | ✔ | Store currency following ISO 4217 standard. |
| total_amount | string | ✔ | The total value of the viewed products |
| items | Item[] | ✔ | The items being clicked. Refer to the Item resource page for the detailed specification. |
| customer_id | string |  | The ID of your customer in your system who associated to the event. |

**Example**

```tsx
ASPixel.events.itemClicked({
  currency: 'USD',
  items: [{...}],
  total_amount: '500.00'
});

```