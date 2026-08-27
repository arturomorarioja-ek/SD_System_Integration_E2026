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

### Solution

1. Roles:

    | System                       | Provider   | Requester  | Broker  |
    | ---------------------------- | ---------- | ---------- | ------- |
    | Admission System             | (Optional) | **Yes**    | No      |
    | National Patient Registry    | **Yes**    | No         | No      |
    | Hospital Patient Management  | **Yes**    | (Optional) | No      |
    | Insurance Validation Service | **Yes**    | No         | No      |
    | Bed Management Service       | **Yes**    | No         | No      |
    | EMR System                   | **Yes**    | (Optional) | No      |
    | Service Registry             | No         | No         | **Yes** |
    
    - Admission System calls NPR to search for patient data, Insurance Validation Service to verify coverage, Bed Management Service to reserve a bed, EMR System to notify admission
        - It could be a service provider to other hospitals
    - NPR provides operations such as `FindPatientByCPR` or `GetPatientDemographics`
    - HPMS provides operations such as `CreatePatient` or `UpdatePatient`
    - Insurance Validation Service provides operations such as `ValidateCoverate` or `GetCoverageDetails`
    - Bed Management Service provides operations such as `ReserveBed`, `ReleaseBed` or `GetAvailableBeds`
    - EMR System provides operations such as `CreateAdmissionRecord` or `LinkPatientToAdmission`
        - It could also request patient information from NPR
    - Service Registry holds metadata for all services (endpoint, contract, operations) and allows the Admission System and others to discover provider services

2. Interaction flow

    1. The receptionist enters the patient's national ID into the Admission System
    2. The Admission System queries the Service Registry (broker) for the endpoint and contract of the NPR service
    3. The Admission System calls the NPR: `FindPatientByNationalId(nationalId)`
    4. If NPR returns data, the Admission System retrieves demographics; if not, it queries the Service Registry for the HPMS endpoint and calls `CreatePatient(...)` on HPMS to register a new internal patient
    5. The Admission System queries the Service Registry for the Insurance Validation Service and calls `ValidateCoverage(patientId, insuranceInfo)`
    6. The Admission System queries the Service Registry for the Bed Management Service endpoint and calls `ReserveBed(ward, priority, patientId)`
    7. Bed Management Service returns a `bedId` and possibly room information
    8. The Admission System queries the Service Registry for the EMR System endpoint and calls an operation such as `CreateAdmissionRecord(patientId, bedId, admissionReason)`
    9. Once the EMR acknowledges the admission, the Admission System confirms the admission to the receptionist and prints or displays the patient's bed information

3. Diagram

    <img width="1146" height="536" alt="image" src="https://github.com/user-attachments/assets/9029d5ef-4877-492b-aec5-4f0dcab5ab2a" />
