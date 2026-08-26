### Software Architectures
Work in groups of 5.

Match the following scenarios to the software architecture(s) that best fit them (monolith, N-tier, Enterprise SOA, microservices, serverless, peer-to-peer):

1. **Eksaminator**. Online exam submission system  
    The platform is used by students to upload assignments and by teachers to grade. Requirements:
    - Moderate number of users (a few thousand)
    - High data integrity
    - Strict deadlines
    - Predictable load (peaks around exam periods)
    - Limited budget for operations
    - No real-time features   
2. **Ride-Now**. Real-time ride-sharing app  
    Features:
    - GPS location tracking
    - Real-time driver availability
    - Dynamic pricing
    - Independent evolution of subsystems (dispatch, payments, driver onboarding)
    - Very high availability required
    - Continuous deployment expected   
3. **Stockflow**. Batch-processing inventory system for a warehouse  
    Situation:
    - Three legacy systems: ordering, shipping, and warehouse stock
    - Operations run nightly (batch)
    - CEO wants them coordinated, not replaced
    - Each subsystem already exposes some form of interface (XML or CSV over FTP / HTTP)
    - Real-time performance is not a requirement
4. **Smart-Gallery**. Photo tagging and catalogue  
    Context:
    - Users upload photos
    - Automatic image recognition tags them
    - Metadata stored in a small database
    - Spiky workload (weekends heavy, weekdays low)
    - Minimal ops team
    - Budget sensitive
    - Processing of each image is independent
    - However: business expects future features (face recognition privacy rules, shared galleries, advanced search)
5. **Musik-Fest**. Digital programme and media downloads  
    Festival organisers need a mobile app providing:
    - Artist programme schedule
    - Map of stages
    - Push notifications
    - Downloadable audio previews (30–60 seconds each)
    - A portal where organisers upload content
    - Analytics, but only when network is available
      
    Requirements:
    - Must work offline after initial sync
    - Real-time social features are out of scope
    - Content updates are infrequent (daily)
    - Back-office is small and can accept simple deployments

To assess the applicability of each architecture to each scenario, you may consider the following factors, among others:
- Cost
- Fault isolation
- Team autonomy
- Deployment
- Scalability
