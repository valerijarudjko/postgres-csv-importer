# CSV to PostgreSQL Import Script

A lightweight and reusable Bash script to import any CSV file into any PostgreSQL database table from your macOS terminal.


## 🪿 How to use: 

```bash
importcsv <database_name> <table_name> <csv_file_name>
```
### Example:

```bash
importcsv flowers_db flowers_2024 flower_shop.csv
```

- `flowers_db` — any name of your PostgreSQL database
- `flowers_2024` — target table name (must already exist)
- `flower_shop.csv` — CSV file located on your Desktop

## Installation & copy:

### Step 1: Create the script file
nano ~/Desktop/tech/scripts/importcsv

### Step 2: Paste the following into nano and save:
#!/bin/bash

DB=$1
TABLE=$2
FILENAME=$3
USER="postgres"
DELIM=";"

psql -U $USER -d $DB -c "\copy $TABLE FROM '/Users/$(whoami)/Desktop/$FILENAME' DELIMITER '$DELIM' CSV HEADER ENCODING 'UTF8';"

### Step 3: Make the script executable
chmod +x ~/Desktop/tech/scripts/importcsv

### Step 4: Add to PATH (if not already)
echo 'export PATH=$PATH:$HOME/Desktop/tech/scripts' >> ~/.zprofile
source ~/.zprofile

### 🪿 Now you can run it like this:
importcsv flowers_db flowers_2024 flower_shop.csv

✅ Requirements

- PostgreSQL installed and accessible via `psql`
- CSV file uses `;` (semicolon or comma) as a primary delimiter
- CSV file is located on your Desktop
- Table in the database already exists and matches the CSV structure

(adjust to your needs)

##  Notes

- The script validates your input (must pass 3 arguments)
- Use UTF-8 encoded files with a header row


<<<< You can add to your script for usage check: >>>>

# Usage check
if [ "$#" -ne 3 ]; then
  echo "❗ Usage: importcsv <database_name> <table_name> <csv_file.csv>"
  echo "Example: importcsv flowers_db flowers_2024 flower_shop.csv"
  exit 1
fi
 



 ---
Created for PostgreSQL data projects.
#### Author: V.R

