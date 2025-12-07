```mermaid
flowchart TB
    subgraph Logistics [LOGISTICS DEPARTMENT (Inventory & Storage)]
        direction TB
        Start((Start)) --> Receive[Receive Donations/Shipments]
        Receive --> Inspect1[Check expiration, packaging, temperatures]
        Inspect1 --> Decision1{Usable?}
        Decision1 -- Yes --> Store[Store Items]
        Decision1 -- No --> Dispose[Dispose/Report Issue]
        Store --> Update[Update Inventory System]
        Dispose --> Update
    end

    subgraph SocialServices1 [SOCIAL SERVICES (Eligibility & Records)]
        direction TB
        Register[Register Client / Retrieve Record] --> Inspect2[Verify Documentation]
        Inspect2 --> Decision2{Eligible?}
        Decision2 -- Yes --> Approve[Approve Client for Pack]
        Decision2 -- No --> Referrals[Provide Referrals / Close Intake]
        Approve --> Review[Review Household Needs]
        Referrals --> EndSS1(( ))
    end

    subgraph Volunteers [VOLUNTEERS (Packing & Portioning)]
        direction TB
        Assemble[Assemble Food Packs] --> Inspect3[Check Quantity & Item Quality]
        Inspect3 --> Decision3{Complete Pack?}
        Decision3 -- Yes --> Queue[Move to Distribution Queue]
        Decision3 -- No --> Fix[Fix Pack / Request Substitution]
        Fix --> Queue
    end

    subgraph Distribution [DISTRIBUTION TEAM (Logistics + Social Services + Volunteers)]
        direction TB
        Call[Call Client / Verify ID] --> Inspect4[Match Pack to Household Size]
        Inspect4 --> Decision4{Suitable?}
        Decision4 -- Yes --> Handover[Handover Pack]
        Decision4 -- No --> Adjust[Adjust Items / Escalate to Social Services]
        Adjust --> Handover
    end

    subgraph SocialServices2 [SOCIAL SERVICES (Follow-Up)]
        direction TB
        Survey[Conduct Client Survey] --> Inspect5[Review Feedback]
        Inspect5 --> Decision5{Further Support Needed?}
        Decision5 -- Yes --> Referral[Provide Referral]
        Decision5 -- No --> Close[Close Case]
        Referral --> Close
    end

    subgraph Outputs [OUTPUTS]
        direction LR
        Out1[Distributed Food Packs] --- Out2[Updated Records] --- Out3[Donor Usage Metrics] --- Out4[Client Feedback Logged]
    end

    Update --> Register
    Review --> Assemble
    Queue --> Call
    Handover --> Survey
    Close --> Outputs

    style Logistics fill:#f9f,stroke:#333,stroke-width:2px
    style SocialServices1 fill:#bbf,stroke:#333,stroke-width:2px
    style Volunteers fill:#bfb,stroke:#333,stroke-width:2px
    style Distribution fill:#ffb,stroke:#333,stroke-width:2px
    style SocialServices2 fill:#bbf,stroke:#333,stroke-width
:2px
    style Outputs fill:#fff,stroke:#333,stroke-width:2px
```




