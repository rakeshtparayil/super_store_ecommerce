# Super Ecommerce Project

## Project Overview
This project focuses on advanced analytics for an ecommerce platform, including customer lifetime value (CLV) calculations, feature engineering, database optimization, and visualization of key performance indicators. The analysis provides strategic insights for business decision-making across product categories, customer segments, and geographical regions.

## Data Dictionary

### Customer Tables
| Column | Description | Data Type |
|--------|-------------|-----------|
| customer_id | Unique identifier for each customer | STRING |
| name | Customer's full name | STRING |
| email | Customer's email address | STRING |
| segment | Customer segment (Consumer, Corporate, Home Office) | STRING |
| region | Geographical region | STRING |
| state | State location | STRING |
| city | City location | STRING |
| postal_code | Postal/ZIP code | INTEGER |
| join_date | Date customer joined the platform | DATE |
| last_active_date | Date of customer's most recent activity | DATE |

### Order Tables
| Column | Description | Data Type |
|--------|-------------|-----------|
| order_id | Unique order identifier | STRING |
| customer_id | Reference to customer | STRING |
| order_date | Date order was placed | DATE |
| ship_date | Date order was shipped | DATE |
| ship_mode | Shipping method selected | STRING |
| shipping_cost | Cost of shipping | FLOAT |
| returned | Whether order was returned (Yes/No) | BOOLEAN |

### Product Tables
| Column | Description | Data Type |
|--------|-------------|-----------|
| product_id | Unique identifier for each product | STRING |
| category | Main product category | STRING |
| sub_category | Product subcategory | STRING |
| product_name | Name of the product | STRING |
| base_price | Original price before discounts | FLOAT |
| discount | Discount amount applied | FLOAT |
| quantity | Quantity ordered | INTEGER |
| profit | Profit generated from sale | FLOAT |
| profit_margin | Profit as percentage of sales | FLOAT |

### Sales Metrics Tables
| Column | Description | Data Type |
|--------|-------------|-----------|
| traditional_clv | Customer lifetime value based on historical purchases | FLOAT |
| profit_adjusted_clv | CLV adjusted for profitability | FLOAT |
| composite_clv | Comprehensive CLV incorporating multiple factors | FLOAT |
| discount_sensitivity | Customer responsiveness to discounts | FLOAT |
| purchase_frequency | Average number of purchases per time period | FLOAT |
| avg_order_value | Average value of customer orders | FLOAT |
| retention_rate | Percentage of returning customers | FLOAT |

## Feature Engineering

### Customer Features
- **Recency**: Days since last purchase
- **Frequency**: Number of purchases in time period
- **Monetary Value**: Total spend in time period
- **Discount Sensitivity**: Correlation between purchase amount and discount level
- **Category Loyalty**: Percentage of purchases within dominant category
- **Seasonal Purchase Patterns**: Purchase distribution across seasons

### Product Features
- **Profit Margin**: Profit as percentage of revenue
- **Return Rate**: Percentage of units returned
- **Cross-Sell Potential**: Correlation with other category purchases
- **Price Elasticity**: Sales response to price changes
- **Seasonal Popularity**: Seasonal sales patterns
- **Category Position**: Performance relative to category average

### Geographic Features
- **Regional Performance**: Sales and profitability by region
- **State Quadrant Analysis**: States mapped by profit and discount sensitivity
- **Urban/Rural Split**: Performance differences by population density
- **Shipping Cost Impact**: Effect of shipping costs on order completion

## Database Design

### Database Schema
The project utilizes a normalized database design with the following structure:
- **Customers**: Core customer demographic data
- **Products**: Product catalog information
- **Orders**: Order header information
- **OrderItems**: Line items for each order
- **Geography**: Regional, state, and city information
- **TimeCalendar**: Date dimension for time-based analysis
- **Metrics**: Pre-calculated KPIs and metrics

### Database Implementation
Two parallel database implementations were created:
1. **PostgreSQL**: Primary production database with complete dataset
   - Optimized for complex queries and reporting
   - Includes materialized views for performance
   - Partitioned by date ranges for query efficiency

2. **SQLite**: Lightweight implementation for development and portability
   - Contains subset of data for testing
   - Simplified schema for rapid development
   - Easily shareable with team members

### Data Segmentation
Data was segmented into logical groups to optimize analysis:
- **Customer Segments**: Consumer, Corporate, Home Office
- **Product Categories**: Furniture, Office Supplies, Technology
- **Geographic Regions**: East, West, Central, South
- **Performance Tiers**: High, Medium, Low value customers

## Data Visualization (Tableau)

### Dashboard 1: Executive Overview
- Overall sales performance and trends
- Key KPIs by category and region
- CLV distribution across customer segments

### Dashboard 2: Customer Analysis
- Customer segmentation analysis
- Retention and churn visualization
- RFM (Recency, Frequency, Monetary) analysis

### Dashboard 3: Product Performance
- Category and subcategory analysis
- Profit margin by product type
- Return rate analysis

### Dashboard 4: Geographic Insights
- State quadrant analysis (profit vs. discount sensitivity)
- Regional performance comparison
- Shipping impact by location

### Dashboard 5: CLV Deep Dive
- CLV comparison across subcategories
- Traditional vs. adjusted CLV analysis
- Customer lifecycle visualization

## KPI Calculations

### Customer Lifetime Value (CLV)
Three different CLV calculation methodologies were implemented:

1. **Traditional CLV**:
Traditional CLV = Average Order Value × Purchase Frequency × Customer Lifespan

2. **Profit-Adjusted CLV**:
Profit-Adjusted CLV = Average Order Profit × Purchase Frequency × Customer Lifespan

3. **Composite CLV**:
Composite CLV = (0.7 × Profit-Adjusted CLV) + (0.2 × Retention Factor × Base CLV) + (0.1 × Growth Potential)

## Running the Project

### Prerequisites
- Python 3.8+
- PostgreSQL 12+
- Tableau Desktop/Public
- Required Python packages: pandas, numpy, scikit-learn, psycopg2, sqlalchemy

### Setup Instructions
1. Clone the repository

git clone https://github.com/username/super-ecommerce.git