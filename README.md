# Advanced Filter Fields Comparison: Collection Manager vs Shopify FMS

This document compares the advanced filter fields available in the **Collection Manager** and **Shopify FMS** repositories.

## Overview

- **Collection Manager**: Uses a rule-based filtering system with fields defined in `instance/advanced_filter/constants.py` and supports both product and collection filtering.
- **Shopify FMS**: Uses two filtering systems:
  - **Shopify Search Filters**: Direct queries to Shopify GraphQL API
  - **Parquet Filters**: Queries against parquet files stored in S3

---

## Collection Manager - Advanced Filter Fields

### Product Filter Fields

The Collection Manager supports the following filter fields for products (as defined in `RULE_COLUMN`):

| Field Name | Display Name | Type | Notes |
|------------|--------------|------|-------|
| `buy_to_view` | Buy to view | Analytics | Conversion metric |
| `buy_to_checkout` | Buy to checkout | Analytics | Conversion metric |
| `buy_to_cart` | Buy to cart | Analytics | Conversion metric |
| `checkout_to_view` | Checkout to view | Analytics | Conversion metric |
| `checkout_to_cart` | Checkout to cart | Analytics | Conversion metric |
| `cart_to_view` | Cart to view | Analytics | Conversion metric |
| `checkouts` | Checkouts | Analytics | Google Analytics metric |
| `add_to_carts` | Add to carts | Analytics | Google Analytics metric |
| `views` | Views | Analytics | Google Analytics metric |
| `revenue` | Revenue | Analytics | Order-based metric |
| `products_sold` | Products sold | Analytics | Order-based metric |
| `created_at` | Created date | Date | Product creation date |
| `published_at` | Published date | Date | Product publication date |
| `title` | Product title | String | Product name |
| `sku` | Product sku | String | SKU identifier |
| `body_html` | Product description | String | Product description HTML |
| `type` | Product type | String | Product type |
| `vendor` | Product vendor | String | Product vendor |
| `price` | Product price | Numeric | Product price |
| `tags` | Product tag | String | Product tags |
| `compare_at_price` | Compare at price | Numeric | Compare at price |
| `variant_weight` | Weight | Numeric | Variant weight |
| `inventory` | Inventory stock | Numeric | Total inventory |
| `variant_title` | Variant title | String | Variant title |
| `variant_inventory` | Variant inventory | Numeric | Variant-level inventory |
| `discount_percent` | Discount % | Numeric | Discount percentage |
| `discount` | Discount amount | Numeric | Discount amount |
| `net_revenue` | Net revenue | Analytics | Net revenue after discounts |
| `position` | Random | Numeric | Random position |
| `new_inventory_added_date` | New inventory added date | Date | Date when inventory was added |
| `restock_date` | Restocked date | Date | Restock date |
| `updated_at` | Last updated date | Date | Last update timestamp |
| `collection` | Collection title | String | Collection name |
| `collection_handle` | Collection handle | String | Collection handle |
| `collection_id` | Collection id | Numeric | Collection ID |
| `variant_number` | Number of variants | Numeric | Total variant count |
| `variant_number_available` | Number of available variants | Numeric | Available variant count |
| `is_price_reduced` | Price reduced | Boolean | Whether price is reduced |
| `variant_stock_ratio` | Variant stock ratio | Numeric | Stock ratio metric |
| `cost` | Cost | Numeric | Product cost (premium plans only) |
| `profit` | Profit | Numeric | Profit amount (premium plans only) |
| `true_profit` | True profit | Numeric | True profit (premium plans only) |
| `margin` | Margin | Numeric | Margin percentage (premium plans only) |
| `true_margin` | True margin | Numeric | True margin (premium plans only) |
| `sell_through_rate` | Sell through rate | Numeric | Sell-through rate metric |
| `handle` | Product handle | String | Product handle |

### Supported Operators

- `is equal to` / `==`
- `is not equal to` / `!=`
- `is greater than` / `>`
- `is less than` / `<`
- `contains`
- `doesn't contain` / `not contain`
- `starts with`
- `ends with`
- `in the top`
- `in the bottom`
- `is not empty` / `is set`
- `is empty` / `is not set`
- `between`
- `is in the last` / `>`
- `is not in the last` / `<`

### Special Field Configurations

- **Collection fields**: Only support "is equal to" operator
- **Compare at price**: Supports "is not empty" and "is empty" operators
- **Variant inventory**: Supports special operators: "is tracked", "is not tracked", "continue selling", "not continue selling"
- **Tags**: Different operators for smart vs custom collections
- **Price/Weight/Inventory**: Support "in the top (%)" and "in the bottom (%)" for custom collections

