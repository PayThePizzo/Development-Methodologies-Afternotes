# Development-Methodologies-Afternotes

Resources

- [ ] Business Models
  - [ ] B2B
- [ ] Software Architecture
  - [ ] Monolithic
  - [ ] Microservices
  - [ ] Layered
  - [ ] Event-Driven
  - [ ] Middleware
- [ ] Business Tools
  - [ ] Enterprise resource planning (ERP)
  - [ ] Customer relationship management (CRM)
  - [ ] Supply chain management (SCM)
  - [ ] ETL (Extract, Transform, Load)
- [ ] Testing
  - [ ] Maven (Java)
  - [ ] JUnit (Java, Unit Testing)
  - [ ] React Testing Library (Js)
  - [ ] JEST (Js)
  - [ ] Cypress + Cucumber (Automation, E2E Testing)
  - [ ] BrowserStack (Front End Testing)
  - [ ] Applitools (Front End Testing)
  - [ ] SauceLabs (Front End Testing)
- [ ] Monitoring
  - [ ] Sentry.io 
  - [ ] Splunk
  - [ ] Observer
- [ ] Quality Assurance (QA)
- [ ] Version Control
  - [ ] Git
  - [ ] Github Actions
- [ ] Code Quality
  - [ ] Pre-Commit Hooks
- [ ] System Administration
- [ ] API
  - [ ] AWS API
  - [ ] Kong
  - [ ] NGINX
- [ ] Communication (Networks)
  - [ ] WebSocket Protocol
  - [ ] gRPC
- [ ] Security (Cybersecurity)
  - [ ] OAuth2 
- [ ] Data Management
- [ ] Big Data
  - [ ] Apache Kafka for real-time streaming
  - [ ] Spark for batch processing.
- [ ] Orchestration
  - [ ] Apache AirFlow for workflow automation
- [ ] AI
- [ ] Block Chain
- [ ] IoT
  - [ ] Azure IoT Hub
  - [ ] AWS IoT Core
- [ ] Cloud
  - [ ] AWS
  - [ ] Azure
- [ ] Containers
  - [ ] Kubernetes (Cloud, Multi Host)
  - [ ] Docker (Single Host)
- [ ] Project Management
  - [ ] Waterfall
  - [ ] Lean
  - [ ] Agile
  - [ ] Scrum
  - [ ] Kanban
  - [ ] Extreme Programming
  - [ ] DevOps
- [ ] Front End
- [ ] Continuous Integration
  - [ ] Github Actions 
  - [ ] Jenkins
  - [ ] GitLab CI
  - [ ] CircleCI
- [ ] Data Sources
  - [ ] Databases
    - [ ] Cassandra (Distributed)
    - [ ] NoSQL (Scalable data)
    - [ ] SQL (For relational data)
    - [ ] Redis (in memory)
    - [ ] AWS S3 (Raw Data)
    - [ ] Google BigQuery for analytics-ready dataset
- [ ] Data Integration Tools (Data Governance)
  - [ ] MuleSoft
  - [ ] Talend
  - [ ] Apache NiFi
- [ ] Versioning
  - [ ] Apache Avro
  - [ ] JSON Schema
- [ ] Schema Registries
  - [ ] Apache Avro
  - [ ] Apache Kafka Schema Registry
  - [ ] Protocol Buffers
- [ ] Data Migration
  - [ ] Apache NiFi
  - [ ] AWS Glue ( Simplifies ETL processes)
  - [ ] Azure Data Factory (Offers pipelines for data movement and transformation)
  - [ ] Google Cloud Dataflow (Real-time and batch data processing.)
- [ ] Common Data Exchange Formats
  - [ ] JSON
  - [ ] XML
  - [ ] SOAP
  - [ ] REST
- [ ] Serverless Integration
  - [ ] AWS Lambda
  - [ ] Azure Functions
  - [ ] Google Cloud Functions
- [ ] Unified Data Integration
  - [ ] Snowflake
  - [ ] Google BigQuery

Redis, Github Workflow, Terraform, Ansible, ELK Stack (Logging), Kafka (Message Queueing)

Version control
Automated testing
Continuous integration pipelines
Deployment automation
Configuration Management
Containerization (packaging application and
dependencies into containers and ensuring
consistency across development, testing and
production environments)
Orchestration (managing container deployment and
scaling, automating container lifecycle
management)
Microservices architecture






In linea generale, per la preparazione mi sono basato su un esame tipo che aveva messo su moodle che ho capito essere una soluzione molto generale e quindi applicabile a diversi scenari, ovviamente bisogna stare attenti al caso ma diciamo che solitamente con architetture a microservizi, una struttura del sistema simile a quella che mette lui (quindi con database e modello LLM, ecc ) e metodologia agile non sbagli praticamente mai perché sono delle scelte implementative largamente applicabili. Anche l'uso di un cloud e di un API gateway sono attuali e molto usati. 

Infine per prepararmi, c'ho messo relativamente poco, prestando attenzione ai dettagli che ti ho detto prima, ho preso la prova d'esame che ha caricato e ne ho fatte generare dall'AI prove molto simili per poi caricare una soluzione e avere una valutazione e possibili correzioni (è un metodo un po' così ma il prof non c'ha dato ulteriori esempi) 

To be honest, the exam is quite straightforward. The professor usually gives you a scenario, and you have to explain which development methodology would be most suitable (for example, Agile) and justify your choice. You may also be asked to discuss the security measures you would adopt in that context.

However my tip is to understand the problem and map out the architecture on a cloud infrastructure. I designed it on AWS as microservices as it was easier for me, you can design it on GCP or Azure any other service you are familiar with. Before exam practice taking problems and coming up with high level architectual solutions, most problems have the same pattern. The reamining questions are easy as they are concerened with software development, best practives, and resource allocations like team struture etc.



The technologies you can use are:

* "Seamless Communication" -> System integration "addresses these issues by enabling seamless communication and collaboration between different systems"
  * Point-to-Point Integration
    * Example: Connecting an e-commerce platform directly to a payment gateway.
  * Centralized Integration Architecture
    * Example: Using an Enterprise Service Bus (ESB) to connect CRM, ERP, and supply chain systems.

