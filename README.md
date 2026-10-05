# Azure Retail Data Integration Platform using Azure Data Factory

> **Project Status:** 🟡 In Progress

## 📌 Project Overview

This project demonstrates the design and implementation of a cloud-based retail data integration platform using **Azure Data Factory (ADF)** and **Azure Data Lake Storage Gen2 (ADLS Gen2)**.

The objective is to build a scalable, reusable, parameterized, and secure data ingestion framework that can ingest retail data from multiple sources into a centralized Azure Data Lake.

The project uses a retail business scenario with datasets such as:

- Customers
- Products
- Stores
- Orders

Azure Data Factory is used for **data ingestion and orchestration**, while ADLS Gen2 is used as the centralized cloud storage layer.

---

## 🎯 Project Objectives

The main objectives are:

- Build an end-to-end Azure data ingestion pipeline.
- Store source data in Azure Data Lake Storage Gen2.
- Implement parameterized and reusable ADF pipelines.
- Implement metadata-driven ingestion.
- Demonstrate dynamic file processing.
- Implement incremental data loading.
- Implement secure access using Managed Identity and RBAC.
- Implement pipeline monitoring and error handling.
- Integrate Azure Data Factory with GitHub.
- Create a foundation for downstream Databricks, Power BI, and AI projects.

---

## 🏗️ Architecture

```text
                   SOURCE SYSTEMS
                         |
                  CSV / Database
                         |
                         v
              +---------------------+
              | Azure Data Factory  |
              |                     |
              | Copy Activity       |
              | Lookup              |
              | Get Metadata        |
              | ForEach             |
              | Parameters          |
              | Variables           |
              | Triggers            |
              +----------+----------+
                         |
                         v
              +---------------------+
              |     ADLS Gen2       |
              |                     |
              |  Raw                |
              |  Processed          |
              |  Archive             |
              +----------+----------+
                         |
                         v
                Downstream Projects
                         |
             +-----------+-----------+
             |                       |
         Databricks               Power BI
             |
        Lakehouse / Delta
```

---

## 🛠️ Technologies Used

| Technology | Purpose |
|---|---|
| Azure Data Factory | Data ingestion and orchestration |
| Azure Data Lake Storage Gen2 | Centralized data storage |
| Azure RBAC | Access control |
| Managed Identity | Secure authentication |
| Azure SQL / SQL Server | Optional source and watermark store |
| GitHub | Version control |
| CSV | Initial source data |

---

## 📂 Source Data

The initial project uses the following datasets:

### Customers

```text
customer_id
customer_name
city
state
```

### Products

```text
product_id
product_name
category
price
```

### Stores

```text
store_id
store_name
city
state
```

### Orders

```text
order_id
customer_id
product_id
store_id
order_date
quantity
```

---

## 🗄️ ADLS Gen2 Structure

```text
retail-data/
│
├── raw/
│   ├── customers/
│   ├── products/
│   ├── stores/
│   └── orders/
│
├── processed/
│   ├── customers/
│   ├── products/
│   ├── stores/
│   └── orders/
│
├── archive/
│
└── config/
```

---

## 🔄 Data Pipeline

The initial pipeline will follow this pattern:

```text
Source Files
     |
     v
Get Metadata
     |
     v
ForEach
     |
     v
Check File
     |
     v
Copy Activity
     |
     v
ADLS Gen2
```

The pipeline will be designed to dynamically process multiple files rather than creating a separate pipeline for every file.

---

## ⚙️ ADF Concepts Demonstrated

This project will demonstrate:

- Linked Services
- Datasets
- Copy Activity
- Get Metadata Activity
- Lookup Activity
- ForEach Activity
- If Condition
- Parameters
- Variables
- Dynamic Expressions
- Metadata-driven pipelines
- Incremental loading
- Schedule triggers
- Error handling
- Monitoring
- Managed Identity
- Azure RBAC
- Git integration

---

## 🔁 Incremental Loading

The project will demonstrate incremental ingestion so that the pipeline does not unnecessarily process the complete dataset during every execution.

