# Sovereign Data Pipeline: SQL-Bash-Python Integration

## 🌐 Overview
This repository demonstrates a complete, end-to-end data engineering pipeline designed for high-performance research environments. It explores the transition from structured relational data (MySQL) to processed deliverables using a "Sovereign" local computing philosophy.

Developed as part of the **Hudson Frontier Technologies** research initiative, this pipeline serves as a benchmark for ingesting and processing large-scale datasets (such as OSHA safety records) for AI/ML training.

## 🛠️ Tech Stack
* **Database:** MySQL (Bulk Data Ingestion & Relational Mapping)
* **Automation:** Python 3.9 (Service Delivery & Scripting)
* **Orchestration:** Bash/Linux Pipes (Real-time Stream Processing)
* **Version Control:** Git (Reproducible Research Workflow)

## 🚀 Key Features & Benchmarks
* **Bulk Loading:** Utilizes `LOAD DATA INFILE` for high-speed ingestion, achieving a **0.712s** write time for core datasets—significantly outperforming standard transactional inserts.
* **Data Stream Processing:** Implements Linux piping to perform complex data analysis (e.g., frequency distribution of actor attributes) directly in the shell without memory overhead.
* **Network Serving:** Integrated Python-based HTTP service layer for delivering processed datasets to remote AI agents across a cluster.

## 📁 Project Structure
* `actors.csv`: Raw data export.
* `query_actors.py`: Python script for automated database interaction.
* `sakila-schema.sql`: Full database architecture and constraints.
* `filtered_names.txt`: Sample output of the Bash-processed stream.

## 🔧 Installation & Usage
1. Clone the repository: `git clone [Your Repo Link]`
2. Import the schema: `mysql -u root -p < sakila-schema.sql`
3. Load the data using the optimized CSV ingestion script.
4. Run the Python service: `python3 -m http.server 8081`

## 🔬 Research Context
This lab serves as a foundation for the **WIPS (Workplace Integrated Prevention System)**, enabling the ingestion of massive OSHA datasets into sovereign AI models for workplace safety prediction and real-time hazard detection.
 
**Lab:** Hudson Forge
