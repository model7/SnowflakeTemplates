# SnowflakeScripts
- Target: Load initial and cdc data to estimate costs (storage and compute) across cloud platform and Snowflake
- Scope includes:
	- loading data from Azure Blob Storage stage to staging tables in Snowflake
	- Snowflake objects and scripts to prove stage connectivity and load staging tables for initial and cdc blob files for a single source system
- Scope does not include:
	- mechanisms to create initial or cdc blob files
	- mechanisms to load final initial + cdc (merged) target tables

Environment:
- data flow initial load: source system > Azure Blob Storage "Initial Load" container
- data flow cdc (change data capture): source system > Azure Blob Storage "CDC" container


Step 1: Create Snowflake databases, warehouse, schema, etc.
File: "1 - Create Snowflake Environment Objects"

Step 2: Create table where procedures store start/end timestamps. This is optional, but appears to give better execution time stats than TASK_HISTORY. Tasks may not be executed exactly when scheduled making it difficult to assess execution start/end for a procedure.
File: "2 - TASK_TIMESTAMP Table"

Step 3: Load initial set of data (snapshot of history) and CDC (change records captured since snapshot of history) catchup
File: "3 - Initial Load And CDC Catch Up"

Step 4: Create procedure to load cdc staging schema.
File: "4 - Create LOAD_CDC Procedure"

Step 5: Create task to execute CDC load procedure on a schedule.
File: "5 - "Create LOAD_CDC Task"


File: "Process Monitoring Queries" - used to select data from key tables/functions to monitor the data loads and related stats

File: "Snowflake_POC_Setup"
File: 
