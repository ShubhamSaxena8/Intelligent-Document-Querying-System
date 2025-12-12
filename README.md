# Intelligent-Document-Querying-System
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
