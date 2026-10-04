# AWS 3-Tier App (LocalStack Simulation)

This repository contains a containerized 3-tier application architecture deployed as Infrastructure as Code (IaC) via Terraform, alongside a GitHub Actions CI/CD pipeline. To prevent real-world AWS billing, the entire infrastructure and pipeline are engineered to run securely against [LocalStack](https://localstack.cloud/) at zero cost.

## Architecture Overview
* **Presentation / App Tier:** A Python FastAPI backend with interactive Swagger UI documentation.
* **Database Tier:** A PostgreSQL database containerized for local development and testing.
* **Infrastructure (Terraform):** Configurations simulating a Virtual Private Cloud (VPC), Public & Private Subnets across availability zones, an Internet Gateway, NAT Gateway with an Elastic IP (EIP), Route Tables, Security Groups, and EC2 compute instances.
* **CI/CD Automation:** A GitHub Actions workflow configured to automatically validate, plan, and apply the Terraform architecture against a LocalStack container on every push to the `main` branch.

## Prerequisites
* Docker & Docker Compose
* Terraform (`>= 1.5.0`)
* Git

## Running the Application Locally

1. **Start the Application & Database:**
   Spin up the FastAPI and PostgreSQL containers in the background:
   ```bash
   docker compose up -d --build