---

## Shopify FMS - Advanced Filter Fields

### Shopify Search Filters (GraphQL API)

These filters query Shopify directly via GraphQL API.

#### Product Search Fields

| Field Name | Type | Description |
|------------|------|-------------|
| `barcode` | String | Product variant barcode |
| `bundles` | Boolean | Product bundle status |
| `category_id` | String | Product category ID |
| `collection_id` | Numeric | Collection ID |
| `combined_listing_role` | Select | Role in combined listing (parent/child/no_role) |
| `created_at` | DateTime | Product creation date |
| `delivery_profile_id` | Numeric | Delivery profile ID |
| `error_feedback` | String | Publishing errors |
| `gift_card` | Boolean | Is gift card |
| `handle` | String | Product handle |
| `has_only_composites` | Boolean | Has only composite variants |
| `has_only_default_variant` | Boolean | Has only default variant |
| `has_variant_with_components` | Boolean | Has variants with components |
| `id` | Numeric | Product ID |
| `inventory_total` | Numeric | Total inventory count |
| `is_price_reduced` | Boolean | Price reduced status |
| `out_of_stock_somewhere` | Boolean | Out of stock in at least one location |
| `price` | Numeric | Variant price |
| `product_configuration_owner` | String | App ID |
| `product_publication_status` | String | Publication status |
| `product_type` | String | Product type |
| `publication_ids` | String | Publication IDs (comma-separated) |
| `publishable_status` | Select | Publishable status |
| `published_at` | DateTime | Publication date |
| `published_status` | Select | Published status (unset/pending/approved/not approved) |
| `sku` | String | Variant SKU |
| `status` | Select | Product status (ACTIVE/ARCHIVED/DRAFT) |
| `tag` | String | Product tag |
| `tag_not` | String | Exclude tag |
| `title` | String | Product title |
| `updated_at` | DateTime | Last update date |
| `variant_id` | Numeric | Variant ID |
| `variant_title` | String | Variant title |
| `vendor` | String | Product vendor |

#### Collection Search Fields

| Field Name | Type | Description |
|------------|------|-------------|
| `collection_type` | Select | Collection type (custom/smart) |
| `handle` | String | Collection handle |
| `id` | Numeric | Collection ID |
| `product_id` | Numeric | Product ID in collection |
| `product_publication_status` | Select | Product publication status |
| `publishable_status` | String | Publishable status |
| `published_at` | DateTime | Publication date |
| `published_status` | Select | Published status |
| `title` | String | Collection title |
| `updated_at` | DateTime | Last update date |

#### Product Variant Search Fields

| Field Name | Type | Description |
|------------|------|-------------|
| `barcode` | String | Variant barcode |
| `delivery_profile_id` | Numeric | Delivery profile ID |
| `exclude_composite` | Boolean | Exclude composite variants |
| `requires_components` | Boolean | Requires components |
| `sku` | String | Variant SKU |
| `tag` | String | Tag |
| `tag_not` | String | Exclude tag |
| `taxable` | Boolean | Taxable status |
| `title` | String | Variant title |
| `updated_at` | Date | Update date |
| `vendor` | String | Vendor |

#### Location Search Fields

| Field Name | Type | Description |
|------------|------|-------------|
| `active` | Boolean | Active status |
| `address1` | String | Address line 1 |
| `address2` | String | Address line 2 |
| `city` | String | City |
| `country` | String | Country |
| `created_at` | Date | Creation date |
| `geolocated` | Boolean | Geolocated status |
| `id` | Numeric | Location ID |
| `latitude` | Numeric | Latitude |
| `longitude` | Numeric | Longitude |
| `name` | String | Location name |
| `phone` | String | Phone number |
| `province` | String | Province |
| `zip` | String | ZIP code |

### Parquet Search Filters (S3 Data)

These filters query parquet files stored in S3.

#### Product Parquet Fields

| Field Name | Type | Description |
|------------|------|-------------|
| `id` | String | Product ID |
| `title` | String | Product title |
| `handle` | String | Product handle |
| `product_type` | Multiselect | Product type (dynamically populated) |
| `tags` | Multiselect | Product tags (dynamically populated) |
| `status` | Select | Product status (ACTIVE/ARCHIVED/DRAFT) |
| `vendor` | String | Product vendor |
| `variant_number` | Numeric | Number of variants |
| `publications` | Multiselect | Publication IDs (dynamically populated) |
| `inventory_total` | Numeric | Total inventory count |

