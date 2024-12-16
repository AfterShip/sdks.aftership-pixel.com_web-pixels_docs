### **2.1 Search Submitted Event**

To report an event when a visitor submit a search action.

**Event Name**

`$search_submitted`

**Function Interface**

`events.searchSubmitted(eventParameter:SearchSubmittedEventParameter)`

**SearchSubmittedEventParameter**

| Parameter | Type | Required | Description |
| --- | --- | --- | --- |
| search_term | string | ✔ | The term used in the search action. |
| customer_id | string |  | The ID of your customer in your system who associated to the event. |

**Example**

```tsx
ASPixel.events.searchSubmitted({
  search_term: 'laptop',
  customer_id: 'dcf4b98f250242ffad7822fa44835b38'
});
```