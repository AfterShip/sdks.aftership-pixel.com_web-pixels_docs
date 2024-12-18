## init(sdkConfig: SdkConfig)

To initialize the SDK, you need to provide a `pixel_id` to identify the store. This process is asynchronous, so be sure to handle it accordingly.

### Interface

| Field | Type | Required? | Description |
| --- | --- | --- | --- |
| sdkConfig | SdkConfig | ✔ | Constructor |

### Sdk Config

| Field | Type | Required? | Description |
| --- | --- | --- | --- |
| pixel_id | string | ✔ | AfterShip Pixel ID is an 32-character string represent your store. Currently AfterShip Pixel API is available by invitation only. Please contact us for more information and to obtain your pixel ID. |

### Sample Usage

```jsx
await ASPixel.init({
	pixel_id: '<input your AfterShip PixelId>'
});
```