**Note**: Parquet product filters support joins with:
- Orders (for `products_sold`, `revenue`, `net_revenue`)
- Google Analytics (for `views`, `add_to_carts`, `checkouts`, `revenue`)
- Product Variants
- Inventory Levels
- Locations

#### Product Variant Parquet Fields

| Field Name | Type | Description |
|------------|------|-------------|
| `id` | String | Variant ID |
| `title` | String | Variant title |
| `sku` | String | Variant SKU |
| `price` | Numeric | Variant price |

**Note**: Many variant fields are commented out in the codebase (e.g., `compare_at_price`, `inventory_item_id`, `barcode`, `discount`, `profit`, `margin`, etc.)

#### Collection Parquet Fields

| Field Name | Type | Description |
|------------|------|-------------|
| `id` | String | Collection ID |
| `title` | String | Collection title |
| `handle` | String | Collection handle |
| `image` | String | Collection image URL |
| `alt_text` | String | Image alt text |
| `product_count` | Numeric | Number of products |
| `products` | Text | Product IDs (CSV) |
| `updated_at` | DateTime | Last update date |
| `sort_order` | Select | Sort order (MANUAL/BEST_SELLING/PRICE_ASC/etc.) |
| `template_suffix` | String | Template suffix |
| `type` | Select | Collection type (custom/smart) |
| `disjunctive` | Boolean | Disjunctive status |
| `rules` | String | Collection rules (disabled) |
| `publication_count` | Numeric | Number of publications |
| `publications` | Text | Publication IDs (disabled) |

#### Order Parquet Fields

| Field Name | Type | Description |
|------------|------|-------------|
| `id` | String | Order line item ID |
| `order_id` | String | Order ID |
| `order_created_at` | DateTime | Order creation date |
| `order_updated_at` | DateTime | Order update date |
| `customer_id` | String | Customer ID |
| `product_id` | String | Product ID |
| `collection_ids` | String | Collection IDs |
| `variant_id` | String | Variant ID |
| `quantity` | Numeric | Quantity ordered |
| `price` | Numeric | Item price |
| `price_discounted` | Numeric | Discounted price |
| `net_price` | Numeric | Net price after discounts |
| `products_sold` | Numeric | Products sold |
| `revenue` | Numeric | Revenue |
| `net_revenue` | Numeric | Net revenue |

#### Location Parquet Fields

| Field Name | Type | Description |
|------------|------|-------------|
| `id` | String | Location ID |
| `name` | String | Location name |
| `active` | Boolean | Active status |
| `created_at` | DateTime | Creation date |
| `updated_at` | DateTime | Update date |

#### Other Parquet Entity Fields

- **Publications**: `id`, `name`, `handle`
- **Inventory Levels**: `id`, `location_id`, `inventory_item_id`, `quantity`, `updated_at`
- **Google Analytics (GA)**: `time`, `item_id`, `item_name`, `item_viewed`, `item_added_to_cart`, `item_checked_out`, `item_revenue`, `views`, `add_to_carts`, `checkouts`, `revenue`

---

## Comparison Summary

### Fields Available in Both Repositories

| Field | Collection Manager | Shopify FMS (Search) | Shopify FMS (Parquet) |
|-------|-------------------|---------------------|----------------------|
| `title` | ✅ | ✅ | ✅ |
| `handle` | ✅ | ✅ | ✅ |
| `sku` | ✅ | ✅ | ✅ |
| `price` | ✅ | ✅ | ✅ |
| `vendor` | ✅ | ✅ | ✅ |
| `type` / `product_type` | ✅ | ✅ | ✅ |
| `tags` | ✅ | ✅ | ✅ |
| `inventory` / `inventory_total` | ✅ | ✅ | ✅ |
| `variant_title` | ✅ | ✅ | ✅ |
| `variant_inventory` | ✅ | ❌ | ❌ |
| `compare_at_price` | ✅ | ❌ | ❌ (commented) |
| `created_at` | ✅ | ✅ | ❌ (commented) |
| `published_at` | ✅ | ✅ | ❌ (commented) |
| `updated_at` | ✅ | ✅ | ✅ |
| `collection_id` | ✅ | ✅ | ❌ |
| `collection` / `collection.title` | ✅ | ❌ | ✅ |
| `collection_handle` | ✅ | ✅ | ✅ |
| `is_price_reduced` | ✅ | ✅ | ❌ |
| `status` | ❌ | ✅ | ✅ |
| `barcode` | ❌ | ✅ | ❌ (commented) |

