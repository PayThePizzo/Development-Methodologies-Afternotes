# Fortnite

The delay before data begins to transfer after a request is
made. Minimizing latency is critical for real-time
applications like gaming or video streaming.

Example: In online gaming, high latency causes lag,
disrupting the user experience. Techniques to reduce
latency include reducing network hops and optimizing
backend processing times.

Fortnite’s Architecture:
– Microservices-Based Backend:
• Uses Kubernetes to scale services such as matchmaking and account management.
– SaaS Integration:
• OAuth2 support for logins with Google, PlayStation Network, and Xbox Live accounts.
• SaaS payment systems to handle microtransactions.
– Cross-Platform Play:
• Players on consoles, PCs, and mobile devices can play together.
• Cloud synchronization for progress and purchases.

Results:
– Millions of simultaneous players.
– Service continuity even during global updates, thanks to distributed systems.
– Effective monetization with personalized in-game purchases.

Concurrent Users (peak): 15.3M+ (during
special events).
Concurrent Users (daily average): Millions of
wolrdwide players.
Monthly Active Users (MAU): 350M registered
users.

Client-server calls per second:
– Matchmaking and authentication: 100.000+ of
requests per second during peak
– WebSocket and Real-Time updates: 30.000+
messages per second per game server.

Latency: 20-50ms for most players using
regionally distributed servers.

Game severs in operation: 1000+ of server
instance on cloud providers.
– Each server suppors 100-200 players per match
DB queries for player profiles: 2M+ of queries
per day.
Logged Events: 2TB+/daily for every player.
CDN: handling 2PB+ of monthly traffic.
Cost per player: about $0.01 per player per day
on cloud infrastructure, depending on global
demand

--- 

## Fortnite - Gemini 1

```mermaid
graph TB
    subgraph Clients ["Cross-Platform Client Layer"]
        PC[PC Clients]
        Console[Console Clients <br/> PSN / Xbox / Switch]
        Mobile[Mobile Devices]
    end

    subgraph Edge ["Global Edge & Delivery Layer (Latency Minimization)"]
        CDN[Global CDN <br/> Handles 2PB+ Monthly Traffic]
        Anycast[Anycast DNS / Edge Routing <br/> Targets 20-50ms Latency]
    end

    subgraph Compute_Regional ["Regional Game Server Fleet (1000+ Instances)"]
        DGS[Dedicated Game Servers <br/> 100-200 Players per Match Loop]
        WS[WebSocket & UDP Real-Time Sync <br/> 30k+ msgs/sec per server]
    end

    subgraph K8s_Backend ["Core Microservices Fleet (Kubernetes Backend)"]
        Auth[Auth Service <br/> OAuth2: Google, PSN, Xbox Live]
        Matchmaker[Matchmaking Engine <br/> 100,000+ Peak RPS]
        ProfileService[Cloud Sync & Progress Service]
        Monetization[SaaS Payment Gateway <br/> Microtransactions]
    end

    subgraph Storage_Data ["Data, Analytics & Persistent Storage Layer"]
        Cache[(In-Memory Cache Cluster <br/> Absorbs Profile Reads)]
        DB[(Global Player Profile DB <br/> 2M+ Queries/Day)]
        Kafka[High-Throughput Log Pipeline]
        DataLake[(Analytics Data Lake <br/> Stores 2TB+ Daily Logs)]
    end

    %% Client Interactions
    Clients -->|Download Game Patches & Assets| CDN
    Clients -->|Low-Latency Game Traffic| Anycast
    Anycast -->|Routes to Nearest Node| WS
    WS <-->|High-Frequency State Sync| DGS

    %% Control Plane & Orchestration
    Clients -->|Authentication Requests| Auth
    Clients -->|Queue for Match| Matchmaker
    Clients -->|In-Game Store Purchases| Monetization

    %% Backend Systems Connections
    Matchmaker -->|Spawns / Allocates Session| DGS
    Monetization -->|Updates Entitlements| ProfileService
    ProfileService --> Cache
    Cache <--> DB

    %% Telemetry & Log Flow
    DGS -.->|Asynchronous Telemetry| Kafka
    K8s_Backend -.->|Audit & Event Logs| Kafka
    Kafka -->|Batch Writes| DataLake

    classDef clientStyle fill:#fafafa,stroke:#666,stroke-width:2px;
    classDef edgeStyle fill:#e8f5e9,stroke:#2e7d32,stroke-width:2px;
    classDef regionalStyle fill:#fff3e0,stroke:#e65100,stroke-width:2px;
    classDef k8sStyle fill:#e1f5fe,stroke:#0288d1,stroke-width:2px;
    classDef dataStyle fill:#f3e5f5,stroke:#7b1fa2,stroke-width:2px;

    class Clients,PC,Console,Mobile clientStyle;
    class Edge,CDN,Anycast edgeStyle;
    class Compute_Regional,DGS,WS regionalStyle;
    class K8s_Backend,Auth,Matchmaker,ProfileService,Monetization k8sStyle;
    class Storage_Data,Cache,DB,Kafka,DataLake dataStyle;
```

