### Service-Oriented Architecture
Work in groups of 5.

You are designing integrations for a medium-sized hospital. When a patient arrives at the hospital reception, the following steps occur:
1. The Admission System is used by the receptionist to start the admission.
2. The Admission System needs to:

    - Check whether the patient already exists in the National Patient Registry (NPR) using the CPR
    - If the patient exists, retrieve basic demographic data (name, date of birth, address) from the NPR
    - If the patient does not exist, create a new patient entry in the Hospital Patient Management System (HPMS)
3. For every admission, the Admission System must:

    - Verify coverage with the Insurance Validation Service (external to the hospital)
    - Reserve a bed through the Bed Management Service
    - Notify the Electronic Medical Record (EMR) System that a new admission has started, so that clinicians can access or create clinical data

4. The hospital uses a Service Registry.  
    Each service (NPR, HPMS, Insurance Validation, Bed Management, EMR) registers:
    - Its service name
    - Endpoint URL
    - Supported operations
    
    Systems that want to consume a service first query the Service Registry, obtain the endpoint and contract information, and then call the selected service.

**Tasks**

1. Identify roles. For each of the following systems, decide whether it acts as a service provider, service requester, or service broker:

    - Admission System
    - National Patient Registry (NPR)
    - Hospital Patient Management System (HPMS)
    - Insurance Validation Service
    - Bed Management Service
    - EMR System
    - Service Registry

    Note that a system could potentially play more than one role.

2. Describe the interaction flow from the moment the receptionist enters the patient's national ID until a bed is reserved and the EMR is notified. Focus on who requests what from whom.
3. Draw a simple diagram. It should show:

    - The systems as boxes
    - Arrows indicating service calls (with a short label, such as "check coverage", "reserve bed", etc.)
    - Which component you consider to be the service broker
