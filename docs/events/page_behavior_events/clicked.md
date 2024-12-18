### Clicked Event

To report an event when a visitor clicks a link that directs them away from the current domain.

**Event Name**

`$clicked`

**Function Interface**

`events.clicked(eventParameter:ClickedEventParameter)`

**ClickedEventParameter**

| Parameter   | Type   | Required | Description                                              |
|-------------|--------|----------|----------------------------------------------------------|
| link_url    | string | ✔        | The full URL for an outbound link or file download.      |
| label       | string | ✔        | The label of the button.                                 |
| customer_id | string |          | The ID of the customer in your system who is associated with the event. |

**Example**
```javascript
ASPixel.events.clicked({
  link_url: '<https://www.aftership.com>',
  label: 'official website',
  customer_id: 'dcf4b98f250242ffad7822fa44835b38'
});
```