For database-based sources, a watermark approach will be demonstrated.

```text
Watermark
    |
    v
Identify New/Changed Data
    |
    v
ADF Copy Activity
    |
    v
ADLS
    |
    v
Update Watermark
```

For file-based sources, newly arriving files will be identified and processed dynamically.

---

## 🔐 Security

The project will use Azure security best practices.

Instead of storing storage account keys directly in the pipeline:

```text
Azure Data Factory
        |
        | Managed Identity
        v
Azure RBAC
        |
        v
ADLS Gen2
```

The ADF managed identity will be granted the required permissions on the storage account.

---

## 📊 Monitoring

ADF monitoring capabilities will be used to track:

- Pipeline execution
- Activity execution
- Success and failure
- Execution duration
- Trigger execution
- Error messages

Screenshots of successful and failed executions will be added to the repository.

---

## 🔀 GitHub Version Control

The project will use GitHub for version control.

Development workflow:

```text
Feature Branch
      |
      v
Development
      |
      v
Commit
      |
      v
Pull Request
      |
      v
Review
      |
      v
Merge
```

Example branch:

```text
feature/metadata-driven-ingestion
```

---

## 📁 Repository Structure

```text
azure-adf-retail-data-integration/
│
├── README.md
│
├── architecture/
│   ├── architecture.png
│   └── data-flow.png
│
├── data/
│   └── sample-data/
│       ├── customers.csv
│       ├── products.csv
│       ├── stores.csv
│       └── orders.csv
│
├── adf/
│   ├── pipelines/
│   ├── datasets/
│   ├── linked-services/
│   └── triggers/
│
├── sql/
│   └── watermark.sql
│
├── documentation/
│   ├── design.md
│   ├── implementation.md
│   └── incremental-load.md
│
└── screenshots/
```

---

## 🚀 Implementation Roadmap

### Phase 1 — Azure Setup

- [ ] Create Resource Group
- [ ] Create ADLS Gen2 Storage Account
- [ ] Create containers
- [ ] Upload sample data
- [ ] Create Azure Data Factory

### Phase 2 — ADF Configuration

- [ ] Create Linked Service
- [ ] Configure Managed Identity
- [ ] Configure RBAC
- [ ] Create datasets
- [ ] Create parameterized datasets

### Phase 3 — Pipeline Development

- [ ] Create Copy Activity
- [ ] Create Get Metadata Activity
- [ ] Create ForEach Activity
- [ ] Implement dynamic file processing
- [ ] Implement metadata-driven ingestion

### Phase 4 — Incremental Loading

- [ ] Design watermark mechanism
- [ ] Create watermark table
- [ ] Implement incremental processing
- [ ] Update watermark after successful execution

### Phase 5 — Production Features

- [ ] Add error handling
- [ ] Add triggers
- [ ] Configure monitoring
- [ ] Test failure scenarios

### Phase 6 — GitHub

- [ ] Commit ADF artifacts
- [ ] Create feature branches
- [ ] Create Pull Request
- [ ] Merge changes
- [ ] Complete documentation

---

## 📈 Expected Outcome

At the end of the project, the solution will provide a reusable Azure data ingestion framework capable of loading multiple retail datasets into ADLS Gen2 using Azure Data Factory.

The project will also provide the data foundation for the next stages of the portfolio:

```text
Project 1
ADF + ADLS
      |
      v
Project 2
Databricks + Delta Lake
      |
      v
Project 3
Power BI
      |
      v
Project 4
AI / LLM
```

---

## 🎓 Key Learning Outcomes

This project is designed to demonstrate practical understanding of:

**Azure Data Factory → Data Integration → ADLS → Incremental Processing → Security → Monitoring → Git**

The emphasis is on understanding the architecture and implementation rather than simply creating individual Azure resources.

---

## 👨‍💻 Author

**Godugu Mahender**

20+ Years of IT Experience  
Database Development | Data Engineering | BI | Azure | Databricks | AI

---

## 📌 Project Status

**Current Status:** 🟡 Design / Initial Development

The implementation and documentation will be updated progressively as each component is completed.
