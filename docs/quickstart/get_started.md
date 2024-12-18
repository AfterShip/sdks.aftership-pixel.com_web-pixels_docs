# AfterShip Pixel

AfterShip Pixel is a powerful tool for optimizing marketing campaigns and conducting analytics, built with a strong focus on data science. The AfterShip Pixel Web SDK and API make integration easy.

## Quick Start

### Get Started

Follow these steps to begin using AfterShip Pixel APIs:

1. Log in to your AfterShip account.
2. Obtain your API credentials.
3. Start integrating the APIs into your system.

#### 1. Obtaining an AfterShip Pixel ID

The AfterShip Pixel ID is a unique 32-character string that represents your store. Currently, the AfterShip Pixel API is available by invitation only. Please contact us for more details and to obtain your Pixel ID.

#### 2. Installation

AfterShip offers two commonly used integration methods for web development. Depending on how your store is set up, you can choose either method to quickly integrate AfterShip Pixel into your store.

**Method 1: Using npm or yarn (Recommended)**

We recommend using [npm](https://www.npmjs.com/) or [yarn](https://yarnpkg.com/) for installation. These tools make development easier and allow you to take advantage of the rich ecosystem of JavaScript packages and tooling.

```shell
# npm install
$ npm install @aftership/web-pixels --save

# or yarn install
$ yarn add @aftership/web-pixels
```

Call `ASPixel.init` to complete the SDK initialization, allowing AfterShip Pixel to know the source of incoming events.

```jsx
import ASPixel from '@aftership/web-pixels/web';

await ASPixel.init({
  pixel_id: '<AfterShipPixelId>'
})
```

**Method 2: Adding the AfterShip Pixel Code Snippet**

Alternatively, you can add the following snippet to your website's main template. This ensures it will be automatically included on every page of your website.

```html
<!-- Replace "<AfterShipPixelId>" with your real Pixel id. -->
<script>
var e=document.createElement("script");e.src="https://sdks.automizely-analytics.io/web-pixels/v1/web.js",e.async=!0,e.onload=()=>{var e=window.methodQueue;window.methodQueue=[];for(var i=0;i<e.length;i++)e[i].prop&&window.ASPixel[e[i].prop].apply(window.ASPixel,e[i].args||[])},document.head.appendChild(e),window.methodQueue=window.methodQueue||[],window.ASPixel=window.ASPixel||new Proxy({},{get(e,i){return()=>{methodQueue.push({prop:i,args:arguments})}}}),window.ASPixel.init({pixel_id:"<AfterShipPixelId>"});
</script>
```

💡We recommend adding the AfterShip Pixel code towards the bottom of your site's template. If you're using Google Analytics or other third-party services, you can place the AfterShip Pixel code either directly above or below those.

#### 3. Reporting the First Event
The `ASPixel.events.*` function allows you to record any events and actions on your website. This method accepts a string for the event name and an optional dictionary of properties associated with the event.
💡The SDK sends the request upon calling `ASPixel.events.*()`. Before invoking this API function, ensure that your website complies with all relevant data privacy regulations (e.g., GDPR, CCPA, etc.).

**Sample Usage**
```javascript
// Tracking a click action
ASPixel.events.clicked({
  link: 'www.aftership.com',
  label: 'aftership'
});

// Tracking a page view action
ASPixel.events.pageViewed();

```

#### 4. Identifying Users
After sending the first event, you can include the `customer_id` parameter when calling `ASPixel.events.*` to identify individual users.

**Sample Usage**
```javascript
// Tracking a search action with a customer ID
ASPixel.events.searchSubmitted({
  search_term: 'laptop',
  customer_id: "e4b0f8a6c9d64a2b8e2f0c67a8d4f9e2"
});

// Tracking a page view action with a customer ID
ASPixel.events.pageViewed({
  customer_id: 'e4b0f8a6c9d64a2b8e2f0c67a8d4f9e2'
});
```

#### 5. Debugging the Events
The SDK offers an option to enable debug mode. When the debug mode is enabled, the SDK will not report events, and the related logs will be output to the browser's debug console.

<img src="https://assets.am-static.com/api_docs_center/web_pixel/64ee4681306442caf7d838211ddf16a5">

##### Enabling Debug Mode

**Method 1:**

Visit the web page with `?aftership_pixel_debug=1` appended to the URL.

**Method 2:**

Call `window.ASPixel.debug(true)` in the browser's debug console.

##### Disabling Debug Mode

**Method 1:**

Visit the web page with `?aftership_pixel_debug=0` appended to the URL.

**Method 2:**

(Excluding Checkout/Thank you pages): Call `window.ASPixel.debug(false)` in the browser's debug console.
