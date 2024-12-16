### **1.4 Submitted Event**

To report an event when a visitor submit a form.

**Event Name**

`$submitted`

**Function Interface**

`events.submitted(eventParameter:SubmittedEventParameter)`

**SubmittedEventParameter**

| Parameter | Type | Required | Description |
| --- | --- | --- | --- |
| form_id | string | ✔ | The unique identifier of the form. |
| form_name | string | ✔ | The name of the form. |
| succeed | boolean | ✔ | Indicates whether the form submission was successful. |
| customer_id | string |  | The ID of your customer in your system who associated to the event. |

**Example**

```tsx
ASPixel.events.submitted({
	form_id: '1234',
	form_name: 'suggestions',
	succeed: true,
	customer_id: 'dcf4b98f250242ffad7822fa44835b38'
});
```