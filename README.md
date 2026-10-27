Day 8 Project: Sales Tracker in Google Sheets
Project Overview
This project is a lightweight sales tracker built in Google Sheets. It records sample retail transactions and calculates sales totals automatically. A separate summary tab rolls up sales by day, week, and month.
Objectives
- Keep raw sales entries separate from summary calculations.
- Calculate each transaction's sales value from quantity and unit price.
- Summarize sales for daily, weekly, and monthly periods.
- Reduce data-entry errors using data validation.
- Verify the formulas against the sample entries.
Workbook Structure
1. Sales_Data
This tab contains the source entries.
Column	Field	Description
A	Date	Date of the transaction
B	Product	Product sold
C	Category	Product category
D	Quantity	Units sold
E	Unit Price	Price per unit
F	Total Sales	Quantity multiplied by unit price


In F2, use =D2*E2 and fill the formula down for each transaction.
2. Summary
This tab contains headline metrics and sales rollups:
- Total sales
- Total quantity sold
- Number of transactions
- Daily sales by date
- Weekly sales by Monday-starting week
- Monthly sales by calendar month
Key Formulas
The examples below match the workbook's sample data. When adding more records, extend bounded ranges or use open-ended ranges where appropriate.
Purpose	Example formula
Total sales	=SUM(Sales_Data!F2:F11)
Total quantity sold	=SUM(Sales_Data!D2:D)
Number of transactions (sample rows)	=COUNTA(Sales_Data!B2:B11)
Number of transactions (ongoing use)	=COUNTA(Sales_Data!B2:B)
Daily total, with date in A10	=SUMIF(Sales_Data!A:A,A10,Sales_Data!F:F)
Weekly total, with week start in D10	=SUMIFS(Sales_Data!F:F,Sales_Data!A:A,">="&D10,Sales_Data!A:A,"<"&D10+7)
Monthly total, with month start in G10	=SUMIFS(Sales_Data!F:F,Sales_Data!A:A,">="&G10,Sales_Data!A:A,"<"&EDATE(G10,1))


Note: The weekly summary uses Monday as the start of each week. The monthly summary uses calendar months.
Data Validation and Usability
- Quantity (D2:D1000): number greater than 0; invalid input is rejected.
- Unit Price (E2:E1000): number greater than 0; invalid input is rejected.
- Date (A2:A1000): valid date; invalid input is rejected.
- The source data header row is bold and frozen for easier navigation.
- The raw data and summary calculations are kept on separate tabs to reduce accidental changes.
Sample Results
The workbook was checked against 10 sample transactions for October 2026.
Metric	Verified result
Total sales	259,900
Total quantity sold	39
Number of transactions	10
October 2026 sales	259,900


Currency values are shown as plain numbers above; format the relevant cells as Indian Rupees (₹) in Google Sheets if desired.
How to Use
1. Add each new transaction as a new row in Sales_Data.
2. Enter the date, product, category, quantity, and unit price.
3. Copy the Total Sales formula down if it is not already filled into the new row.
4. Check the daily, weekly, and monthly totals in Summary.
5. Periodically verify the summary against the source entries, especially after changing formulas or ranges.
Interview Questions
How would you design a spreadsheet so non-technical staff can enter data safely?

Use clearly named columns, a dedicated data-entry tab, data validation, consistent date and currency formats, frozen headers, and protected formula cells. Keep a separate summary tab and provide short instructions for entering each record.

What is the risk of mixing raw data and formulas on the same tab?

Users may overwrite formulas, insert data into the wrong place, or accidentally include calculated values in the source data. Separating source entries from calculations makes the workbook easier to maintain, audit, and troubleshoot.
Tools
- Google Sheets
- Spreadsheet formulas: SUM, SUMIF, SUMIFS, COUNTA, EDATE
- Data validation
Project Files
- README.md - project overview and instructions
- Sales_Tracker_Project_Report.pdf - formatted project report
- Sales_Tracker_Project_Report.docx - editable version of the report
Google Sheets Link
Add your view-only Google Sheets link here if you want reviewers to open the workbook directly.
