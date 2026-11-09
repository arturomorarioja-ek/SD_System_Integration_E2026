### Distributed database pattern matching
Match the real-world scenarios below to these distributed database patterns:
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

Take into account that more than one main pattern (e.g., replication and partitioning) can be chosen for certain scenarios.

Work in groups of 4 or 5 students.

**Scenarios**  
1. Global e-commerce platform with worldwide service
    - Most traffic is reads (product browsing)
    - Writes (orders, updates) are less frequent but critical
    - The system must remain available even if a region is down
2. SaaS platform with multiple customers
    - Each company's data must be logically isolated
    - Some customers are much larger than others
    - Cross-customer queries are rare
3. Logging system 
    - Continuous logging from thousands of services
    - Queries typically retrieve logs from the last day or week
    - Old logs are archived or deleted
4. Social media: user profiles and activity
    - Users are evenly distributed
    - Horizontal scaling is necessary
    - Queries are often per user (e.g., retrieving a user timeline)
5. Financial system processing transactions
    - Consistency and integrity are critical
    - Control over writes is necessary
    - Read replicas are acceptable for reporting
6. Collaborative document editing system
    - Multiple users can edit simultaneously
    - Writes happen from different locations
    - Real-time: low latency necessary
7. Business analytics dashboard
    - Heavy read queries (aggregations)
    - Data comes from multiple sources
    - Slight delay in data consistency is acceptable
8. Wide user profile table for a sales platform
    - Frequently accessed fields (name, email)
    - Rarely accessed fields (preferences, logs)
    - Common queries must have optimized performance
