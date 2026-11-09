**Software Architecture**
- Monolith
- N-Tier
- Enterprise SOA
- Microservices
- Serverless
- P2P
 
**Software Application Patterns**
- Application Patterns
  - Layered
  - Onion
  - Hexagonal
  - Modular monolith
  - Microkernel
  - CQRS
  - Event sourcing
- UI Patterns
  - MVC
  - MVP
  - MVVM

**Service-Oriented Architecture**
- DOA (Distributed Object Architecture): CORBA, MS DCOM
- SOC
  - Service providers vs. service requesters vs. service brokers
  - Composition
    - Orchestration
    - Choreography
  - Service substitution
    - Reconfiguration (replacement)
    - Recomposition (specification change)
  - SOA
    - Service providers = service producers vs. service requesters = service consumers vs. service brokers

**File Formats**
- Content-based file types: binary, text
- Text file types
  - Flat Text: delimited, CSV
  - Markup Languages
    - Presentation (e.g., RTF)
    - Procedural (e.g., MD, LaTeX)
    - Descriptive = semantic (e.g., XML)
  - Data Serialisation Languages
    - JSON
    - YAML

**XML**
- Well-formed XML
- Namespaces
- XSD
- XSL

**TCP/IP**
- TCP
- UDP
- QUIC
- SSL/TLS

**HTTP**
- HTTP/1.1
- HTTP/2
- HTTP/3
- HTTPS

**REST**
- Constraints
  - Client-Server Architecture
  - Statelessness
  - Cacheability
  - Layered System
  - Code on Demand (optional)
  - Uniform Interface
    - Resource Identification in Request
    - Resource Manipulation Through Representations
    - Self-Descriptive Messages
    - HATEOAS (Hypermedia as the Engine of Application State)
- Versioning Strategies
- Pagination and Filtering

**SOAP**
- SOAP Message
  - Envelope
  - Header (optional)
  - Body
    - Fault
  - Encoding (optional)
- WS-Security
- WSDL (Web Services Description Language)

**GraphQL**
- Overfetching & Underfetching
- GraphQL Operations
  - Query
  - Mutation
  - Subscription
- Pagination, Alias, Variables, Conditional Directives, Fragments, Unions
- SDL (Schema Definition Language)
- GraphQL Server: Resolvers

**gRPC**
- Types of Communication
  - Unary RPC
  - Server-Side Streaming RPC
  - Client-Side Streaming RPC
  - Bidirectional Streaming RPC
- Protocol Buffers
- Further gRPC Features: Deadlines, Terminations, Interceptors, Reflection

**API Security** 
- Security Attacks That Affect APIs
  - SQL-Injection
  - XSS
  - CSRF
  - Session Hijacking
  - Clickjacking
  - DoS
  - Oversized Payloads
- API Security Best Practices
  - Authentication
    - HTTP Authentication
    - Token-Based Authentication
      - Session Cookies
      - Session Fixation
      - Cookie Security
      - Bearer Token
      - Token Hardening
      - API Key Management
    - JWT
      - Header
      - Payload
      - Signature
    - OAuth 2.0 / OIDC
      - Resource Owner, Resource Server, Client, Authorization Server, Grant Type, Scope
- CORS
  - SOP
  - Preflight Requests

**WebSockets** 
- Constant Polling
- Long Polling
- SSE (Server-Sent Events)
- WebSockets

**Distributed Databases**
- Replication
  - Leader-Leader
  - Leader-Follower
- Partitioning
  - Vertical
  - Horizontal
    - By list of values
    - By range of dates
    - By key hash
- Sharding
  - Tenant-based
  - Hash-based
- ETL (Extract-Transform-Load)
