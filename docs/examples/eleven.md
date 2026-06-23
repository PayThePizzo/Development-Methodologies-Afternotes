# Eleven

---

## Notes

Large Scale -> Microservices
Cloud 

---

## Attempt

### Notes

* IoT
  * Platforms for remote assett management and monitoring

### Assumptions

Assumptions

* All users (private, businesses, administrations) rely on the same app, while the developers use the web app for monitoring.
* The charging stations have their own App/Interface (needed for payments on site)
  * We assume that we must be connected, through the app (after auth), to the station to make payments (no on-site payments with card, just app)
* We also have a Web App for Monitoring Systems

## Schema

```mermaid
flowchart TB
    Sensors[Charging Station Sensors]

    subgraph FE[Front End Layer]
        App[Mobile App]
        StationApp[Station Interface]
        WebApp[Web App]
    end

    subgraph API[API Gateway Layer]
        LoadBal[Load Balancer]
        APIGateway[API Gateway]
    end

    subgraph Microservices[Microservices Layer]
        EnergyServ[Energy Usage Service]
        Payment[Payment Service]
        AuthServ[Authentication Service]
        CRMServ[CRM Service]
        ChargeServ[Charging Services]
    end

    subgraph CloudLayer[Cloud Layer]
        IoTCore[IoT Core]
        EnergyUsageDB[Energy Usage DB]
        Alert[Alert System]
    end

    subgraph EdgeComputing[Edge Computing]
        IoTGateway[Charging Station IoT Gateway]
        EdgeComputer[Edge Computer]
        FailAnalysis[Predictive Model\nFailure Analysis]
    end

    subgraph DataLayer[Data Layer]
        UserDB[(User Data)]
        AnayticsDB[(Analytics DB)]
    end

    subgraph Security[Security Layer]
        Enc[Encryption]
        Auth[Authentication]
    end


    App & StationApp & WebApp --> API
    LoadBal --> APIGateway
    API --> Microservices
    AuthServ --> Auth
    Microservices --> DataLayer
    EnergyUsageDB --> Alert
    EnergyUsageDB --> EnergyServ

    IoTCore --> EnergyUsageDB
    Sensors --> IoTGateway
    IoTGateway --> EdgeComputer
    EdgeComputer --> FailAnalysis
    FailAnalysis --> IoTCore
```

---

## Attempt 1 - Gemini

```mermaid
flowchart TB
    Sensors[Charging Station Sensors]

    subgraph FE[Front End Layer]
        App[Mobile App]
        StationApp[Station Interface]
        WebApp[Web App]
    end

    subgraph API[API Gateway Layer]
        LoadBal[Load Balancer]
        APIGateway[API Gateway]
    end

    subgraph Microservices[Microservices Layer]
        AuthServ[Authentication Service]
        ChargeServ[Charging Session Service]
        Payment[Payment Service]
        EnergyServ[Energy Usage Service]
        CRMServ[CRM & Contract Service]
    end

    subgraph Security[Security Layer]
        Enc[Encryption]
        Auth[Authentication / AuthZ]
    end

    subgraph EdgeComputing[Edge Computing / Station]
        IoTGateway[Charging Station IoT Gateway]
        EdgeComputer[Edge Computer]
        FailAnalysis[Predictive Model\nFailure Analysis]
    end

    subgraph CloudLayer[Cloud Layer]
        IoTCore[IoT Core]
        EnergyUsageDB[(Energy Usage DB)]
        Alert[Alert System]
    end

    subgraph DataLayer[Data Layer]
        UserDB[(User Data & Contracts)]
        AnalyticsDB[(Analytics DB)]
    end

    %% Front End to API Gateway Connections
    App & StationApp & WebApp --> LoadBal
    LoadBal --> APIGateway

    %% App to Station Interaction (Assumption: local connection for payment/session initiation)
    App -.->|Local Auth / Sync| StationApp

    %% API Gateway to Microservices
    APIGateway --> AuthServ
    APIGateway --> ChargeServ
    APIGateway --> Payment
    APIGateway --> EnergyServ
    APIGateway --> CRMServ

    %% Microservices to Security Layer
    AuthServ --> Auth
    ChargeServ & Payment & CRMServ --> Enc

    %% Microservices to Data Layers
    AuthServ & CRMServ & Payment --> UserDB
    ChargeServ --> AnalyticsDB
    EnergyUsageDB --> EnergyServ

    %% IoT & Edge Telemetry Data Flow
    Sensors --> IoTGateway
    IoTGateway --> EdgeComputer
    EdgeComputer --> FailAnalysis
    FailAnalysis --> IoTCore
    
    %% Cloud Processing & Storage
    IoTCore --> EnergyUsageDB
    IoTCore --> AnalyticsDB
    EnergyUsageDB --> Alert
    Alert -.->|System Monitoring Streams| WebApp
```

## Attempt 2 - Gemini

```mermaid
flowchart TB
    subgraph FE[Front End Layer]
        App[Mobile App\nPrivate / Business / Admin]
        StationApp[Station Interface\nOn-Site Sync]
        WebApp[Web App\nDev/Ops Monitoring]
    end

    subgraph GW[API & Gateway Layer]
        LB[Load Balancer]
        APIG[API Gateway\nRate Limiting & Routing]
    end

    subgraph MS[Microservices Layer]
        AuthServ[Auth & Token Service]
        ChargeServ[Charging Session Service]
        PayServ[Payment Service]
        EnergyServ[Energy Usage Service]
        CRMServ[CRM & Contract Service]
    end

    subgraph CacheLayer[Caching Layer]
        RedisCache[(Redis\nSession & State Cache)]
    end

    subgraph EdgeLayer[Edge Computing / Stations]
        Sensors[Station Sensors] --> IoTGe[Station IoT Gateway]
        IoTGe --> EdgeComp[Edge Computer\nPredictive Failure ML]
    end

    subgraph CloudData[Cloud Processing & Data Layer]
        IoTCore[IoT Core Hub]
        TSDB[(Time-Series DB\nEnergy Usage & Telemetry)]
        CoreDB[(Transactional DB\nUsers & Contracts)]
        Alerts[Alert System]
    end

    %% Interactions & Edge cases
    App -.->|Local App-to-Station Auth| StationApp
    App & StationApp & WebApp --> LB
    LB --> APIG

    %% Gateway Routing
    APIG --> AuthServ
    APIG --> ChargeServ
    APIG --> PayServ
    APIG --> EnergyServ
    APIG --> CRMServ

    %% Cache and Fast In-Memory State Paths
    AuthServ & ChargeServ <--> RedisCache

    %% Storage Mapping
    AuthServ & CRMServ & PayServ --> CoreDB
    EnergyServ --> TSDB

    %% IoT Telemetry Stream Loop
    EdgeComp -->|MQTT/Telemetry Streams| IoTCore
    IoTCore --> TSDB
    TSDB --> Alerts
    Alerts -.->|Real-time Status Feeds| WebApp
```

Perfect, missing
* Kafka for async communication (monitoring)
* Security layer (encryption, authentication)