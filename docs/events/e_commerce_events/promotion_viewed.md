### **2.6 Promotion Viewed Event**

To report an event when the customer view the promotion.

**Event Name**

`$promotion_viewed`

**Function Interface**

`events.promotionViewed(eventParameter:PromotionViewedEventParameter)`

**PromotionViewedEventParameter**

| Parameter | Type | Required | Description |
| --- | --- | --- | --- |
| promotion_asset_name | string | ✔ | The name of the asset used by the promotion. |
| promotion_id | string | ✔ | The ID of the promotion associated with the event. |
| promotion_name | number | ✔ | The name of the promotion associated with the event. |
| customer_id | string |  | The ID of your customer in your system who associated to the event. |
| app_name | string |  | The key of the Aftership’s application which helps in distinguishing events originating from different applications or modules within the AfterShip ecosystem. |

**Example**

```tsx
ASPixel.events.promotionViewed({
  promotion_asset_name: 'xxxx',
  promotion_id: '12314',
  promotion_name: 'xxxx'
});
```