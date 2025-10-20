Automated Data Cleaning in SQL

📘 Project Overview
This project demonstrates how to automate a full data cleaning pipeline using Stored Procedures, Triggers, and Events. The goal is to simulate a real-world scenario where incoming raw data is automatically cleaned, standardized, and stored in a separate table — ensuring data quality, consistency, and automation without manual intervention.

⚙️ Technologies & Skills Used
• SQL 
• Stored Procedures 
• Events 
• Triggers 
• Data Cleaning & Transformation
• Timestamp tracking for data lineage

🧩 Project Structure
• US_HOUSEHOLD_INCOME — Source raw dataset containing U.S. household income data.
• US_HOUSEHOLD_INCOME_CLEANED — Destination table to store cleaned and standardized records.
• Stored Procedure — Main logic that copies raw data, cleans it, and records timestamps.
• Event — Automates execution of the procedure every 2 minutes.
• Trigger — Automatically calls the cleaning procedure whenever new data is inserted.

🧠 Key Concepts Implemented
Stored Procedure: Copy_and_Clean_Data()
Creates or replaces the cleaned table, copies all data from the raw table with a timestamp, removes duplicates, and standardizes column values.

⏰ Event Scheduler
Runs automatically every 30 DAYS, triggering the stored procedure:

CREATE EVENT run_data_cleaning
  ON SCHEDULE EVERY 30 DAYS
  DO CALL PRACTICE_DATABASE.PUBLIC.Copy_and_Clean_Data();

🔄 Trigger
Executes the cleaning process immediately after a new record is inserted:

CREATE TRIGGER transfer_clean_data
AFTER INSERT ON PRACTICE_DATABASE.PUBLIC.US_HOUSEHOLD_INCOME
FOR EACH ROW
BEGIN
    CALL PRACTICE_DATABASE.PUBLIC.Copy_and_Clean_Data();
END;

🧹 Data Cleaning Highlights
• Duplicate Removal — Uses ROW_NUMBER() to identify and delete duplicates by ID.
• Text Standardization — Ensures consistent capitalization and naming conventions.
• Error Correction — Fixes known typos and category mismatches.
• Timestamp Tracking — Adds a timestamp for each cleaning run for monitoring and data versioning.

🗂️ File Summary

📦 automated-data-cleaning/
 ┣ 📜 automated_cleaning.sql   
 ┣ 📄 README.md               
 ┗ 📊 sample_data.csv  

🚀 How to Run the Project
1. Create the Raw Table
2. Execute the Script
3. Verify Cleaned Data
4. Observe Automation (event + trigger)

🧭 Key Learnings
✅ How to design modular SQL automation pipelines
✅ How to implement self-maintaining data cleaning systems
✅ How to integrate Snowflake-specific features (procedures, events, triggers)
✅ Improved understanding of data quality management in real-time pipelines.


👨‍💻 Author
Nithin Ramayanam
Data Analyst | Aspiring Data Scientist
Experience: SQL, Python, Tableau, Databricks, Snowflake AWS, Azure
