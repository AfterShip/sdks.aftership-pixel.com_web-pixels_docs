# Integration with AfterShip Personalization

## Data Reporting

Merchants using the AfterShip Personalization API for product recommendations often need data to analyze the sales strategy of the widget. AfterShip offers a simple and fast solution, allowing stores to integrate required reporting events and begin receiving data in just one hour. The following key metrics are included in the reports:

Users are primarily identified by `customer_id`. If the user lacks a `customer_id`, a random string generated and stored in the LocalStorage by AfterShip Pixel will serve as the session ID.

- **Unique Visitors**: Number of unique visitors who viewed the widget.
- **Click Rate**: The percentage of unique visitors who clicked on the widget. Multiple clicks by the same user count as a single click.
  - **Formula**: `Click rate = unique clicks / unique visitors`
  
- **Conversion Rate**: The percentage of visitors who purchased a product featured in the widget.
  - **Formula**: `Conversion rate = converted visitors / unique visitors`
  
- **Revenue**: The total revenue generated from the widget's product recommendations.
  - **Definition**: Revenue is attributed if a user interacts with a product in the recommendation widget and makes a purchase of that product within 24 hours.

## Requirements

For accurate revenue reporting, AfterShip links the Order ID from the `$purchase_completed` event to the final prices of the items. Depending on your setup, the requirements may differ:

- **For Shopify Headless Stores**: Simply install the AfterShip Personalization app.
- **For Commence API Users**: Ensure that order data synced through the Commence API includes clear line item pricing.

## Key Events for Reporting

To capture the necessary data, you need to report at least three events on your website: `$promotion_viewed`, `$promotion_engaged`, and `$purchase_completed`. These events follow a user’s journey through the store.

<img src="https://assets.am-static.com/api_docs_center/web_pixel/bf21b07bf0554736f7a6990113cf7f6f">

### 1. Upsell Offer View Event

Triggered when an upsell offer is displayed.

**Event Name**: `$promotion_viewed`

**Parameters**:

- **app_name**: Specifies the source application generating the event, which, in this case, is AfterShip Personalization. It helps differentiate events originating from various applications or modules within the AfterShip ecosystem.

- **promotion_scene_name**: Identifies the specific business context or page type on an eCommerce platform where the promotion is shown. Common examples include HomePage, ProductPage, CartPage, CheckoutPage, ThankYouPage, and OrderStatusPage.

- **promotion_asset_name**: Uniquely identifies the specific widget or component on a page that displays the promotion. It is especially useful when multiple recommendation modules (widgets) exist on a single page, enabling detailed performance analysis for each widget.

- **product_ids**: An array of product IDs included in the upsell offer.

**Example Payload**
```jsx
ASPixel.events.promotionViewed({
  app_name: ASPixel.Apps.AfterShipPersonalization,
  promotion_scene_name: "CartPage",
  promotion_asset_name: "Cross-Sell Widget",
  product_ids: ["7707982524535", "7807912425575"],
});
```

### 2. Click Product Event

Triggered when a user clicks on any part of a recommended product within the upsell widget (e.g., product image, title, variant, or the "Add to Cart" button).

**Event Name**: `$promotion_engaged`

**Parameter Details**:

- **app_name**: Specifies the source application that triggered the event, in this case, AfterShip Personalization. This helps differentiate events originating from various applications or modules within the AfterShip ecosystem.

- **promotion_scene_name**: Identifies the specific business context or page type where the promotion is displayed on an eCommerce platform. Common examples include: HomePage, ProductPage, CartPage, CheckoutPage, ThankYouPage, and OrderStatusPage.

- **promotion_asset_name**: Uniquely identifies the specific widget or component displaying the promotion. This is especially useful when multiple recommendation modules (widgets) are present on a single page, allowing for detailed performance analysis of each widget.

- **items**: An array of objects containing details about each product in the order (e.g., item ID, product ID, price, etc.).
  - **product_id**: The SPU (Standard Product Unit) ID of the item.
  - **product_name**: The SPU title or name of the item.

**Example Payload**

```jsx
ASPixel.events.promotionEngaged({
  app_name: ASPixel.Apps.AfterShipPersonalization,
  promotion_scene_name: "CartPage"
  promotion_asset_name: "Cross-Sell Widget",
  items: [
    {
      "product_id": "7707982524535",
      "product_name": "Shirt",
    }
  ]
});
```

### 3. Purchase Event

Triggered after a user completes a purchase. It can be sent from either your website's frontend or backend, depending on the capabilities of your eCommerce platform.

**Event Name**: `$purchase_completed`

**Parameter Details**:

- **order_id**: A unique identifier for the order.

- **currency**: The currency used for the order payment.

- **value**: The total payment amount for the order.

- **items**: An array of objects containing details about each product in the order (e.g., item ID, product ID, price, etc.).
  - **product_id**: The SPU (Standard Product Unit) ID of the item.
  - **variant_id**: The SKU ID of the item.
  - **unit_price**: The unit price of the item, in the specified currency. If a discount applies to an item, set the price to the discounted amount and specify the discount in the `discount` parameter.
  - **quantity**: The quantity of the item. If not provided, the default is set to 1.

**Example Payload**

```jsx
ASPixel.events.purchaseCompleted({
  order_id: "a83bb006-88d2-40e7-a00c-70b577435a1", 
  currency: "USD",
  value: 49.99,
  items: [
    {      
      "product_id": "7707982524535",
      "variant_id": "4402182524212",
      "unit_price": {
        "currency": "USA",
        "amount": "20.11"
      },
      "quantity": 3
    },
    {      
      "product_id": "7807912425575",
      "item_id": "5216582523310",
      "unit_price": {
        "currency": "USA",
        "amount": "20.11"
      },
      "quantity": 3
    }  
  ], 
});
```
