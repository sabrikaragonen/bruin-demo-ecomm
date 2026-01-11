# E-commerce Pipeline

## How to Query Data

**Use Bruin MCP tools to query data.** Do NOT write Python scripts or functions to fetch data. Bruin MCP provides direct database access - use it.

## CRITICAL: Dataset Prefix Required

**Dataset:** `ecomm`
**Project:** `bruin-demo-data`

**ALWAYS prefix table names with `ecomm.` in ALL queries.**

```sql
-- CORRECT
SELECT * FROM ecomm.customers;

-- WRONG (will fail)
SELECT * FROM customers;
```

## Available Tables

- `ecomm.customers` - Customer master data
- `ecomm.shopify_subscriptions` - Subscription orders from Shopify
- `ecomm.klaviyo_marketing` - Email marketing events from Klaviyo
- `ecomm.gorgias_helpdesk` - Support tickets from Gorgias
- `ecomm.shipstation_logistics` - Shipment tracking from ShipStation

Table schemas are defined in `assets/*.asset.yml` files.

## Key Relationships

- `customer_id` links customers to orders, tickets, marketing events, and shipments
- `order_id` links shopify_subscriptions to shipstation_logistics
