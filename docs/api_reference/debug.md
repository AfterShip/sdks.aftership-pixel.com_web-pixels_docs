## debug(isDebug: boolean)

To debug data reporting, you can call `window.ASPixel.debug()` in the browser’s console to enable debug mode. Once enabled, events will not be sent to AfterShip; instead, the event data will be output to the console.

### Interface

| Field | Type | Required? | Description |
| --- | --- | --- | --- |
| isDebug | Boolean | ✔ | `true` to enable debug mode.
`false` to disable debug mode. |

```jsx
// To enable the debug mode.
ASPixel.debug(true);

// To disable the debug mode.
ASPixel.debug(false);
```