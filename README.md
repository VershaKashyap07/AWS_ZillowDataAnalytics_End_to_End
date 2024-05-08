
---

### Overview:
This project demonstrates an end-to-end pipeline on AWS for processing data from the Zillow API. The pipeline involves storing raw JSON data in Amazon S3, transforming it into CSV format, loading it into Amazon Redshift, and visualizing it using Amazon QuickSight. The workflow is orchestrated using Apache Airflow.

### Services Used:
1. **Zillow API:** Used to fetch real estate data.
2. **Amazon S3:** Used for storing raw JSON data and intermediate CSV files.
3. **AWS Lambda:** Used to trigger copy operations between S3 buckets.
4. **Amazon Redshift:** Used as the data warehouse for storing and querying processed data.
5. **Apache Airflow:** Used for orchestrating the data pipeline.
6. **Amazon QuickSight:** Used for data visualization.

### Pipeline Steps:
1. **Data Ingestion:**
   - Raw JSON data from the Zillow API is fetched and stored in an S3 bucket.

2. **Data Transformation:**
   - A Lambda function is triggered to transform the raw JSON data into CSV format.
   - The transformed CSV files are stored in another S3 bucket.

3. **Data Loading:**
   - Another Lambda function is triggered to copy the CSV files from the intermediate S3 bucket to a final storage location.
   - A sensor checks for the availability of the CSV files in the final storage location.

4. **Data Warehousing:**
   - Once the CSV files are available, the data is loaded into Amazon Redshift.
   - Tables are created in Redshift to match the schema of the CSV files.

5. **Data Visualization:**
   - Finally, data stored in Amazon Redshift is visualized using Amazon QuickSight for insights and analysis.

### Project Structure:
- **Airflow DAGs:** Contains the Airflow Directed Acyclic Graph (DAG) definitions for orchestrating the pipeline.
- **Lambda Functions:** Contains the code for the AWS Lambda functions used in the pipeline.
- **Redshift SQL Scripts:** Contains SQL scripts for creating tables and loading data into Amazon Redshift.
- **README.md:** This file, providing an overview of the project, its services, and pipeline steps.

### Instructions for Deployment:
1. **Setup AWS Services:**
   - Configure AWS credentials and permissions.
   - Create S3 buckets for storing raw and processed data.
   - Set up Amazon Redshift cluster and configure security groups.

2. **Configure Airflow:**
   - Install Apache Airflow and set up the environment.
   - Define Airflow DAGs for each pipeline step, including task dependencies.

3. **Implement Lambda Functions:**
   - Develop Lambda functions for transforming and copying data between S3 buckets.

4. **Create Redshift Tables:**
   - Write SQL scripts to create tables in Amazon Redshift matching the schema of CSV files.

5. **Run the Pipeline:**
   - Trigger the Airflow DAGs to execute the pipeline.
   - Monitor the progress and troubleshoot any issues.

6. **Visualize Data:**
   - Access Amazon QuickSight to visualize and analyze the processed data stored in Amazon Redshift.

### Conclusion:
This project showcases a robust and scalable data pipeline architecture on AWS, demonstrating the integration of various AWS services for data ingestion, transformation, storage, warehousing, and visualization. By following the instructions provided, users can deploy and customize the pipeline to suit their specific data processing requirements.

---