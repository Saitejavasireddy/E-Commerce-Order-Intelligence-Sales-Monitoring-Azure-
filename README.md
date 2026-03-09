# E-Commerce-Order-Intelligence-Sales-Monitoring-Azure-
This is an end-to-end real-time data engineering pipeline that simulates U.S. e-commerce orders, streams them through Azure, processes them in Databricks using PySpark, and visualizes the results in Power BI. It follows the classic Bronze → Silver → Gold (Medallion Architecture).
Pipeline flow:

<img width="831" height="403" alt="image" src="https://github.com/user-attachments/assets/c66ff632-ecf5-4e20-b9dd-81d1047000ee" />



Python simulator generates fake orders (order ID, state, city, product, quantity, price, timestamp) → streams to Azure Event Hub every second
Databricks (PySpark Structured Streaming) reads from Event Hub → Bronze (raw) → Silver (cleaned) → Gold (aggregated by state/product in 1-min windows)
All layers stored in Azure Blob Storage as Delta tables
Power BI connects to the Gold Delta table via Databricks SQL Endpoint and displays maps, line charts, donut charts, and a raw data table
