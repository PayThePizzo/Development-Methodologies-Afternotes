# Netflix

Video streaming based on complex infrastructure

What are its features?

* CDN
  * Thousands of server nodes distributed globally
  * Stores cached copies of content close to end-users
  * Reduces latency and bandwidth costs
  * Handles about 95% of streaming traffic
  * Backend services
    * Load Balancer distributes traffic across services
    * API Gateway handles client requests and routing
    * Microservices contains the business logic
* Storage layer
  * Media Storage: Original and transcoded content
  * User Data: Preferences, viewing history, accounts
  * Analytics Database: Viewing patterns, performance metrics
* Media processing
  * Transcoding Service: Creates multiple quality versions of videos
  * Quality Adaptation: Manage different bitrates and resolutions
  * DRM Service: Handles content protection

What technologies are used?

* Java and Node.js for microservices
* Cassandra for distributed databases
* Redis for caching
* Kafka for message queuing
* ELK Stack for logging

---

## Project Management

It uses the DevOps methodology to maintain a high level of reliability and availability of its services

See [Chaos Monkey](https://netflix.github.io/chaosmonkey/) for “failure as a service”

Test automation 

```mermaid
flowchart TB
    %% --- Client Devices ---
    subgraph CLIENTS["Client Devices"]
        STV[Smart TV]
        MOB[Mobile Device]
        WEB[Web Browser]
        CON[Gaming Console]
    end

    %% --- Content Delivery Network ---
    subgraph CDN["Content Delivery Network"]
        CDN1[CDN Edge Server 1]
        CDN2[CDN Edge Server 2]
        CDNN[CDN Edge Server n]
    end

    %% --- Backend Services (Outer Main Subgraph) ---
    subgraph BACKEND["Backend Services"]
        LB[Load Balancer]
        API[API Gateway]

        %% --- Microservices ---
        subgraph MICROSERVICES["Microservices"]
            AUTH[Authentication Service]
            CONT[Content Service]
            REC[Recommendation Engine]
            PROF[User Profile Service]
            ANALYTICS[Analytics Service]
        end

        %% --- Storage Layer ---
        subgraph STORAGE["Storage Layer"]
            MEDIA_DB[("Media Storage")]
            USER_DB[("User Data")]
            ANALYTICS_DB[("Analytics DB")]
        end

        %% --- Media Processing ---
        subgraph PROCESSING["Media Processing"]
            TRANS[Transcoding Service]
            QUAL[Quality Adaptation]
            DRM[DRM Service]
        end
    end

    %% --- Connections ---
    STV & MOB & WEB & CON --> CDN
    CDN --> LB
    LB --> API
    API --> MICROSERVICES
    MICROSERVICES --> STORAGE
    STORAGE --> PROCESSING
    
    %% Curved arrow going back from Media Processing to Media Storage
    PROCESSING --> MEDIA_DB
```
