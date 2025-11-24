# Conditional-Data-Pipeline-Orchestration-Azure-Data-Factory-

## 📌 Project Overview
This project demonstrates how to design a **conditional ETL pipeline** in **Azure Data Factory (ADF)** to copy customer and product data from an on‑premises MySQL database into **Azure Data Lake Storage (ADLS)**.  
The pipeline is parameterized to ensure data movement only occurs when specific record count thresholds are met, optimizing efficiency and reducing unnecessary transfers.

---

## 🎯 Objectives
- Copy **customer data** from MySQL to ADLS only if record count > 500.
- Trigger a **child pipeline** to copy product data if customer record count > 600.
- Pass parameters (customer count) seamlessly between parent and child pipelines.
- Ensure secure on‑premises to cloud transfer using **Self‑Hosted Integration Runtime (IR)**.

---

## 🛠️ Tech Stack
- **Azure Data Factory (ADF)**  
- **Azure Data Lake Storage Gen2 (ADLS)**  
- **MySQL Database**  
- **Self‑Hosted Integration Runtime (IR)**  
- **Pipeline Activities:** Lookup, Set Variable, IF Condition, Copy, Execute Pipeline  

---

## ⚙️ Implementation Steps
1. **Setup Self‑Hosted Integration Runtime**  
   - Configured secure connectivity between on‑prem MySQL and ADF.

2. **Create Linked Services & Datasets**  
   - Linked MySQL and ADLS as data sources/destinations.  
   - Defined datasets for customer and product tables.

3. **Parent Pipeline (CustomerTable)**  
   - Lookup activity to count rows in `customers` table.  
   - Set Variable activity to store row count.  
   - IF Condition activity to check if count > 500.  
   - Copy Activity to move data into ADLS (CSV format).  
   - Execute Pipeline activity to trigger child pipeline with parameter `customerCount`.

4. **Child Pipeline (ProductTable)**  
   - Parameterized to accept `customerCount`.  
   - IF Condition activity to check if count > 600.  
   - Copy Activity to move product data into ADLS.

---

## 📊 Architecture Diagram
MySQL (On-Prem) → Self-Hosted IR → Azure Data Factory → Conditional Logic → ADLS (CSV Files)


---

## ✅ Key Features
- **Conditional Orchestration:** Data copied only when thresholds are met.  
- **Parameter Passing:** Customer count dynamically passed to child pipeline.  
- **Secure Transfer:** Self‑Hosted IR ensures safe on‑prem to cloud connectivity.  
- **Optimized Workflow:** Reduced unnecessary data movement, improving efficiency.  

---

## 📂 Output
- Customer data stored in ADLS as CSV when record count > 500.  
- Product data stored in ADLS as CSV when customer count > 600.  

---

## 🚀 How to Run
1. Deploy pipelines in **Azure Data Factory**.  
2. Configure **Self‑Hosted IR** with MySQL credentials.  
3. Validate and publish pipelines.  
4. Trigger the **CustomerTable pipeline**; it will conditionally execute the **ProductTable pipeline**.  

---

## 📌 Resume-Ready Highlight
> *Built a parameterized ETL pipeline in Azure Data Factory to copy customer data from MySQL to ADLS only when record count exceeded thresholds, passing parameters to child pipelines for product data. Configured self‑hosted Integration Runtime and implemented conditional logic with Lookup, Set Variable, and IF activities to optimize data movement and workflow efficiency.*
