# E-commerce Demo Dataset

This dataset simulates a subscription-based e-commerce company (like a subscription box service) with 20 customers. All data is linked via `customer_id` and `email`.

## Data Sources

| File | Source | Description |
|------|--------|-------------|
| `customers.csv` | Internal | Customer master data with subscription info |
| `klaviyo_marketing.csv` | Klaviyo | Raw email marketing events |
| `shopify_subscriptions.csv` | Shopify | Raw subscription order events |
| `gorgias_helpdesk.csv` | Gorgias | Raw support ticket events |
| `shipstation_logistics.csv` | ShipStation | Raw shipment tracking events |

---

## Sample Questions

### Delivery & Fulfillment
- "Which orders have delivery exceptions?"
- "Who has packages lost in transit?"
- "Show me all stalled shipments"
- "What's our delivery success rate by carrier?"
- "List customers waiting more than 7 days for delivery"

### Churn & Risk Analysis
- "Which customers are at risk of churning?"
- "Show me customers with delivery issues AND support tickets"
- "Who has refund-related tickets?"
- "List angry customers with shipping exceptions"
- "Which VIP customers have open issues?"

### Revenue & Subscriptions
- "What's our total subscription revenue this month?"
- "Show me revenue by subscription plan"
- "Who are our highest LTV customers?"
- "What's the average order value by plan?"
- "List customers with upcoming billing dates"

### Marketing & Engagement
- "What's our email open rate by campaign?"
- "Which campaigns have the highest click rates?"
- "Show me customers who haven't engaged with emails"
- "List VIP customers and their email engagement"
- "What's the engagement rate for retention campaigns?"

### Support Analysis
- "How many open tickets do we have?"
- "What's the most common ticket category?"
- "Show me customers with multiple open tickets"
- "What's our average resolution time?"
- "List tickets mentioning refunds"

### Cross-Source Analysis
- "Find customers with delivery issues who also opened support tickets"
- "Which high-LTV customers have shipping problems?"
- "Show me customers with refund tickets AND stalled shipments"
- "List VIP customers with negative experiences across all touchpoints"
- "Which customers have delivery exceptions but haven't contacted support yet?"

---

## Schema Reference

### customers.csv
| Column | Type | Description |
|--------|------|-------------|
| customer_id | string | Unique customer identifier |
| email | string | Customer email |
| first_name | string | Customer first name |
| signup_date | date | Signup date |
| subscription_status | string | Active/Cancelled/Paused |
| lifetime_value | integer | Customer LTV ($) |
| subscription_plan | string | Basic/Premium/VIP |

### klaviyo_marketing.csv
| Column | Type | Description |
|--------|------|-------------|
| event_id | string | Unique event identifier |
| customer_id | string | Customer identifier |
| email | string | Customer email |
| event_type | string | email_sent/email_opened/email_clicked |
| event_timestamp | timestamp | Event timestamp |
| campaign_name | string | Marketing campaign name |
| email_subject | string | Email subject line |
| clicked | boolean | Whether email was clicked |
| opened | boolean | Whether email was opened |

### shopify_subscriptions.csv
| Column | Type | Description |
|--------|------|-------------|
| order_id | string | Unique order identifier |
| customer_id | string | Customer identifier |
| email | string | Customer email |
| order_date | date | Order date |
| amount | integer | Order amount ($) |
| product_name | string | Product name |
| subscription_type | string | monthly/quarterly/annual |
| next_billing_date | date | Next billing date |

### gorgias_helpdesk.csv
| Column | Type | Description |
|--------|------|-------------|
| ticket_id | string | Unique ticket identifier |
| customer_id | string | Customer identifier |
| email | string | Customer email |
| created_at | timestamp | Ticket creation time |
| resolved_at | timestamp | Resolution time (null if open) |
| status | string | open/resolved |
| category | string | delivery/refund/question |
| sentiment | string | Angry/Frustrated/Neutral/Happy |
| subject | string | Ticket subject |

### shipstation_logistics.csv
| Column | Type | Description |
|--------|------|-------------|
| shipment_id | string | Unique shipment identifier |
| order_id | string | Order identifier |
| customer_id | string | Customer identifier |
| email | string | Customer email |
| shipped_at | timestamp | Shipment date |
| delivered_at | timestamp | Delivery date (null if not delivered) |
| status | string | In Transit/Delivered/Stalled/Exception |
| carrier | string | UPS/FEDEX/USPS/DHL |
| tracking_number | string | Tracking number |
| exception_reason | string | Lost in Transit/Damaged/Weather Delay/Address Issue |
