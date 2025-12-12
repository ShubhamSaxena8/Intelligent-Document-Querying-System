# Intelligent Document Querying System

Generative AI RAG application using Amazon Bedrock, Aurora Postgres Serverless, and Amazon S3 to turn a document corpus into a chat-based knowledge system.

## Overview

This project demonstrates how to build an end-to-end generative AI application on AWS. It ingests documents, stores and indexes them for retrieval, and uses Bedrock-hosted LLMs to answer natural language questions over that content.

## What This Project Does

- Provisions AWS resources with Terraform (Bedrock access, Aurora Postgres Serverless, S3).
- Ingests and stores documents in S3 and structured data in Aurora Postgres.
- Builds a retrieval pipeline so Bedrock can ground responses in relevant document context (RAG pattern).
- Exposes a chat-style interface where users can query the document base in natural language.
- Applies security measures around access, data storage, and GenAI interactions.

## Tech Stack

- Amazon Bedrock  
- Amazon Aurora Postgres Serverless  
- Amazon S3  
- Terraform (IaC)  
- Python + SQL  

## Outcome

A working intelligent document querying system that showcases how to combine Bedrock LLMs with AWS data services to deliver secure, retrieval-augmented answers over organizational documents.

## Project Overview

This project consists of several components:

1. Stack 1 - Terraform configuration for creating:
   - A VPC
   - An Aurora Serverless PostgreSQL cluster
   - s3 Bucket to hold documents
   - Necessary IAM roles and policies

2. Stack 2 - Terraform configuration for creating:
   - A Bedrock Knowledge Base
   - Necessary IAM roles and policies

3. A set of SQL queries to prepare the Postgres database for vector storage
4. A Python script for uploading files to an s3 bucket

The goal is to create a Bedrock Knowledge Base that can leverage data stored in an Aurora Serverless database, with the ability to easily upload supporting documents to S3. This will allow us to ask the LLM for information from the documentation.

## Project Structure

```
project-root/
│
├── stack1
|   ├── main.tf
|   ├── outputs.tf
|   └── variables.tf
|
├── stack2
|   ├── main.tf
|   ├── outputs.tf
|   └── variables.tf
|
├── modules/
│   ├── aurora_serverless/
│   │   ├── main.tf
│   │   ├── variables.tf
│   │   └── outputs.tf
│   └── bedrock_kb/
│       ├── main.tf
│       ├── variables.tf
│       └── outputs.tf
│
├── scripts/
│   ├── aurora_sql.sql
│   └── upload_to_s3.py
│
├── spec-sheets/
│   └── machine_files.pdf
│
└── README.md
```
