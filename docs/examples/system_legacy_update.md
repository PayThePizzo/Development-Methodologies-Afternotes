# System Legacy Update

## Introduction
As the Head of IT Infrastructure for a B2B company, you are responsible for overseeing an
ecosystem of technological systems that, while operational, present significant challenges due to
their legacy nature and lack of integration. Currently, your infrastructure comprises a monolithic on-
premises ERP solution, a modern SaaS-based CRM system offering a robust set of APIs for
integration, and a dedicated Warehouse Management System (WMS) – on premise, but quite
modern (even here you have a good set of APIs for integrations). The WMS communicates with the
ERP predominantly through CSV file exchanges to manage outbound logistics.

Despite supporting core business operations, these systems operate in silos. This lack of
integration has resulted in fragmented data management, most notably the existence of duplicate
customer records—one set maintained in the CRM and another in the ERP. Recent changes in
company leadership have shifted our strategic direction: the company is now preparing to expand
into the B2C market, necessitating new processes and public-facing sales channels (an e-
commerce). A critical requirement for this transformation is the consolidation and cleansing of
customer data across all platforms, allowing for unified client management and seamless
operations.
This introduction outlines the current state of our IT landscape and frames the challenges and
priorities that will drive our architectural and organizational solutions moving forward.
Objective
The objective of this case is to propose comprehensive architectural and organizational solutions
to effectively prepare the architecture for the future.
Case Study Overview
Before preparing the architectural and organizational solutions required by this test, you should
carefully consider the following key elements. These points highlight the main challenges and
priorities that must be addressed to ensure a successful transformation.
•
•
•
•
•
•
Assess the current technological ecosystem, carefully considering legacy system features
and the lack of integration.
Take into account the presence of modern systems equipped with APIs (CRM and WMS).
Identify the main issues regarding fragmented and duplicated customer data records.
Bear in mind that this new direction demands different processes and requires platforms to
be accessible to external (end) customers (obviously not directly).
Focus on the need to consolidate and cleanse customer data across all systems to support
future requirements.
Determine priorities and criticalities that will guide the architectural and organizational
solutions necessary to achieve future objectives.
Architectural Solutions
System Integration
Integrating various systems into a unified system, the architecture should enable seamless data
flow between these components and permit the implementation of the entire offering (refer to the
“Case Study Overview” paragraph).
Evaluate what you can do with ERP legacy system which permits limited possibilities for
integrations.