### Fields Unique to Collection Manager

- Analytics metrics: `buy_to_view`, `buy_to_checkout`, `buy_to_cart`, `checkout_to_view`, `checkout_to_cart`, `cart_to_view`, `checkouts`, `add_to_carts`, `views`
- Revenue metrics: `revenue`, `net_revenue`, `products_sold`
- Financial metrics: `cost`, `profit`, `true_profit`, `margin`, `true_margin`, `discount`, `discount_percent`
- Inventory metrics: `variant_number`, `variant_number_available`, `variant_stock_ratio`
- Date fields: `new_inventory_added_date`, `restock_date`
- Other: `body_html`, `sell_through_rate`, `position` (random)

### Fields Unique to Shopify FMS

#### Shopify Search Only:
- `bundles`, `category_id`, `combined_listing_role`, `delivery_profile_id`, `error_feedback`, `gift_card`, `has_only_composites`, `has_only_default_variant`, `has_variant_with_components`, `product_configuration_owner`, `product_publication_status`, `publication_ids`, `publishable_status`, `published_status`, `tag_not`, `out_of_stock_somewhere`, `exclude_composite`, `requires_components`, `taxable`

#### Parquet Only:
- Collection: `image`, `alt_text`, `product_count`, `products`, `sort_order`, `template_suffix`, `disjunctive`, `rules`, `publication_count`
- Order: `order_id`, `order_created_at`, `order_updated_at`, `customer_id`, `collection_ids`, `price_discounted`, `net_price`
- Location: `name`, `active`
- GA: `time`, `item_id`, `item_name`, `item_viewed`, `item_added_to_cart`, `item_checked_out`, `item_revenue`

### Operator Support Comparison

| Operator | Collection Manager | Shopify FMS |
|---------|-------------------|-------------|
| Equals (`=`) | ✅ | ✅ |
| Not Equals (`!=`) | ✅ | ✅ |
| Greater Than (`>`) | ✅ | ✅ |
| Less Than (`<`) | ✅ | ✅ |
| Contains | ✅ | ✅ |
| Does Not Contain | ✅ | ✅ |
| Starts With | ✅ | ✅ |
| Ends With | ✅ | ✅ |
| Is Null / Is Empty | ✅ | ✅ |
| Is Not Null / Is Not Empty | ✅ | ✅ |
| Between | ✅ | ✅ |
| In | ❌ | ✅ |
| Not In | ❌ | ✅ |
| In The Top | ✅ | ❌ |
| In The Bottom | ✅ | ❌ |
| In The Top (%) | ✅ | ❌ |
| In The Bottom (%) | ✅ | ❌ |
| Is In The Last | ✅ | ❌ |
| Is Not In The Last | ✅ | ❌ |

### Special Features

#### Collection Manager
- Supports "smart" vs "custom" collection types with different available fields
- Plan-based field restrictions (premium fields: cost, profit, margin, etc.)
- Special operators for variant inventory (tracked, continue selling)
- Google Analytics integration for conversion metrics
- Support for metafields (configurable)

#### Shopify FMS
- Two query systems: Direct Shopify API and Parquet file queries
- Support for dataset joins (Orders, GA, Variants, Inventory, Locations)
- Dynamic dropdown population from actual data
- Timeseries filtering for time-based data
- Aggregation support for joined datasets
- Multiselect support for array fields

---

## Recommendations

1. **For Product Filtering**: Collection Manager offers more comprehensive analytics and financial metrics, while Shopify FMS provides better integration with Shopify's native search capabilities.

2. **For Collection Filtering**: Shopify FMS Parquet filters provide more collection-specific metadata (image, sort_order, etc.), while Collection Manager focuses on collection membership filtering.

3. **For Analytics**: Collection Manager has superior analytics integration with Google Analytics and order-based metrics.

4. **For Real-time Data**: Shopify FMS Search filters provide real-time data directly from Shopify, while Parquet filters work with cached data.

5. **For Complex Queries**: Shopify FMS supports more complex query structures with joins and aggregations, while Collection Manager focuses on rule-based filtering.

---

## Notes

- Collection Manager excludes certain fields in "smart" collection mode
- Shopify FMS has many commented-out fields in Parquet filters that may be enabled in the future
- Both systems support custom metafields, though implementation differs
- Collection Manager has plan-based restrictions for premium features
- Shopify FMS Parquet filters support dynamic value population from actual data

