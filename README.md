# Manabox Inventory Merger

A Python script that merges duplicate entries in Magic: The Gathering card inventory CSV files exported from Manabox, consolidating quantities while preserving all card details.

## Features

- Automatically combines duplicate card entries based on identifying characteristics
- Preserves card details including name, set, condition, foil status, and language
- Sums quantities for identical cards
- Calculates average purchase prices for merged entries
- Provides detailed statistics before and after merging
- Includes data verification to ensure no cards are lost during the process
- User-friendly file selection dialog

## Requirements

- Python 3.6 or higher
- pandas library
- numpy library
- tkinter (usually included with Python)

## Installation

1. **Install Python**: Download and install Python from [python.org](https://www.python.org/downloads/)

2. **Install required libraries**:
   ```bash
   pip install pandas numpy
   ```

3. **Download the script**: Save `main.py` to your desired directory

## Usage

### Basic Usage

1. **Run the script**:
   ```bash
   python main.py
   ```

2. **Select your CSV file**: A file dialog will open. Navigate to and select your Manabox inventory CSV file.

3. **Review the output**: The script will display:
   - Original inventory statistics
   - Merged inventory statistics
   - Verification results
   - Preview of merged data

4. **Find your merged file**: The output will be saved as `inventory_merged.csv` in the same directory as the script.

### Expected CSV Format

The script expects a CSV file with the following columns:
- Name
- Set code
- Collector number
- Language
- Foil
- Condition
- Quantity
- Scryfall ID
- Purchase price
- Altered
- Purchase price currency

## How It Works

The script identifies duplicate cards by comparing these key attributes:
- Card name
- Set code
- Collector number
- Language
- Foil status (foil/normal)
- Condition
- Purchase price currency
- Altered status
- Scryfall ID

When duplicates are found, the script:
- Sums the quantities
- Calculates the average purchase price
- Keeps one entry with the combined data

## Output Example

```
--- ORIGINAL INVENTORY STATISTICS ---
Total cards: 1,247
Foil cards: 89
Normal cards: 1,158
Total entries (rows): 543

--- MERGED INVENTORY STATISTICS ---
Total cards: 1,247
Foil cards: 89
Normal cards: 1,158
Total entries (rows): 398

--- VERIFICATION ---
Total quantities match: True (1247 → 1247)
Foil quantities match: True (89 → 89)
Normal quantities match: True (1158 → 1158)
ALL VERIFICATIONS PASSED - Merge completed successfully!
```

## Troubleshooting

### Common Issues

**"No module named 'pandas'" error**:
```bash
pip install pandas numpy
```

**"No file selected" message**:
- Ensure you click on a CSV file in the file dialog
- Check that the file has a `.csv` extension

**"FileNotFoundError" error**:
- Verify the CSV file exists in the specified location
- Ensure you have read permissions for the file

**Verification failed**:
- This indicates a potential issue with the merge process
- Check the original CSV file for unusual data or formatting issues
- Contact support with the error details

### File Location

By default, the merged file is saved as `inventory_merged.csv` in the same directory where you run the script. To change the output location, modify line 120 in the script:

```python
output_filename = 'path/to/your/desired/output.csv'
```

## Technical Details

- **Version**: 2.0.0
- **Language**: Python
- **Dependencies**: pandas, numpy, tkinter
- **Input Format**: CSV (Comma-Separated Values)
- **Output Format**: CSV with merged duplicate entries

## Data Safety

- The script never modifies your original file
- All changes are saved to a new file (`inventory_merged.csv`)
- Verification checks ensure no data is lost during merging
- Backup your original file before processing as a precaution

## License

This project is provided as-is for personal use.