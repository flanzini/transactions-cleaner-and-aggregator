# Transactions Cleaner and Aggregator

Small personal project to automate one of my recurring finance tasks:
parsing monthly transaction exports from different sources and generating
a single, clean CSV file aggregating all transactions.

I originally built this as a Jupyter notebook to avoid manually copying
and pasting data into Excel every month.

## What it does

- Loads raw transactions exported from one or more sources (e.g. TradeRepublic PDF monthly account statement, Revolut monthly Excel statement...)
- Parses amounts and descriptions from semi-structured text
- Normalizes column names and formats (date, description, amount)
- Combines multiple sources into a single DataFrame
- Exports a consolidated CSV file like:

  `AllTransactions_MMYY.csv`  (e.g. `AllTransactions_0325.csv`)

## Tech stack

- Python
- Jupyter Notebook
- pandas
- datetime

## High-level flow

1. Compute the reference month/year (e.g. "previous month" from the current date).
2. Load input data for that month (e.g. statement exports) from local files.
3. Parse and clean each source (handle description lines, split amounts, normalize signs).
4. Append everything into one combined DataFrame.
5. Write the final CSV to disk with the pattern `AllTransactions_{month}{year}.csv`.

The notebook is step-by-step and commented so it can be adapted to other export formats.

## Usage

1. Clone the repo:
   ```bash
   git clone https://github.com/<your-username>/transactions-cleaner-and-aggregator.git
   cd transactions-cleaner-and-aggregator
   ```

2. (Optional) Create and activate a virtual environment.

3. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

4. Launch Jupyter and open the notebook:
   ```bash
   jupyter notebook transactions_cleaner_and_aggregator.ipynb
   ```

5. Update the input paths in the first cells to point to your own monthly
   statements / exports.

6. Run the notebook cells from top to bottom. At the end you should see a
   consolidated CSV written to disk.

> **Note:** The `sample_data/example_transactions.csv` file is synthetic
> and provided only as an example. Do not commit or share your real
> financial data.

## Disclaimer

This project was built for personal finance tracking and is shared as-is
for educational and inspirational purposes. Please review and adapt the
logic before using it with your own data.
