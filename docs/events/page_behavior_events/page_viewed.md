### **Page Viewed Event**

To report an event when a visitor loads the page or when the browser history state is changed by the active site.

**Event Name**

`$page_viewed`

**Function Interface**

`events.pageViewed(eventParameter?:CommonEventParameter)`

**CommonEventParameter**

| Parameter | Type | Required | Description |
| --- | --- | --- | --- |
| customer_id | string |  | The ID of your customer in your system who associated to the event. |

**Example**

```tsx
ASPixel.events.pageViewed();

ASPixel.events.pageViewed({
	customer_id: 'dcf4b98f250242ffad7822fa44835b38'
});
```