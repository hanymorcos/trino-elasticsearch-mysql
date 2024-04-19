# Trino Overview and Benefits

Trino, formerly known as PrestoSQL, is a powerful distributed SQL query engine designed for high-performance data processing and analytics. Here are some key highlights and benefits of Trino that upper management should be aware of:

## Key Highlights

1. **Faster Data Analytics**: Trino enables lightning-fast data analytics by allowing organizations to query vast amounts of data stored across various data sources in real-time. Its distributed architecture and in-memory processing capabilities ensure high-speed query execution, even for complex analytical queries.

2. **Unified Data Access**: Trino provides a unified SQL interface for querying data across different data sources, including traditional databases, data lakes, cloud storage, and NoSQL databases. This allows organizations to analyze data from multiple sources without the need for complex ETL processes or data movement.

3. **Scalability and Flexibility**: Trino is highly scalable and can easily scale out to handle large datasets and increasing query workloads. It supports dynamic resource allocation and can be deployed in both on-premises and cloud environments, providing flexibility to adapt to changing business requirements.

4. **Cost-Efficiency**: By leveraging Trino's ability to query data in-place, organizations can avoid costly data duplication and movement. Trino's efficient query processing reduces the need for expensive hardware infrastructure, leading to cost savings in data management and analytics operations.

5. **Real-Time Insights**: Trino enables real-time data analysis by processing queries on live, up-to-date data. This allows organizations to make data-driven decisions faster and respond quickly to changing market conditions, customer needs, and business opportunities.

6. **Ecosystem Integration**: Trino integrates seamlessly with popular data ecosystem tools and frameworks, including Apache Hadoop, Apache Spark, Apache Kafka, and more. This enables organizations to leverage their existing investments in data infrastructure and tools while benefiting from Trino's advanced querying capabilities.

7. **Enterprise-Grade Security**: Trino provides robust security features, including authentication, authorization, encryption, and audit logging, to ensure the confidentiality, integrity, and availability of data. It complies with industry-standard security protocols and regulations, making it suitable for enterprise deployments.

## Usage Examples
In this example, we setup trino in front of Elastic Search and Mysql database. 

### Docker Compose Setup

```bash
docker-compose up -d


-- Create database mydatabase in MySQL
CREATE DATABASE mydatabase;

-- Create a table test in MySQL
CREATE TABLE mydatabase.test (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(50),
    age INT
);

-- Insert sample data into the test table
INSERT INTO mydatabase.test (name, age) VALUES
('John', 30),
('Alice', 25),
('Bob', 35);

-- Trino client is included 

# Query data from MySQL in trino client 
trino> SELECT * FROM mysql.mydatabase.test;

# Query data from Elasticsearch trino client 
trino> SELECT * FROM elasticsearch.default.my_index;

# Join data from MySQL and Elasticsearch
trino> SELECT * FROM elasticsearch.default.my_index a, mysql.mydatabase.test b WHERE a.age = b.age;

