# Retail Organization

Scenario: A retail company uses a legacy ERP system
for inventory management but needs a modern
online store to compete in e-commerce.
Solution 1: Encapsulation via SOA
–
 Expose inventory functionality as a SOAP-based API.
–
 Minimal changes to the legacy system.
–
 Standardized access to ERP functionality.
–
 Simplifies integration with modern applications.
Solution 2: Modernization with Microservices
– Build a microservice for online order processing,
integrating with the legacy inventory system.
– Designed to be scalable and deployable on cloud
platforms.
– Developed in parallel, without requiring changes to
the legacy system.
•
•
Solution 3: Strangler Pattern
– Gradually replace the ERP inventory module with a
new microservice, ensuring minimal downtime.
– Initially, all requests continue to go through the legacy
ERP system.
– Over time, new functionalities (e.g., inventory
management) are implemented as microservices.
– Eventually, the legacy module is entirely replaced
without significant downtime.
Outcome
– The company retains its reliable ERP system for
critical operations, minimizing risk and cost.
– Modern microservices provide scalability, flexibility,
and support for e-commerce functionality.
– Gradual migration ensures business continuity while
introducing modern architecture.