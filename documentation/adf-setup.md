
# Azure Data Factory Implementation

## Data Factory

**Name:** adf-retail-data-dev-1

## Authentication

Azure Data Factory uses a System-Assigned Managed Identity.

The managed identity was granted:

**Storage Blob Data Contributor**

on the ADLS Gen2 storage account.

## Linked Service

**Name:** LS_ADLS_Retail

**Connector:** Azure Data Lake Storage Gen2

**Authentication:** System-Assigned Managed Identity

**Integration Runtime:** AutoResolveIntegrationRuntime

## Source Dataset

**Name:** DS_Source_Customers

Source:

```text
raw/customers/customers.csv