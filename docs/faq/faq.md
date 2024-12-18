# FAQ
## 1. Will installing the AfterShip Pixel affect my website's performance?

No, the AfterShip Pixel is designed to have minimal impact on your website's performance. The primary tracking code loads only after essential resources have been downloaded. Additionally, we use a local caching mechanism to optimize performance. If the user has already downloaded the data within the cache’s validity period, the cached version will be used instead of downloading it again.

## 2. What if my website is using Content Security Policy (CSP)

If your website uses a Content Security Policy (CSP), you'll need to update it to allow AfterShip Pixel’s domains.

| Domain | CSP |
| --- | --- |
| *.aftership-pixel.com | **`script-src` `connect-src`**  |

## 3. Why did my events fail to report to AfterShip?

1. **Initialization issue:** Verify that the initialization and `events.*` methods are correctly triggered. The `events.*` method reports events only after the `init()` method is called. For more information, refer to the **Reporting the First Event** section.

2. **Debug mode:** Open the DevTools console and check if Debug mode is enabled. If you see prompts after refreshing the webhook, this means the debug mode is active and the events will not be sent to AfterShip. To disable it, refer to the **Disabling Debug Mode** section.


3. **CSP configuration:** Ensure that your **Content Security Policy (CSP)** settings are properly configured to allow necessary operations. For more details, refer to the **CSP Explanation** section.



## 4. Does the Pixel SDK collect any other data?

No, the SDK does not automatically collect data. Data is reported only when the `ASPixel.events.*` function is called.

When `ASPixel.events.*` is invoked, the following data points are appended to each event:

- Page Parameters
    - **URL**: The current page's URL
    - **Referrer**: The URL of the referring page
    - **Page Title**: The title of the current page
- Browser Parameters
    - **pseudoId**: A random string stored in the browser's LocalStorage
    - **sessionId**: ****A random string stored in the browser's SessionStorage
    - **am_id**: A string stored in the browser's SessionStorage, similar to UTM parameters

## 5. How does the Pixel SDK comply with privacy regulations?

The SDK triggers a request after the `ASPixel.events.*` method is called. Before invoking this API, please ensure your website complies with relevant privacy regulations, such as GDPR, CCPA, etc.