---

## Fortnite - Gemini 2

If the case study were adapted for Fortnite using the architectural specifications and metrics detailed in lecture-11-devmet-services-integration-part-4.pdf, the system must pivot from an IoT sensor polling model to a massively scaled, ultra-low-latency game backend capable of handling millions of concurrent connections.

Based explicitly on the engineering realities outlined in your slides (e.g., 30,000+ WebSocket messages per second, 2TB+ of daily log data, and multi-platform SaaS authentication), here is how that high-level Mermaid diagram evolves to pass an architectural exam.

```mermaid
flowchart TB
    subgraph Clients[Client Layer & Static Delivery]
        PC[PC Client]
        Console[Console Client\nPlayStation / Xbox / Switch]
        Mobile[Mobile Client]
        CDN[Global Content Delivery Network\n2PB+ Monthly Textures & Patches]
    end

    subgraph Edge[Edge & API Routing Layer]
        LB[Load Balancer]
        APIG[API Gateway\nEdge Validation & Token Routing]
        SaaSAuth[[SaaS Identity Providers\nOAuth2: Google / PSN Live / Xbox]]
    end

    subgraph K8s[Compute Layer - Kubernetes Cluster]
        AuthServ[Auth & Session Service]
        MatchServ[AWS GameLift / Matchmaking]
        ProfileServ[Player Profile & Inventory]
        GameState[Authoritative Game State Service]
        PayServ[SaaS Payment Service\nMicrotransactions]
        LogServ[Ingestion & Analytics Service]
    end

    subgraph Broker[Asynchronous Messaging Bus]
        Kafka[[Kafka Event Bus\nHigh-Throughput Telemetry Pipeline]]
    end

    subgraph Storage[Distributed Storage Layer]
        Redis[(Redis\nIn-Memory Transient State Cache)]
        NoSQL[(NoSQL DB\nPlayer Profiles & Inventories)]
        GlobalSQL[(Distributed SQL\nRelational Financial Ledger)]
    end

    %% Asset Delivery Path
    CDN -.->|Static Asset Ingestion| PC & Console & Mobile

    %% Client Communication Channels
    PC & Console & Mobile -->|Real-Time WebSockets\n30k+ msgs/sec per instance| GameState
    PC & Console & Mobile -->|HTTPS REST API Calls| LB
    LB --> APIG

    %% Identity & Gateway Integrations
    APIG <-->|Federated OAuth2 Handshake| SaaSAuth
    APIG --> AuthServ
    APIG --> MatchServ
    APIG --> ProfileServ
    APIG --> PayServ

    %% Inter-Service Operations & State Tracking
    MatchServ -->|gRPC: Provision Session| GameState
    GameState <--> Redis
    ProfileServ --> NoSQL
    PayServ --> GlobalSQL

    %% 2TB+ Telemetry & Logging Stream
    GameState & ProfileServ & PayServ -->|Emit Game Events| Kafka
    Kafka --> LogServ
```

### Component Matrix & Architectural Justifications

* **Cross-Platform Asset Delivery Layer:** Unlike charging stations, games depend heavily on multi-gigabyte client-side rendering engine downloads. A global **CDN layer** handling over 2PB of monthly traffic offloads heavy binary transfers entirely from the core microservices.
* **Federated Edge Authentication:** To support cross-platform progression across PC, console, and mobile clients seamlessly, the **API Gateway** integrates directly with external **SaaS identity solutions** (Google, PSN, Xbox Live) via OAuth2.
* **Dual-Protocol Splitting:**
* **Synchronous REST APIs:** Used for non-time-critical requests (store browsing, reading player inventories, account settings).
* **Persistent WebSockets/UDP Pipelines:** Bypasses standard routing algorithms entirely to sync game state data directly with an authoritative server at a strict 20–50ms latency margin.


* **In-Memory Architecture Shifting:** Instead of utilizing traditional SQL databases for dynamic data, an intensive multi-player backend maps core state components strictly into an **In-Memory Cluster (Redis)** to handle thousands of operations per second without write locking.
* **The 2TB+ Event Pipe (Kafka):** Telemetry flows continuously from running match instances. Direct database storage would instantly trigger bottlenecks; instead, events push straight into **Kafka** before batch-processing routines securely move archival data onto analytics warehouses.