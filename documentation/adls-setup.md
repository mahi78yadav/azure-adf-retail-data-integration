# Azure Data Lake Storage Gen2 Setup

## Objective

Create Azure Data Lake Storage Gen2 as the centralized storage layer for the retail data integration platform.

## Planned Storage Structure

The storage account will contain the following containers:

- raw
- processed
- archive
- config

## Data Structure

```text
raw/
├── customers/
├── products/
├── stores/
└── orders/

processed/
├── customers/
├── products/
├── stores/
└── orders/

archive/

config/
