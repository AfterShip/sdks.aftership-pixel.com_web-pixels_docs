### **1.3 Modal Viewed Event**

To report an event when a visitor view a modal prompt.

**Event Name**

`$modal_viewed`

**Function Interface**

`events.modalViewed(eventParameter:ModalViewedEventParameter)`

**ModalViewedEventParameter**

| Parameter | Type | Required | Description |
| --- | --- | --- | --- |
| modal_name | string | ✔ | The name or identifier of the modal being viewed. |
| customer_id | string |  | The ID of your customer in your system who associated to the event. |

**Example**

```tsx
ASPixel.events.modalViewed({
  modal_name: 'welcome modal',
  customer_id: 'dcf4b98f250242ffad7822fa44835b38'
});
```