# Point Data Schema

## Overview
This document describes the schema and format of the point data for Client 1.

## Data Format
Point data is available in two formats:
- **CSV**: `data/points.csv` - Tabular format suitable for spreadsheet applications
- **JSON**: `data/points.json` - Structured format suitable for programmatic access

## Coordinate System
All coordinates use the **WGS84** (World Geodetic System 1984) coordinate system.

## Data Fields

### id
- **Type**: Integer
- **Description**: Unique identifier for each point
- **Example**: 1, 2, 3, ...

### name
- **Type**: String
- **Description**: Human-readable name for the point
- **Example**: "Point_A", "Point_B"

### latitude
- **Type**: Decimal number
- **Description**: Latitude coordinate in decimal degrees
- **Range**: -90 to 90
- **Example**: 40.7128

### longitude
- **Type**: Decimal number
- **Description**: Longitude coordinate in decimal degrees
- **Range**: -180 to 180
- **Example**: -74.0060

### elevation
- **Type**: Decimal number
- **Description**: Elevation above sea level in meters
- **Example**: 10.5

### timestamp
- **Type**: ISO 8601 datetime string
- **Description**: Date and time when the point was recorded
- **Format**: YYYY-MM-DDTHH:MM:SSZ
- **Example**: "2025-01-15T10:30:00Z"

### category
- **Type**: String (enumerated)
- **Description**: Classification of the point
- **Allowed Values**: 
  - `primary` - Main reference or measurement points
  - `secondary` - Supporting observation points
  - `tertiary` - Additional control or marker points
- **Example**: "primary"

### description
- **Type**: String
- **Description**: Textual description of the point and its purpose
- **Example**: "Reference point in downtown area"

## Data Statistics
- **Total Points**: 10
- **Primary Points**: 4
- **Secondary Points**: 4
- **Tertiary Points**: 2

## Usage Examples

### Reading CSV in Python
```python
import csv

with open('data/points.csv', 'r') as f:
    reader = csv.DictReader(f)
    for row in reader:
        print(f"Point {row['id']}: {row['name']} at ({row['latitude']}, {row['longitude']})")
```

### Reading JSON in Python
```python
import json

with open('data/points.json', 'r') as f:
    data = json.load(f)
    for point in data['points']:
        print(f"Point {point['id']}: {point['name']} at ({point['latitude']}, {point['longitude']})")
```

### Reading CSV in JavaScript/Node.js
```javascript
const fs = require('fs');
const csv = require('csv-parser');

fs.createReadStream('data/points.csv')
  .pipe(csv())
  .on('data', (row) => {
    console.log(`Point ${row.id}: ${row.name} at (${row.latitude}, ${row.longitude})`);
  });
```

### Reading JSON in JavaScript/Node.js
```javascript
const fs = require('fs');

const data = JSON.parse(fs.readFileSync('data/points.json', 'utf8'));
data.points.forEach(point => {
  console.log(`Point ${point.id}: ${point.name} at (${point.latitude}, ${point.longitude})`);
});
```

## Data Validation
All point data has been validated to ensure:
- Unique IDs for each point
- Valid coordinate ranges (latitude: -90 to 90, longitude: -180 to 180)
- Proper ISO 8601 timestamp format
- Valid category values (primary, secondary, tertiary)
- Non-empty descriptions

## Version History
- **v1.0** (2025-01-15): Initial dataset with 10 points
