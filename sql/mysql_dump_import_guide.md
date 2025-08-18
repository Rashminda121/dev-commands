# MySQL Dump & Import Process (1000 rows per table)

## Step 1: Prepare the environment

1. Create a folder for dumps:

```powershell
mkdir C:\Users\<USER>\Documents\dumps
```

2. Set your MySQL password temporarily in PowerShell (avoids prompt):

```powershell
$env:MYSQL_PWD = "<YOUR_PASSWORD>"
```

Replace `<YOUR_PASSWORD>` with your actual MySQL password.

---

## Step 2: Dump each table (1000 rows each) using `mysqldump`

Use `--single-transaction` to avoid `LOCK TABLES` errors.

```powershell
$dumpFolder = "C:\Users\<USER>\Documents\dumps"

# List of tables to dump
$tables = @(
    "table1", "table2", "table3", "table4",
    "table5", "table6", "table7", "table8",
    "table9", "table10", "table11", "table12",
    "table13", "table14", "table15", "table16",
    "table17", "table18"
)

# Loop to dump all tables
foreach ($table in $tables) {
    Write-Host "Dumping $table..."
    mysqldump -u <USERNAME> -h <HOST> <DATABASE> $table --where="1 LIMIT 1000" --single-transaction > "$dumpFolder\$table.sql"
}
```

- Replace `<USERNAME>`, `<HOST>`, `<DATABASE>` with your MySQL credentials.
- Each table will be saved as its own `.sql` file.

---

## Step 3: Create the target database (if it doesn’t exist)

```powershell
mysql -u <ROOT_USER> -h <HOST> -e "CREATE DATABASE IF NOT EXISTS <DATABASE>;"
```

- Replace `<ROOT_USER>`, `<HOST>`, `<DATABASE>` accordingly.

---

## Step 4: Import all SQL files into the database

```powershell
Get-ChildItem -Path $dumpFolder -Filter *.sql | ForEach-Object {
    Write-Host "Importing $($_.Name)..."
    Get-Content $_.FullName | mysql -u <ROOT_USER> -h <HOST> <DATABASE>
}
```

- Each `.sql` file will be executed in the target database.
- Ensure the folder path and database names are correct.

---

## Step 5: Verify data import

```powershell
mysql -u <ROOT_USER> -h <HOST> -e "USE <DATABASE>; SHOW TABLES;"
```

```powershell
mysql -u <ROOT_USER> -h <HOST> -e "SELECT * FROM table1 LIMIT 5;" <DATABASE>
```

- Replace `<DATABASE>` and table names as needed.
- Check that your data has been imported successfully.

