### **Item**

| Name | Type | Required | Example value | Description |
| --- | --- | --- | --- | --- |
| id | `string` | ✔ | SKU_12345 | The ID of the item. Please provide either `id` or `title` . |
| title | `string` | ✔ | Stan and Friends Tee | The name of the item.Please provide either `id` or `title` . |
| product_id | `string` | ✔ | P920582 | The product ID of this item. |
| product_title | `string` | ✔ | T-Shirt | The product name of this item. |
| coupon | `string` |  | SUMMER_FUN | The coupon name/code associated with the item. Event-level and item-level `coupon` parameters are independent. |
| discount | `string` |  | 2.22 | The unit monetary discount value associated with the item. |
| index | `number` |  | 5 | The index/position of the item in a list. |
| brand | `string` |  | Google | The brand of the item. |
| category | `string` |  | Apparel | The category of the item. If used as part of a category hierarchy or taxonomy then this will be the first category. |
| category2 | `string` |  | Adult | The second category hierarchy or additional taxonomy for the item. |
| category3 | `string` |  | Shirts | The third category hierarchy or additional taxonomy for the item. |
| category4 | `string` |  | Crew | The fourth category hierarchy or additional taxonomy for the item. |
| category5 | `string` |  | Short sleeve | The fifth category hierarchy or additional taxonomy for the item. |
| unit_price | `object` |  | 10.01 | The price of the item before discounts and taxes have been applied. |
| unit_price.currency | `string` | ✔ | USD | Currency code for the amount, adhering to the ISO 4217 standard. |
| unit_price.amount | `string` | ✔ | 10 | The price of the item before discounts and taxes have been applied. |
| quantity | `number` |  | 3 | Item quantity. Default value would be 1 if the value is not provided. |

**Example**

```tsx
{
  product_id: 'P920582',
  product_title: 'T-Shirt',
  variants_id: 'SKU_12345',
  variants_title: 'Stan and Friends Tee',
  coupon: 'SUMMER_FUN',
  discount: '2.22',
  index: 5,
  brand: 'Google',
  category: 'Apparel',
  category2: 'Adult',
  category3: 'Shirts',
  category4: 'Crew',
  category5: 'Short sleeve',
  unit_price: {
    currency: 'USD',
    amount: '10'
  },
  quantity: 3
}
```