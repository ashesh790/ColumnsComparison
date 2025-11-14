# AdvancedFilter Comparison: Collection Manager vs FMS

This document provides a comprehensive comparison of columns and operators available in Collection Manager's AdvancedFilter and FMS (Filter Management System).

## Table of Contents
1. [Operators Comparison](#operators-comparison)
2. [Columns/Fields Comparison](#columnsfields-comparison)
3. [Visual Comparison Matrix](#visual-comparison-matrix)

---

## Operators Comparison

### Collection Manager AdvancedFilter Operators

| User Display | System Value | Description |
|--------------|--------------|-------------|
| is equal to | == | Equality check |
| is not equal to | != | Inequality check |
| is greater than | > | Greater than comparison |
| is less than | < | Less than comparison |
| contains | contains | String contains check |
| doesn't contain | not contain | String does not contain |
| is in the last | > | Date is in the last X days |
| is not in the last | < | Date is not in the last X days |
| starts with | starts with | String starts with |
| ends with | ends with | String ends with |
| in the top | in the top | Top N items |
| in the bottom | in the bottom | Bottom N items |
| is not empty | is set | Field is not null/empty |
| is empty | is not set | Field is null/empty |
| between | between | Range between two values |

### FMS Operators

| Operator Name | Label | Used For |
|---------------|-------|----------|
| = | equals | Equality operators, Numeric, String |
| != | not equals | Equality operators, Numeric, String |
| < | less than | Numeric, Time operators |
| <= | less than or equal to | Numeric, Time operators |
| > | greater than | Numeric, Time operators |
| >= | greater than or equal to | Numeric, Time operators |
| contains | contains | String, Multi-select operators |
| doesNotContain | does not contain | Multi-select operators |
| beginsWith | begins with | String operators |
| endsWith | ends with | String operators |
| in | is in | Multi-select operators |
| notIn | is not in | Multi-select operators |
| isNull | is null | Null operators |
| isNotNull | is not null | Null operators |
| between | between | Range, Time operators |
| notBetween | not between | Range, Time operators |

**FMS Operator Groups:**
- **EQUALITY_OPERATORS**: =, !=
- **NUMERIC_OPERATORS**: =, !=, <, <=, >, >=
- **STRING_OPERATORS**: =, !=, contains, beginsWith, endsWith
- **MULTI_SELECT_OPERATORS**: in, notIn, contains, doesNotContain
- **BOOLEAN_OPERATORS**: =
- **TIME_OPERATORS**: <, <=, >, >=, between, notBetween
- **NULL_OPERATORS**: isNull, isNotNull
- **RANGE_OPERATORS**: between, notBetween

---

## Columns/Fields Comparison

### Collection Manager AdvancedFilter Columns

#### Analytics & Performance Metrics
| User Display | System Column | Operators |
|--------------|---------------|-----------|
| Buy to view | buy_to_view | >, <, ==, !=, in the top, in the bottom |
| Buy to checkout | buy_to_checkout | >, <, ==, !=, in the top, in the bottom |
| Buy to cart | buy_to_cart | >, <, ==, !=, in the top, in the bottom |
| Checkout to view | checkout_to_view | >, <, ==, !=, in the top, in the bottom |
| Checkout to cart | checkout_to_cart | >, <, ==, !=, in the top, in the bottom |
| Cart to view | cart_to_view | >, <, ==, !=, in the top, in the bottom |
| Checkouts | checkouts | >, <, ==, !=, in the top, in the bottom |
| Add to carts | add_to_carts | >, <, ==, !=, in the top, in the bottom |
| Views | views | >, <, ==, !=, in the top, in the bottom |
| Revenue | revenue | >, <, ==, !=, in the top, in the bottom |
| Products sold | products_sold | >, <, ==, !=, in the top, in the bottom |
| Net revenue | net_revenue | >, <, ==, !=, in the top, in the bottom |

#### Product Information
| User Display | System Column | Operators |
|--------------|---------------|-----------|
| Product title | title | ==, !=, contains, not contain, starts with, ends with |
| Product sku | sku | ==, !=, contains, not contain, starts with, ends with |
| Product description | body_html | ==, !=, contains, not contain, starts with, ends with |
| Product type | type | ==, !=, contains, not contain, starts with, ends with |
| Product vendor | vendor | ==, !=, contains, not contain, starts with, ends with |
| Product tag | tags | ==, !=, contains, not contain |
| Product price | price | ==, !=, >, <, between |
| Compare at price | compare_at_price | ==, !=, >, <, between, is set, is not set |
| Product handle | handle | ==, !=, contains, not contain, starts with, ends with |

#### Variant Information
| User Display | System Column | Operators |
|--------------|---------------|-----------|
| Variant title | variant_title | ==, !=, contains, not contain, starts with, ends with |
| Variant inventory | variant_inventory | ==, !=, >, <, between |
| Weight | variant_weight | ==, !=, >, <, between |

#### Inventory & Stock
| User Display | System Column | Operators |
|--------------|---------------|-----------|
| Inventory stock | inventory | ==, !=, >, <, between |
| Number of variants | variant_number | ==, !=, >, <, between |
| Number of available variants | variant_number_available | ==, !=, >, <, between |
| Variant stock ratio | variant_stock_ratio | ==, !=, >, <, between |

#### Financial Metrics
| User Display | System Column | Operators |
|--------------|---------------|-----------|
| Discount % | discount_percent | ==, !=, >, <, between |
| Discount amount | discount | ==, !=, >, <, between |
| Cost | cost | ==, !=, >, <, between |
| Profit | profit | ==, !=, >, <, between |
| True profit | true_profit | ==, !=, >, <, between |
| Margin | margin | ==, !=, >, <, between |
| True margin | true_margin | ==, !=, >, <, between |
| Sell through rate | sell_through_rate | ==, !=, >, <, between |

#### Dates
| User Display | System Column | Operators |
|--------------|---------------|-----------|
| Created date | created_at | >, < (is in the last, is not in the last), between |
| Published date | published_at | >, < (is in the last, is not in the last), between |
| New inventory added date | new_inventory_added_date | >, < (is in the last, is not in the last), between |
| Restocked date | restock_date | >, < (is in the last, is not in the last), between |
| Last updated date | updated_at | >, < (is in the last, is not in the last), between |

#### Collection Information
| User Display | System Column | Operators |
|--------------|---------------|-----------|
| Collection title | collection | ==, !=, contains, not contain, starts with, ends with |
| Collection handle | collection_handle | ==, !=, contains, not contain, starts with, ends with |
| Collection id | collection_id | ==, != |

#### Other
| User Display | System Column | Operators |
|--------------|---------------|-----------|
| Random | position | (Special handling) |
| Price reduced | is_price_reduced | ==, != |

---

### FMS Fields

#### Parquet Product Fields (ParquetProductSearchFields)
| Field Name | Label | Operators | Input Type |
|------------|-------|-----------|------------|
| id | id | =, != | text |
| title | title | =, !=, contains, beginsWith, endsWith | text |
| handle | handle | =, !=, contains, beginsWith, endsWith | text |
| product_type | type | in, notIn, contains, doesNotContain | multiselect |
| tags | tags | in, notIn, contains, doesNotContain | multiselect |
| status | status | =, != | select |
| vendor | vendor | =, !=, contains, beginsWith, endsWith | text |
| variant_number | variant_number | =, !=, <, <=, >, >= | number |
| publications | publications | in, notIn, contains, doesNotContain | multiselect |
| inventory_total | inventory_total | =, !=, <, <=, >, >= | number |

#### Parquet Product Variant Fields (ParquetProductVariantSearchFields)
| Field Name | Label | Operators | Input Type |
|------------|-------|-----------|------------|
| id | id | =, != | text |
| title | title | =, !=, contains, beginsWith, endsWith | text |
| sku | sku | =, !=, contains, beginsWith, endsWith | text |
| price | price | =, !=, <, <=, >, >= | number |

#### Parquet Order Fields (ParquetOrderSearchFields)
| Field Name | Label | Operators | Input Type |
|------------|-------|-----------|------------|
| id | id | =, != | text |
| order_id | order_id | =, != | text |
| order_created_at | order_created_at | <, <=, >, >=, between, notBetween | datetime-local |
| order_updated_at | order_updated_at | <, <=, >, >=, between, notBetween | datetime-local |
| customer_id | customer_id | =, != | text |
| product_id | product_id | =, != | text |
| collection_ids | collection_ids | in, notIn, contains, doesNotContain | multiselect |
| variant_id | variant_id | =, != | text |
| quantity | quantity | =, !=, <, <=, >, >= | number |
| price | price | =, !=, <, <=, >, >= | number |
| price_discounted | price_discounted | =, !=, <, <=, >, >= | number |
| net_price | net_price | =, !=, <, <=, >, >= | number |
| products_sold | products_sold | =, !=, <, <=, >, >= | number |
| revenue | revenue | =, !=, <, <=, >, >= | number |
| net_revenue | net_revenue | =, !=, <, <=, >, >= | number |

#### Parquet GA (Google Analytics) Fields (ParquetGASearchFields)
| Field Name | Label | Operators | Input Type |
|------------|-------|-----------|------------|
| id | id | =, != | text |
| time | time | <, <=, >, >=, between, notBetween | datetime-local |
| item_id | item_id | =, != | text |
| item_name | item_name | =, !=, contains, beginsWith, endsWith | text |
| item_viewed | item_viewed | =, !=, <, <=, >, >= | number |
| item_added_to_cart | item_added_to_cart | =, !=, <, <=, >, >= | number |
| item_checked_out | item_checked_out | =, !=, <, <=, >, >= | number |
| item_revenue | item_revenue | =, !=, <, <=, >, >= | number |
| views | views | =, !=, <, <=, >, >= | number |
| add_to_carts | add_to_carts | =, !=, <, <=, >, >= | number |
| checkouts | checkouts | =, !=, <, <=, >, >= | number |
| revenue | revenue | =, !=, <, <=, >, >= | number |
| cart_to_view | cart_to_view | =, !=, <, <=, >, >= | number |
| checkout_to_view | checkout_to_view | =, !=, <, <=, >, >= | number |
| checkout_to_cart | checkout_to_cart | =, !=, <, <=, >, >= | number |
| buy_to_view | buy_to_view | =, !=, <, <=, >, >= | number |
| buy_to_cart | buy_to_cart | =, !=, <, <=, >, >= | number |
| buy_to_checkout | buy_to_checkout | =, !=, <, <=, >, >= | number |

#### Parquet Collection Fields (ParquetCollectionSearchFields)
| Field Name | Label | Operators | Input Type |
|------------|-------|-----------|------------|
| id | id | =, != | text |
| title | title | =, !=, contains, beginsWith, endsWith | text |
| handle | handle | =, !=, contains, beginsWith, endsWith | text |
| image | image | =, !=, contains, beginsWith, endsWith | text |
| alt_text | alt_text | =, !=, contains, beginsWith, endsWith | text |
| product_count | product_count | =, !=, <, <=, >, >= | number |
| products | products | in, notIn, contains, doesNotContain | text |
| updated_at | updated_at | <, <=, >, >=, between, notBetween | datetime-local |
| sort_order | sort_order | =, != | select |
| template_suffix | template_suffix | =, !=, contains, beginsWith, endsWith | text |
| type | type | =, != | select |
| disjunctive | disjunctive | = | select |
| rules | rules | =, !=, contains, beginsWith, endsWith | text |
| publication_count | publication_count | =, !=, <, <=, >, >= | number |
| publications | publications | in, notIn, contains, doesNotContain | multiselect |

#### Shopify Product Fields (ShopifyProductSearchFields)
| Field Name | Label | Operators | Input Type |
|------------|-------|-----------|------------|
| barcode | barcode | =, !=, contains, beginsWith, endsWith | text |
| bundles | bundles | = | select |
| category_id | category_id | =, !=, contains, beginsWith, endsWith | text |
| collection_id | collection_id | =, !=, <, <=, >, >= | number |
| combined_listing_role | combined_listing_role | = | select |
| created_at | created_at | <, <=, >, >=, between, notBetween | datetime-local |
| delivery_profile_id | delivery_profile_id | =, !=, <, <=, >, >= | number |
| error_feedback | error_feedback | =, !=, contains, beginsWith, endsWith | text |
| gift_card | gift_card | = | select |
| handle | handle | =, !=, contains, beginsWith, endsWith | text |
| has_only_composites | has_only_composites | = | select |
| has_only_default_variant | has_only_default_variant | = | select |
| has_variant_with_components | has_variant_with_components | = | select |
| id | id | =, !=, <, <=, >, >= | number |
| inventory_total | inventory_total | =, !=, <, <=, >, >= | number |
| is_price_reduced | is_price_reduced | = | select |
| out_of_stock_somewhere | out_of_stock_somewhere | = | select |
| price | price | =, !=, <, <=, >, >= | number |
| product_configuration_owner | product_configuration_owner | =, !=, contains, beginsWith, endsWith | text |
| product_publication_status | product_publication_status | =, !=, contains, beginsWith, endsWith | text |
| product_type | product_type | =, !=, contains, beginsWith, endsWith | text |
| publication_ids | publication_ids | =, !=, contains, beginsWith, endsWith | text |
| publishable_status | publishable_status | =, !=, contains, beginsWith, endsWith | select |
| published_at | published_at | <, <=, >, >=, between, notBetween | datetime-local |
| published_status | published_status | = | select |
| sku | sku | =, !=, contains, beginsWith, endsWith | text |
| status | status | =, !=, contains, beginsWith, endsWith | select |
| tag | tag | =, !=, contains, beginsWith, endsWith | text |
| tag_not | tag_not | =, !=, contains, beginsWith, endsWith | text |
| title | title | =, !=, contains, beginsWith, endsWith | text |
| updated_at | updated_at | <, <=, >, >=, between, notBetween | datetime-local |
| variant_id | variant_id | =, !=, <, <=, >, >= | number |
| variant_title | variant_title | =, !=, contains, beginsWith, endsWith | text |
| vendor | vendor | =, !=, contains, beginsWith, endsWith | text |

---

## Visual Comparison Matrix

### Field Availability Comparison

| Collection Manager Field | CM System Column | Available in FMS? | FMS Field Name | FMS Location | Operator Match? |
|--------------------------|-----------------|-------------------|----------------|--------------|-----------------|
| **Analytics & Performance** |
| Buy to view | buy_to_view | ✅ | buy_to_view | ParquetGASearchFields | ⚠️ Partial |
| Buy to checkout | buy_to_checkout | ✅ | buy_to_checkout | ParquetGASearchFields | ⚠️ Partial |
| Buy to cart | buy_to_cart | ✅ | buy_to_cart | ParquetGASearchFields | ⚠️ Partial |
| Checkout to view | checkout_to_view | ✅ | checkout_to_view | ParquetGASearchFields | ⚠️ Partial |
| Checkout to cart | checkout_to_cart | ✅ | checkout_to_cart | ParquetGASearchFields | ⚠️ Partial |
| Cart to view | cart_to_view | ✅ | cart_to_view | ParquetGASearchFields | ⚠️ Partial |
| Checkouts | checkouts | ✅ | checkouts | ParquetGASearchFields | ⚠️ Partial |
| Add to carts | add_to_carts | ✅ | add_to_carts | ParquetGASearchFields | ⚠️ Partial |
| Views | views | ✅ | views | ParquetGASearchFields | ⚠️ Partial |
| Revenue | revenue | ✅ | revenue | ParquetOrderSearchFields, ParquetGASearchFields | ⚠️ Partial |
| Products sold | products_sold | ✅ | products_sold | ParquetOrderSearchFields | ⚠️ Partial |
| Net revenue | net_revenue | ✅ | net_revenue | ParquetOrderSearchFields | ⚠️ Partial |
| **Product Information** |
| Product title | title | ✅ | title | ParquetProductSearchFields, ShopifyProductSearchFields | ✅ Full |
| Product sku | sku | ✅ | sku | ParquetProductVariantSearchFields, ShopifyProductSearchFields | ✅ Full |
| Product description | body_html | ❌ | - | - | - |
| Product type | type | ✅ | product_type | ParquetProductSearchFields, ShopifyProductSearchFields | ⚠️ Partial |
| Product vendor | vendor | ✅ | vendor | ParquetProductSearchFields, ShopifyProductSearchFields | ✅ Full |
| Product tag | tags | ✅ | tags | ParquetProductSearchFields | ⚠️ Partial |
| Product price | price | ✅ | price | ParquetProductVariantSearchFields, ShopifyProductSearchFields | ⚠️ Partial |
| Compare at price | compare_at_price | ❌ | - | - | - |
| Product handle | handle | ✅ | handle | ParquetProductSearchFields, ShopifyProductSearchFields | ✅ Full |
| **Variant Information** |
| Variant title | variant_title | ✅ | variant_title | ShopifyProductSearchFields | ✅ Full |
| Variant inventory | variant_inventory | ❌ | - | - | - |
| Weight | variant_weight | ❌ | - | - | - |
| **Inventory & Stock** |
| Inventory stock | inventory | ✅ | inventory_total | ParquetProductSearchFields, ShopifyProductSearchFields | ⚠️ Partial |
| Number of variants | variant_number | ✅ | variant_number | ParquetProductSearchFields | ⚠️ Partial |
| Number of available variants | variant_number_available | ❌ | - | - | - |
| Variant stock ratio | variant_stock_ratio | ❌ | - | - | - |
| **Financial Metrics** |
| Discount % | discount_percent | ❌ | - | - | - |
| Discount amount | discount | ❌ | - | - | - |
| Cost | cost | ❌ | - | - | - |
| Profit | profit | ❌ | - | - | - |
| True profit | true_profit | ❌ | - | - | - |
| Margin | margin | ❌ | - | - | - |
| True margin | true_margin | ❌ | - | - | - |
| Sell through rate | sell_through_rate | ❌ | - | - | - |
| **Dates** |
| Created date | created_at | ✅ | created_at | ShopifyProductSearchFields | ⚠️ Partial |
| Published date | published_at | ✅ | published_at | ShopifyProductSearchFields | ⚠️ Partial |
| New inventory added date | new_inventory_added_date | ❌ | - | - | - |
| Restocked date | restock_date | ❌ | - | - | - |
| Last updated date | updated_at | ✅ | updated_at | ParquetCollectionSearchFields, ShopifyProductSearchFields | ⚠️ Partial |
| **Collection Information** |
| Collection title | collection | ✅ | title | ParquetCollectionSearchFields | ✅ Full |
| Collection handle | collection_handle | ✅ | handle | ParquetCollectionSearchFields | ✅ Full |
| Collection id | collection_id | ✅ | id | ParquetCollectionSearchFields, ShopifyProductSearchFields | ⚠️ Partial |
| **Other** |
| Random | position | ❌ | - | - | - |
| Price reduced | is_price_reduced | ✅ | is_price_reduced | ShopifyProductSearchFields | ⚠️ Partial |

### Legend
- ✅ **Full Match**: Field exists in both systems with compatible operators
- ⚠️ **Partial Match**: Field exists but operators differ or are limited
- ❌ **Not Available**: Field does not exist in FMS

### Operator Compatibility

| CM Operator | CM System | FMS Equivalent | Match Status |
|-------------|-----------|----------------|-------------|
| is equal to | == | = | ✅ Match |
| is not equal to | != | != | ✅ Match |
| is greater than | > | > | ✅ Match |
| is less than | < | < | ✅ Match |
| contains | contains | contains | ✅ Match |
| doesn't contain | not contain | doesNotContain | ⚠️ Similar |
| starts with | starts with | beginsWith | ✅ Match |
| ends with | ends with | endsWith | ✅ Match |
| is in the last | > | > (with date) | ⚠️ Similar |
| is not in the last | < | < (with date) | ⚠️ Similar |
| in the top | in the top | - | ❌ Not Available |
| in the bottom | in the bottom | - | ❌ Not Available |
| is not empty | is set | isNotNull | ⚠️ Similar |
| is empty | is not set | isNull | ⚠️ Similar |
| between | between | between | ✅ Match |

---

## Summary

### Fields Available in Both Systems
- **Product Information**: title, sku, vendor, handle, product_type
- **Analytics**: views, add_to_carts, checkouts, revenue, products_sold, net_revenue, conversion metrics
- **Inventory**: inventory_total (as inventory)
- **Dates**: created_at, published_at, updated_at
- **Collections**: title, handle, id

### Fields Only in Collection Manager
- **Financial**: cost, profit, true_profit, margin, true_margin, discount, discount_percent
- **Variant Details**: variant_inventory, variant_weight, variant_number_available, variant_stock_ratio
- **Dates**: new_inventory_added_date, restock_date
- **Other**: body_html, sell_through_rate, position (random)

### Fields Only in FMS
- **Shopify Specific**: barcode, bundles, category_id, delivery_profile_id, gift_card, publication_ids
- **Advanced Inventory**: inventory_levels, locations
- **GA Raw Data**: item_viewed, item_added_to_cart, item_checked_out, item_revenue
- **Order Details**: order_id, customer_id, quantity, price_discounted, net_price

### Operator Differences
- **Collection Manager** has special operators: "in the top", "in the bottom" (not in FMS)
- **FMS** has additional operators: "in", "notIn", "notBetween" (not in Collection Manager)
- **FMS** has more granular numeric operators: <=, >= (Collection Manager only has <, >)
- **FMS** has explicit null operators: isNull, isNotNull (Collection Manager uses "is set"/"is not set")

---

## Recommendations

1. **For Migration**: Fields with ✅ Full Match can be directly migrated
2. **For Partial Matches**: Review operator differences and implement conversion logic
3. **For Missing Fields**: Consider if these fields need to be added to FMS or if alternative fields can be used
4. **For Special Operators**: "in the top" and "in the bottom" may need custom implementation in FMS

---

*Last Updated: Generated from codebase analysis*
*Collection Manager Version: Based on constants.py*
*FMS Version: Based on ouiteo/fms/filters/*

