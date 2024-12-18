## track(eventName: string, eventParameters: object)

For the custom reporting method, provide the event name and custom params.

### Interface

| Field | Type | Required? | Description |  |
| --- | --- | --- | --- | --- |
| eventName | String | ✔ | The name of the reported event. |  |
| eventParameters | object |  | Auxiliary information for the reported event. |  |

```jsx
ASPixel.track('eventName', {
  ...eventParameters
})
```