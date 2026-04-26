Sovereign Data Pipeline: SQL-Bash-Python Integration
🌐 Overview
This repository demonstrates a high-performance, multi-layered data engineering pipeline designed for sovereign research environments. It bridges the gap between structured relational storage (MySQL), stream-based CLI processing (Bash), and networked service delivery (Python).

Developed by Hudson Frontier Technologies, this architecture serves as the foundation for ingesting and processing large-scale datasets—such as OSHA safety records—to support the WIPS (Workplace Integrated Prevention System) project.

🛠️ Tech Stack
Database: MySQL (Bulk Data Ingestion & Relational Mapping)

Automation: Python 3.9 (Service Delivery & Logic)

Orchestration: Bash/Linux Pipes (Real-time Stream Processing)

Version Control: Git (Reproducible Research Workflow)

🚀 Key Features & Benchmarks
Optimized Ingestion: Utilizes LOAD DATA INFILE to achieve a 0.712s write time for core datasets, bypassing the overhead of standard transactional inserts.

Stream Processing: Implements Linux piping for real-time analysis, enabling complex data filtering without high RAM consumption.

Service Layer: Integrated Python-based HTTP server for delivering data fragments to remote AI research nodes.

📁 Project Structure
actors.csv: The raw source data.

query_actors.py: Python script for automated database retrieval.

sakila-schema.sql: The structural blueprint for the database.

filtered_names.txt: Sample output of the processed Bash stream.

📖 Step-by-Step Execution Guide
To reproduce this environment and verify the data integrity, follow these steps:

1. Database Initialization
Log into your MySQL instance and establish the relational schema:

Bash
mysql -u root -p -e "CREATE DATABASE IF NOT EXISTS sakila;"
mysql -u root -p sakila < sakila-schema.sql
2. Optimized Data Ingestion
Perform a bulk load of the raw CSV. Note: We use TRUNCATE first to ensure a clean slate and avoid Primary Key conflicts.

Bash
# Clear the target table
mysql -u root -p sakila -e "TRUNCATE TABLE actors_copy;"

# Execute timed bulk import
time mysql -u root -p sakila -e "LOAD DATA INFILE '$(pwd)/actors.csv' 
INTO TABLE actors_copy 
FIELDS TERMINATED BY ',' 
ENCLOSED BY '\"' 
LINES TERMINATED BY '\n';"
3. Stream Analysis (Bash Pipeline)
Filter and rank the top 5 most frequent attributes directly from the database output:

Bash
mysql -u root -p sakila -e "SELECT last_name FROM actor" | sort | uniq -c | sort -nr | head -n 5
4. Deploying the Service Layer
Activate the local HTTP server to share research files across the network:

Bash
python3 -m http.server 8081
Verify with curl: curl http://localhost:8081/query_actors.py

🔬 Research Context (WIPS Project)
This pipeline is a modular component of the Workplace Integrated Prevention System. By standardizing how we ingest and serve data, we allow the Hudson Forge multi-agent council to query live safety regulations and incident reports without manual intervention.

🗺️ Roadmap
[x] Standardize Sakila pipeline (Complete)

[ ] Ingest OSHA Incident Datasets for WIPS Project

[ ] Integrate pipeline with Hudson Forge Multi-Node Cluster

[ ] Deploy RAG-based AI agents to query safety protocols

Independent Builder: Billy Ray Davis Jr.

Organization: Hudson Frontier Technologies LLC

License: MIT
