# Communication

---

## API Gateway

it’s a server that acts as an intermediary between client applications and backend services. It manages, routes and secures requests from clients to various backend services. The purpose is simplifying client-server interactions by providing a unified entry point , improving efficiency and security for handling multiple microservices.

**Key functions**

- **Request Routing:** directs client requests to the appropriate backend service, allowing microservices to communicate effectively.
    
- **Load Balancing:** distributes incoming traffic evenly across services to ensure optimal performance
    
- **Authentication and Authorization:** handles security by managing authentication and authorization, ensuring only valid clients have access.
    
- **Caching:** temporarily stores responses to reduce load on services and improve response time
    
- **Rate Limiting:** controls the number of requests clients can make, protecting against overload and abusive usage
    
- **Protocol Translation:** converts one protocol to another, enabling communication across various systems.
    

  

**Advantages of Using an API Gateway**

- **Centralized Management:** simplifies the management of common functionalities like security, logging and throttling in one location
    
- **Enhanced Security:** API Gateways handle sensitive processes (like authentication), protecting backend services from direct exposure to clients
    
- **Improved Performance:** Features like caching and load balancing increase application efficiency, particularly with high traffic
    
- **Simplified Client Development:** Provides a unified API, simplifying client interactions and reducing complexity.
    

  

**API Gateway Patterns in Microservices**

- **Backend for Frontend:** Taylors API Gateway responses to different client types, improving user experience
    
- **Edge Gateway:** positioned at the network boundary to handle initial requests, providing an initial layer of security and validation
    
- **Service Mesh Integration:** in a microservices environment, a service mesh complements the API Gateway by managing internal service-to-service communication, whereas the gateway handles client-to-service interactions.
    

  

**Challenges of API Gateways**

- **Single Point of Failure:** the gateway becomes a critical component, so if it fails, all requests to backend services are affected.
    
- **Complexity in Configuration:** managing the gateway and maintaining configurations can be complex as more services and clients are added
    
- **Increased Latency:** the gateway introduces an additional layer, potentially adding latency if not properly optimized.
    

API Gateways are essential in microservices and distributed systems, handling communication, security and efficiency at scale. By managing requests and abstracting backend complexity, gateways ensure smooth and secure interactions between clients and services, providing both developers and users with a seamless experience.

---

## Enterprise Service Bus (ESB)

It’s a software infrastructure designed to facilitate communication between various components of a distributed system, often in a microservices architecture. It serves as a central hub that enables asynchronous and reliable message exchange between independent applications or services, without requiring direct connections between them.

  

**Key features of a Service Bus**

- **Asynchronous Messaging:** Allows services to communicate without waiting for an immediate response, improving scalability and reducing wait times.
    
- **Decoupling:** Services don’t need to know about each other’s implementation, enabling flexibility and ease of maintenance.
    
- **Reliable Delivery:** Ensures messages are reliably sent and received, even in the event of failures, providing a robust communication backbone for complex systems.
    
- **Scalability:** Supports scaling by allowing multiple services to interact through a single, managed communication layer
    

  

**Queue**

It’s a data structure that works on the principle FIFO, where messages are placed in line and processed one at a time. In a Service Bus, queues are typically used for point-to-point communication. Only one consumer can process each message, making queues ideal for load balancing among services.

  

**Topic**

Topics support a publish-subscribe model, where a message sent to a topic can be received by multiple subscribers. Each subscriber gets its own copy of the message. Topics are effective for broadcasting messages to multiple services or systems that need to act upon the same data.

  

**Routing**

Service Buses often supports advanced routing mechanisms that direct messages to specific destinations based on criteria, ensuring that messages reach only the relevant subscribers or queues- this feature is particularly useful in complex environments where messages must be delivered to services based on content, priority or other criteria.

  

**Filters**

They allow the service bus to evaluate message properties or contents and selectively deliver them to appropriate subscribers. Filters can be based on attributes like message type, priority or custom properties, ensuring that only relevant services receive certain messages.

  

  

**Error Handling**

Service buses have mechanisms to handle failed message deliveries by attempting retries or logging errors for review. Configurable retry policies can be set, defining how often and under what conditions a message should be retried, as well as fallback procedures if all retries fail.

  

  

**Dead-Letter Messages**

When a message cannot be delivered after a defined number of attempts, it is sent to a dead-letter queue where it can be stored for analysis or manual intervention. Dead-lettering helps isolate problematic messages, preventing them from clogging up the main message flow.

Its advantages are decoupling (easy communication between services), scalability and resilience

Its limitations are latency, potential bottleneck and management complexity

  

  

**ESB (enterprise service bus) vs ETL (extract, transform, load)**

Both are tools in managing data flow and processing across complex IT environments but each serves a distinct purpose. ESB enables interoperability by allowing multiple services to communicate asynchronously. It acts as a central hub, integrating various systems without the need for direct connections between each pair of applications. ETL moves data from multiple sources into target system (like a data warehouse) for analysis and reporting, transforming the data to fit the target schema.

  

**Key components**

- **ESB:** message routing, message transformation, protocol mediation
    
- **ETL:** extract, transform, load
    

  

**Common uses for ESB**

