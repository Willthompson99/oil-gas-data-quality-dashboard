# Oil & Gas Well Data Quality Dashboard 🛢️

A comprehensive data quality monitoring system for oil and gas well production data, designed to demonstrate best practices in data governance, quality assessment, and business intelligence within the energy sector.

## 🎯 Project Objective

This project simulates a real-world data quality framework used in oil and gas operations to:
- Monitor and validate well production data integrity
- Identify data quality issues that could impact business decisions
- Provide actionable insights through automated quality checks
- Support data stewardship and governance initiatives

## 📊 Dataset Overview

The project uses simulated well production data (`well_production.csv`) containing:
- **5 well records** with various data quality issues intentionally included
- **9 data attributes** covering operational and production metrics
- **Realistic scenarios** including missing values, date inconsistencies, and outliers

### Key Data Fields
| Field | Description | Business Importance |
|-------|-------------|-------------------|
| `Well_ID` | Unique identifier for each well | Critical for tracking and reporting |
| `Volume_Produced` | Total oil/gas produced (bbls) | Key performance metric |
| `Spud_Date` | Drilling start date | Project timeline tracking |
| `Prod_Start/End` | Production period | Revenue calculation window |
| `Operator` | Operating company | Ownership and responsibility |
| `Status` | Well operational status | Asset management |

## 🔍 Data Quality Issues Detected

Our quality assessment framework identified several critical issues:

### 1. **Data Completeness Issues**
- Missing `Volume_Produced` for Well 1002 (Beta-2)
- Missing `Operator` for Well 1005 (Echo-5)

### 2. **Data Validity Issues**
- Negative production volume (-500 bbls) for Well 1004
- Production end date before start date for Well 1003

### 3. **Data Consistency Issues**
- Duplicate Well_ID entries detected
- Inconsistent operator naming ("Unknown" value)

### 4. **Statistical Anomalies**
- Production volume range: -500 to 200,000 bbls
- Average production: 128,625 bbls
- High variance indicating potential outliers

## 🛠️ Technical Architecture

```
┌─────────────────┐     ┌──────────────┐     ┌─────────────┐
│   Source Data   │ --> │    SQLite    │ --> │  Power BI   │
│  (ProCount CSV) │     │   Database   │     │  Dashboard  │
└─────────────────┘     └──────────────┘     └─────────────┘
                               |
                               v
                        ┌──────────────┐
                        │ Data Quality │
                        │    Rules     │
                        └──────────────┘
```

## 📋 Prerequisites

- **SQLite** (DB Browser for SQLite or SQLite Studio)
- **Power BI Desktop** or Excel for visualization
- **Python 3.x** (optional, for data generation)
- **Git** for version control

## 🚀 Getting Started

1. **Clone the repository**
   ```bash
   git clone https://github.com/Willthompson99/oil-gas-data-quality.git
   cd oil-gas-data-quality
   ```

2. **Import data into SQLite**
   ```sql
   -- Create the database and import CSV
   sqlite3 OilGasDataQuality.db
   .mode csv
   .import well_production.csv well_production
   ```

3. **Run data quality checks**
   - Execute queries from `SQL_Data_Quality_Results.md`
   - Review identified issues and patterns

4. **Create visualizations**
   - Connect Power BI to SQLite database
   - Build dashboard using provided metrics

## 📈 Data Quality Metrics

### Quality Dimensions Assessed
- **Completeness**: 80% (4/5 records have complete operator data)
- **Validity**: 60% (3/5 records pass all validation rules)
- **Consistency**: 80% (no duplicate Well_IDs found)
- **Accuracy**: Cannot be measured without source system comparison

## 📝 Business Rules & Validation

Key validation rules implemented:
1. `Volume_Produced` must be non-negative
2. `Prod_End` must be on or after `Prod_Start`
3. `Well_ID` must be unique across the dataset
4. `Operator` field should not be null or "Unknown"
5. All date fields must follow YYYY-MM-DD format

## 🎨 Dashboard Features

The Power BI dashboard includes:
- **Executive Summary**: Overall data quality score
- **Issue Tracker**: List of all quality violations
- **Trend Analysis**: Quality metrics over time
- **Drill-down Capability**: Investigate specific wells
- **Export Functionality**: Generate quality reports

## 📚 Documentation

- `Alation_Mockup_Documentation.md` - Business glossary and metadata
- `SQL_Data_Quality_Results.md` - Detailed query results and findings
- `README.md` - This file

## 🤝 Contributing

Contributions are welcome! Please:
1. Fork the repository
2. Create a feature branch (`git checkout -b feature/improvement`)
3. Commit changes (`git commit -m 'Add new quality rule'`)
4. Push to branch (`git push origin feature/improvement`)
5. Open a Pull Request

## 🔮 Future Enhancements

- [ ] Automated daily quality checks via scheduled jobs
- [ ] Integration with real-time production systems
- [ ] Machine learning for anomaly detection
- [ ] Email alerts for critical quality issues
- [ ] Expanded dataset with more wells and attributes
- [ ] RESTful API for quality metrics

## 📄 License

This project is licensed under the MIT License - see LICENSE file for details.

## 👤 Author

**Will Thompson**
- GitHub: [@Willthompson99](https://github.com/Willthompson99)
- LinkedIn: [Connect with me](https://linkedin.com/in/willthompson)

## 🙏 Acknowledgments

- Inspired by real-world data quality challenges in the energy sector
- Built using industry-standard tools and best practices
- Special thanks to the data governance community

---

*"Quality data drives quality decisions in the oil & gas industry"*
