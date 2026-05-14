# Data

The raw data used in this project is not included in this repository due to file size constraints.

## Download Instructions

1. Visit the [DANE official microdata portal](https://microdatos.dane.gov.co/index.php/catalog/ENChogares)
2. Select the **Gran Encuesta Integrada de Hogares (GEIH) 2023**
3. Download the monthly CSV files for all 12 months of 2023
4. Place the downloaded files in the `data/raw/` folder

## Data Structure

The GEIH 2023 dataset consists of 4 CSV files per month (48 files total), each approximately 10MB in size. The notebook integrates all monthly files into a single unified dataset at runtime.

## Variables Used

| Variable | Description |
|---|---|
| `P6880` | Workplace location |
| `P6800` | Hours worked |
| `P1800S1` | Company size |
| `informal` | Target variable (1 = informal, 0 = formal) |
