# ESG-Detergent-Pipeline-PySpark
This repository contains a data pipeline developed using PySpark in Databricks to analyze the environmental impact of detergents based on sales data. The pipeline processes ESG (Environmental, Social, and Governance) data to provide insights into the environmental footprint of different detergent example products.


# Introduction

The project describes a simple ETL data pipeline from a CSV file, and randomly generated ESG data about 8 detergents and their CO2 emissions, and randomly generated sales data of the detergents in different countries.
The CSV file must first be stored as a table in the Databricks data catalog.
(Data source: https://www.kaggle.com/datasets/nelgiriyewithana/countries-of-the-world-2023)

The pipeline generates 2 results in relation to the CO2 footprint caused by detergents:
- CO2 footprint per article per country
- CO2 footprint per country relative to total CO2 footprint per country

Other results could be evaluated, such as CO2 footprint by month and year and per country and per article. But for demonstration purposes, only the 2 above use cases were evaluated.

The detergents data and sales data are related to each other in a star schema structure: detergents table (dimension table) for sales table (facts table). (https://www.databricks.com/blog/2022/05/20/five-simple-steps-for-implementing-a-star-schema-in-databricks-with-delta-lake.html)

Procedural programming was used, because it is mostly structured, reusable and logically encapsulated. Object-oriented would have made less sense, since many individual components work together and should ultimately form a larger whole.

For production usage, the following things should still be changed:
- Put basic core code in a Python repository, and package it, and only call main() in Databricks. This allows changes to be tracked and versioned. Repos can have restricted access (not everyone can simply change production code in the notebook). And code can be used in other notebooks.
- DB credentials not in code, but in secrets manager or key vault

- Data pipeline can generally be triggered (e.g. by Data Factory)
- Serverless functions can also be used

- As a follow-up measure, the DevOps lifecycle could be defined:
  - Development in VS Code, remote access to test cluster in Databricks
  - Repositories in Azure DevOps (or GitHub) for versioning the artifacts
  - Production code linked to Databricks repos
  - Notebooks triggered by Data Factory

