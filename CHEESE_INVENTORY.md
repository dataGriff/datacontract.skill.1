# Cheese Inventory Data Contract

## Overview
This data contract defines the structure and quality requirements for the cheese inventory management system. It follows the Open Data Contract Specification (ODCS) version 1.2.1.

## Data Model

### Table: `cheese_inventory`

The main table containing all cheese inventory data with the following fields:

| Field Name | Type | Required | Description |
|------------|------|----------|-------------|
| `cheese_id` | string | Yes (Primary Key) | Unique identifier for each cheese item |
| `cheese_name` | string | Yes | Name of the cheese (e.g., Cheddar, Brie, Gouda) |
| `cheese_type` | string | Yes | Category of cheese (Hard, Semi-hard, Semi-soft, Soft, Blue, Fresh) |
| `origin_country` | string | No | Country of origin for the cheese |
| `milk_type` | string | Yes | Type of milk used (Cow, Goat, Sheep, Buffalo, Mixed) |
| `quantity_kg` | decimal | Yes | Current quantity in stock measured in kilograms |
| `unit_price` | decimal | Yes | Price per kilogram in USD |
| `aging_months` | integer | No | Number of months the cheese has been aged |
| `production_date` | date | Yes | Date when the cheese was produced |
| `expiry_date` | date | Yes | Expected expiry date of the cheese |
| `storage_location` | string | Yes | Physical location where the cheese is stored |
| `temperature_celsius` | decimal | Yes | Current storage temperature in Celsius |
| `humidity_percent` | decimal | Yes | Current storage humidity percentage |
| `last_updated` | timestamp | Yes | Timestamp of the last inventory update |

## Valid Values

### Cheese Types
- Hard
- Semi-hard
- Semi-soft
- Soft
- Blue
- Fresh

### Milk Types
- Cow
- Goat
- Sheep
- Buffalo
- Mixed

## Data Quality Rules

The contract includes comprehensive quality checks:

### Uniqueness
- Cheese ID must be unique (no duplicates)

### Completeness
- All required fields must have values (no nulls)
- 12 required fields enforced

### Validity
- Cheese type must be one of the valid categories
- Milk type must be one of the valid sources
- Quantity cannot be negative
- Unit price must be positive
- Aging months cannot be negative
- Storage temperature must be between -10°C and 25°C
- Humidity percentage must be between 0% and 100%

### Freshness
- Data must be updated within the last hour

## Service Levels

| SLA | Specification |
|-----|---------------|
| **Availability** | 99.9% uptime, 24/7 |
| **Retention** | 7 years for regulatory compliance |
| **Freshness** | Real-time updates (< 1 hour) |
| **Frequency** | Streaming (continuous updates) |
| **Support** | 24/7 with 15-minute response time |

## Usage

### Validating the Contract

```bash
datacontract lint cheese-inventory-datacontract.yaml
```

### Testing Data Quality

```bash
datacontract test cheese-inventory-datacontract.yaml
```

Note: Testing requires access to the actual data source configured in the contract.

### Exporting to Other Formats

```bash
# Export as SQL DDL
datacontract export cheese-inventory-datacontract.yaml --format sql

# Export as JSON Schema
datacontract export cheese-inventory-datacontract.yaml --format jsonschema

# Export as dbt model
datacontract export cheese-inventory-datacontract.yaml --format dbt
```

## Data Location

**Production**: `./data/cheese_inventory.parquet`

## Terms of Use

- **Usage**: Internal inventory management and reporting purposes only
- **Limitations**: Data should not be shared externally without proper authorization
- **Notice Period**: 30 days

## Contact

**Owner**: Inventory Management Team  
**Team**: Cheese Operations  
**Email**: cheese-ops@example.com

## Version History

| Version | Date | Changes |
|---------|------|---------|
| 1.0.0 | 2026-01-03 | Initial release of cheese inventory data contract |
