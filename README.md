# End-to-End Data Engineering Project on Databricks

## Overview
This project implements a complete data engineering pipeline using the **Medallion Architecture** (Bronze, Silver, Gold layers) on Databricks. It demonstrates best practices for data ingestion, transformation, and storage using Delta Lake and PySpark.

## Project Architecture

### Medallion Architecture Layers

```
📁 Bronze Layer (Raw Data)
   ├── Customer Data Ingestion
   └── Product Data Ingestion
   
📁 Silver Layer (Cleaned & Validated)
   └── Data Transformations
   
📁 Gold Layer (Business-Ready)
   └── Aggregated Analytics
```

## Features

- **Delta Lake Integration**: All data stored in Delta format for ACID transactions and time travel capabilities
- **Incremental Loading**: Supports append mode for continuous data ingestion
- **Audit Tracking**: Automatic ingestion timestamp for all records
- **Data Archiving**: CSV files archived after successful processing
- **Schema Management**: Database and table creation with proper schema inference

## Project Structure

```
end_to_end_data_engineering_project_on_databricks/
│
├── notebooks/
│   ├── Bronze_layer_DB_Creation.ipynb       # Creates bronze_layer database
│   ├── Bronze_layer_customer_load.ipynb     # Ingests customer data to Delta
│   └── Bronze_layer_product_load.ipynb      # Ingests product data to Delta
│
├── README.md                                 # Project documentation
└── LICENSE                                   # License information
```

## Data Sources

### Customer Data
- **Source**: CSV files from workspace
- **Schema**: customer_id, name, email, country, customer_type, registration_date, age, gender, total_purchases
- **Target Table**: `bronze_layer.bronze_customer`

### Product Data
- **Source**: CSV files from workspace
- **Target Table**: `bronze_layer.bronze_product`

## Technologies Used

- **Apache Spark**: Distributed data processing
- **Delta Lake**: Reliable data lake storage
- **PySpark**: Python API for Spark
- **Databricks**: Unified analytics platform
- **Python**: Data processing and transformations

## Getting Started

### Prerequisites
- Databricks workspace access
- Cluster with Databricks Runtime (DBR)
- Source data files in workspace

### Setup Instructions

1. **Clone this repository** to your Databricks workspace:
   ```bash
   git clone https://github.com/musawenkosikhulu/end_to_end_data_engineering_project_on_databricks.git
   ```

2. **Import notebooks** to your Databricks workspace:
   - Navigate to Workspace → Import
   - Select the `notebooks/` folder

3. **Run notebooks in sequence**:
   - `Bronze_layer_DB_Creation.ipynb` - Creates the bronze database
   - `Bronze_layer_customer_load.ipynb` - Loads customer data
   - `Bronze_layer_product_load.ipynb` - Loads product data

4. **Verify data ingestion**:
   ```sql
   USE bronze_layer;
   SELECT * FROM bronze_customer LIMIT 10;
   SELECT * FROM bronze_product LIMIT 10;
   ```

## Database Schema

### bronze_layer.bronze_customer
 Column | Type | Description |
--------|------|-------------|
 customer_id | int | Unique customer identifier |
 name | string | Customer name |
 email | string | Customer email |
 country | string | Customer country |
 customer_type | string | Customer tier (Regular/Premium/VIP) |
 registration_date | date | Registration date |
 age | int | Customer age |
 gender | string | Customer gender |
 total_purchases | int | Total purchases count |
 ingestion_timestamp | timestamp | Record ingestion time |

## Development Roadmap

- [x] Bronze layer implementation
- [ ] Silver layer transformations
- [ ] Gold layer aggregations
- [ ] Data quality checks
- [ ] Automated pipeline orchestration
- [ ] Real-time streaming ingestion

## Best Practices Implemented

✅ **Incremental Loading** - Append mode for new data  
✅ **Schema Inference** - Automatic schema detection  
✅ **Audit Columns** - Ingestion timestamps for tracking  
✅ **Delta Format** - ACID transactions and versioning  
✅ **Data Archival** - CSV file management post-ingestion  
✅ **Modular Design** - Separate notebooks for each layer  

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

This project is licensed under the terms specified in the LICENSE file.

## Author

**Musawenkosi Khulu**  
📧 musakhulu.mk@gmail.com  
🔗 [GitHub](https://github.com/musawenkosikhulu)

## Acknowledgments

- Databricks Community
- Apache Spark Documentation
- Delta Lake Open Source Project

---

**Note**: This project is part of a learning journey in data engineering on Databricks. For production use, additional considerations for security, monitoring, and error handling should be implemented.
