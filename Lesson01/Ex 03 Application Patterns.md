### Application Patterns
Work in groups of 5.

Match the following scenarios to the application pattern that best fits them (layered, onion, hexagonal, modular monolith, microkernel, CQRS, event sourcing):

1. **Product Catalogue**  
   Large e-commerce platform:
   - Writes (product updates) are rare and done by a small admin team
   - Reads (product browsing, search, filtering) happen millions of times per day
   - Read requirements differ significantly from write requirements (denormalised views, search indices)
   
2. **Booking System**  
   A flight and hotel booking platform built around a rich domain model (reservations, pricing rules, cancellations).  
   The company wants domain logic insulated from frameworks, UI, and database technology because they expect a migration from SQL to NoSQL in two years.
   
3. **ERP Lite**  
   Medium-sized enterprise app with clearly separated domains: Inventory, Invoicing, HR, Scheduling.  
   All modules share the same codebase and database, but must enforce strict boundaries so that teams can work independently without committing to microservices.
   
4. **Bank Ledger with Audit Trail**  
   A financial ledger must store not just account balances but a complete history of all changes.    
   Auditors require the ability to reconstruct the state at any moment in the past.  
   Corrections must be made as compensating transactions, never by editing data.
   
5. **Webshop**  
   A standard webshop with predictable CRUD operations: list products, add to cart, place order, update user info.  
   Stable requirements, minimal complexity, classic front-end + business logic + data access setup.
   
6. **Photo Editor with Plugins**  
   Users download a desktop photo editor with a solid core (loading/saving images, basic editing).  
   Most features (filters, effects, exporters) must be independent plugins that third-party developers can write and users can install dynamically.
   
7. **Payment Adapter Hub**  
   A company must support many payment providers (Stripe, MobilePay, Klarna, PayPal).  
   Each provider has different APIs, authentication models, and workflows.  
   The business logic should not change when a provider is replaced.
