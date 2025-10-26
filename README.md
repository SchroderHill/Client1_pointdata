# Client1_pointdata

Point data collection and management repository for Client 1.

## Overview
This repository contains geographic point data for Client 1, including coordinates, elevations, timestamps, and metadata for various survey and measurement points.

## Data Location
All point data is stored in the `data/` directory:
- **CSV Format**: `data/points.csv` - Suitable for spreadsheet applications and tabular analysis
- **JSON Format**: `data/points.json` - Suitable for programmatic access and API integration
- **Schema Documentation**: `data/SCHEMA.md` - Detailed field descriptions and usage examples

## Quick Start

### Viewing the Data
The point data can be opened directly in:
- Spreadsheet applications (Excel, Google Sheets, LibreOffice Calc) using the CSV file
- Text editors or JSON viewers using the JSON file
- GIS software by importing the CSV/JSON with coordinate columns

### Data Structure
Each point includes:
- Unique identifier
- Name/label
- Latitude and longitude (WGS84)
- Elevation (meters above sea level)
- Timestamp (ISO 8601 format)
- Category (primary/secondary/tertiary)
- Description

### Example Data
```
ID: 1
Name: Point_A
Location: 40.7128, -74.0060
Elevation: 10.5m
Category: primary
```

## Dataset Information
- **Total Points**: 10
- **Coordinate System**: WGS84
- **Elevation Unit**: Meters
- **Data Version**: 1.0
- **Last Updated**: 2025-01-15

## Usage

### Reading CSV (Python)
```python
import csv

with open('data/points.csv', 'r') as f:
    reader = csv.DictReader(f)
    for row in reader:
        print(f"{row['name']}: ({row['latitude']}, {row['longitude']})")
```

### Reading JSON (Python)
```python
import json

with open('data/points.json', 'r') as f:
    data = json.load(f)
    for point in data['points']:
        print(f"{point['name']}: ({point['latitude']}, {point['longitude']})")
```

### Reading with Pandas (Python)
```python
import pandas as pd

# Read CSV
df = pd.read_csv('data/points.csv')
print(df.head())

# Read JSON
import json
with open('data/points.json', 'r') as f:
    data = json.load(f)
df = pd.DataFrame(data['points'])
print(df.head())
```

## Data Quality
All data has been validated for:
- ✅ Unique point identifiers
- ✅ Valid coordinate ranges
- ✅ Proper timestamp format
- ✅ Consistent field structure
- ✅ Complete metadata

## Documentation
For detailed information about data fields, formats, and advanced usage examples, see:
- [Data Schema Documentation](data/SCHEMA.md)

## Support
For questions or issues regarding this point data, please open an issue in this repository.

## License
This data is proprietary to Client 1. Unauthorized distribution or use is prohibited.