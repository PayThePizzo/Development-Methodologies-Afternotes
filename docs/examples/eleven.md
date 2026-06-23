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
    Sensors[Station Sensors]

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
        AlertMonitorServ[Alert & Monitor Service]
    end

    subgraph CacheLayer[Caching Layer]
        RedisCache[(Redis\nSession & State Cache)]
    end

    subgraph EdgeLayer[Edge Computing / Stations]
        IoTGe[Station IoT Gateway]
        IoTGe --> EdgeComp[Edge Computer]
        EdgeComp --> PredFail[Predictive Failure ML]
    end

    subgraph CloudData[Cloud Processing & Data Layer]
        IoTCore[IoT Core Hub]
        TSDB[(Time-Series DB\nEnergy Usage & Telemetry)]
        CoreDB[(Transactional DB\nUsers & Contracts)]
        
        Alerts[Alert System]
    end

    subgraph AsyncMessage[Async Message Layer]
        Kafka[[Kafka Event Bus\nTelemetry & App Events]]
    end

    %% Sensors
    Sensors --> IoTGe


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
    APIG --> AlertMonitorServ

    %% Cache and Fast In-Memory State Paths
    AuthServ & ChargeServ <--> RedisCache

    %% Storage Mapping
    AuthServ & CRMServ & PayServ --> CoreDB
    EnergyServ --> TSDB
    ChargeServ --> TSDB

    %% IoT Telemetry Stream Loop
    PredFail -->|MQTT/Telemetry Streams| IoTCore
    IoTCore --> TSDB
    TSDB --> Alerts
    Alerts --> Kafka --> AlertMonitorServ
```

Perfect, missing
* Sensors must be outside Edge Computing, in a dedicated module for stations
* Decouple Edge Computing and Predictive Model Failure ML Pipeline
* Alert System becomes Alert and Monitoring System. Then, connect it to a Kafka Communication Module. Connect this module to a NEW Monitor Service in Microservice
* Add separate Data Layer (for Transactions and User Info) or Assume Full-Cloud Solution and rename layer to Cloud and Data Layer
* Assume charging sessions data goes to time series db
* Security layer (encryption, authentication)