Service Orchestration in Service-Oriented Architecture (SOA), integrating legacy systems with newer applications, real-time data exchange between multiple services in complex architectures.

  

**Common uses for ETL**

Building data warehouse for analytics and business intelligence, performing periodic batch processing, consolidating data from various operational systems for reporting.

  
---

## Enterprise Resource Planning (ERP)
TAGS: legacy monolithic system; SOAP

È un sistema software integrato che permette di gestire i processi operativi e amministrativi di un'azienda. Il suo scopo è centralizzare e automatizzare i processi aziendali per migliorare l'efficienza e ridurre gli errori. È usato per gestire risorse come personale, produzione, inventario, finanze, e altro.

Un ERP include diversi moduli che coprono diverse aree aziendali, ad esempio:

- **Contabilità e finanza:** gestione delle fatture, bilanci, ecc.
    
- **Gestione magazzino e inventario.**
    
- **Gestione produzione:** pianificazione e monitoraggio della produzione.
    
- **Supply Chain:** gestione di ordini, fornitori e logistica.
    
- **Risorse umane:** gestione del personale, buste paga, ecc.
    

  

Un ERP è utile per aziende di tutte le dimensioni che vogliono centralizzare la gestione aziendale in un unico sistema.

---

## PIM (Product Information Management) (on-premise, RestAPI e CSV exchange)**

Un PIM è un sistema specializzato per centralizzare, organizzare e distribuire le informazioni sui prodotti. Il suo scopo è gestire tutte le informazioni tecniche, descrittive e commerciali sui prodotti per garantire coerenza e accuratezza nei vari canali (e-commerce, cataloghi, distributori, ecc.).  
  

**Funzioni principali:**

- Centralizzare le informazioni sui prodotti (descrizioni, immagini, specifiche tecniche).
    
- Supportare più lingue e localizzazioni per prodotti destinati a mercati diversi.
    
- Permettere l'esportazione dei dati per l'e-commerce, brochure, o marketplace (Amazon, ecc.).
    

  

**Vantaggi:**

- Riduzione degli errori (ad esempio, dati incoerenti tra canali di vendita).
    
- Migliore gestione di cataloghi complessi.
    

  

Il PIM è utile per aziende che gestiscono un vasto catalogo prodotti e operano su più canali di vendita.

  
---
  

**CRM (Customer Relationship Management) (cloud, SaaS, RestAPI)**

Un CRM è un sistema per gestire le relazioni e le interazioni con i clienti. Il suo scopo è migliorare la gestione delle vendite, del supporto clienti e delle attività di marketing.

**Funzioni principali:**

- **Gestione dei contatti:** raccogliere informazioni sui clienti (nome, email, preferenze).
    
- **Tracciamento delle vendite:** gestire pipeline e opportunità di vendita.
    
- **Automazione del marketing:** invio di campagne email, segmentazione dei clienti.
    
- **Supporto clienti:** registrare richieste di assistenza, ticket, ecc.
    

  

**Vantaggi:**

- Migliora la fidelizzazione dei clienti e la personalizzazione dei servizi.
    
- Facilita il monitoraggio e l'ottimizzazione delle vendite.
    

Il CRM è utile per aziende che vogliono ottimizzare le vendite, migliorare la soddisfazione dei clienti e costruire relazioni solide.

  

  

**Database and Data Warehouse**

Un database è un sistema utilizzato per archiviare, gestire e recuperare dati operativi in tempo reale.

Un data warehouse è un sistema progettato per analizzare grandi quantità di dati storici provenienti da diverse fonti.

**Possibili motivazioni per un flusso "Macchinari → Data Warehouse → Database"**

**Analisi preliminare dei dati grezzi (Pre-elaborazione)**

- I dati raccolti dai macchinari potrebbero essere rumorosi, incompleti o ridondanti.
    
- Il data warehouse può essere utilizzato come un'area di staging per:
    
    - Pulire i dati, Aggregarli, Rimuovere valori anomali o duplicati
        
- Solo i dati elaborati vengono trasferiti al database operativo per scopi specifici
    

  

  

**SOAP and REST**

SOAP (Simple Object Access Protocol) è un protocollo di comunicazione utilizzato per lo scambio di informazioni strutturate tra sistemi in un formato standardizzato basato su XML.

  

SOAP è ideale per:

- Applicazioni aziendali complesse che richiedono sicurezza, transazioni, e affidabilità.
    
- Sistemi legacy che già lo utilizzano, come nel caso del tuo ERP.
    
- Situazioni in cui è necessario seguire standard stringenti (es. sanità o finanza).
    

  

REST (Representational State Transfer) è uno stile architetturale utilizzato per creare servizi web leggeri e scalabili, particolarmente adatto per applicazioni moderne. A differenza di SOAP, non è un protocollo, ma un insieme di principi che sfruttano le caratteristiche del protocollo HTTP.

  

REST è ideale per:

- Applicazioni moderne (es. mobile, web).
    
- API leggere che richiedono semplicità e velocità.
    
- Integrazioni tra sistemi diversi che utilizzano formati standard come JSON.
    
- Situazioni in cui il protocollo HTTP soddisfa le necessità (senza bisogno di standard avanzati come in SOAP).