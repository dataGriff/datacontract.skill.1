# Data Contract Repository

This repository contains data contracts following the [Open Data Contract Specification (ODCS)](https://datacontract.com).

## 📊 View the Catalog

Once GitHub Pages is enabled, your data contract catalog will be automatically published at:
`https://datagriff.github.io/datacontract.skill.1/`

## 🚀 Setup GitHub Pages

To enable automatic publishing:

1. Go to your repository **Settings**
2. Navigate to **Pages** (in the left sidebar under "Code and automation")
3. Under **Source**, select **GitHub Actions**
4. Push changes to the `main` branch

The workflow will automatically:
- Generate an HTML catalog of all `*.yaml` data contracts
- Publish it to GitHub Pages
- Update on every push to main

## 📝 Data Contracts

### Cheese Inventory
- **File**: [cheese-inventory-contract.yaml](cheese-inventory-contract.yaml)
- **Description**: Tracks cheese inventory stock levels, product details, and storage conditions
- **Model**: `cheese_inventory` with 12 fields
- **Quality checks**: Freshness, completeness, uniqueness, and validity rules

### Whisky Inventory
- **File**: [whisky-inventory-contract.yaml](whisky-inventory-contract.yaml)
- **Description**: Tracks whisky inventory stock levels, product details, and storage conditions
- **Model**: `whisky_inventory` with 16 fields including distillery, age, region, and cask type
- **Quality checks**: Freshness, completeness, uniqueness, and validity rules for whisky-specific attributes

### Dog Inventory
- **File**: [dog-inventory-contract.yaml](dog-inventory-contract.yaml)
- **Description**: Tracks dog inventory for animal shelter or rescue, including dog details, health records, and adoption status
- **Models**: 
  - `dog_inventory` with 18 fields including breed, age, health status, adoption information, and rescue organization
  - `rescues` with 9 fields containing rescue organization information
- **Relationships**: Each dog references a rescue organization via the `rescue_id` foreign key
- **Quality checks**: Freshness, completeness, uniqueness, and validity rules for dog-specific attributes and rescue information

## 🛠️ Local Development

### Generate catalog locally
```bash
datacontract catalog --files "*.yaml" --output docs/
```

### Lint a data contract
```bash
datacontract lint datacontract.yaml
```

### Export to other formats
```bash
# Generate SQL DDL
datacontract export datacontract.yaml --format sql

# Generate dbt models
datacontract export datacontract.yaml --format dbt

# Generate Great Expectations suite
datacontract export datacontract.yaml --format great-expectations
```

## 📚 Learn More

- [Data Contract CLI Documentation](https://cli.datacontract.com)
- [ODCS Specification](https://datacontract.com)
- [Data Contract Examples](https://github.com/datacontract/datacontract-cli/tree/main/examples)