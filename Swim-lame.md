%% FOOD PANTRY DISTRIBUTION – SWIMLANE DIAGRAM
flowchart LR
    %% Lanes (horizontal rows)
    subgraph Logistics [LOGISTICS DEPARTMENT<br/>Inventory & Storage]
        direction LR
        A1[Receive Donations/Shipments]
        --> A2[Inspect: Expiration, Packaging, Temp]
        --> A3{Usable & Safe?}
        A3 -- Yes --> A4[Store Items]
        A3 -- No --> A5[Dispose / Report to Donor]
        A4 & A5 --> A6[Update Inventory System]
        A6 --> A7[Troubleshooting: Shortages, Wrong Delivery, Refrigeration Failure]
    end

    subgraph Social [SOCIAL SERVICES<br/>Eligibility & Records]
        direction LR
        B1[Register Client / Retrieve Record]
        --> B2[Inspect: Verify ID & Documents]
        --> B3{Eligible?}
        B3 -- Yes --> B4[Approve for Food Pack]
        B3 -- No --> B5[Provide Referrals / Close Intake]
        B4 --> B6[Review Household Size & Dietary Needs]
        B5 & B6 --> B7[Troubleshooting: Missing Docs, Duplicates, Language Barriers]
    end

    subgraph Volunteers [VOLUNTEERS<br/>Packing & Portioning]
        direction LR
        C1[Select Items by Household Size]
        --> C2[Assemble Bags/Boxes]
        --> C3[Inspect: Quantity, Quality, Dietary]
        --> C4{Pack Complete & Balanced?}
        C4 -- Yes --> C5[Move to Distribution Queue]
        C4 -- No --> C6[Fix / Substitute Items]
        C5 & C6 --> C7[Troubleshooting: Low Stock, Mislabeling, Pack Errors]
    end

    subgraph Distribution [DISTRIBUTION TEAM<br/>Logistics + Social Services + Volunteers]
        direction LR
        D1[Call Client / Verify ID]
        --> D2[Inspect: Pack Matches Household & Notes]
        --> D3{Suitable & Client Satisfied?}
        D3 -- Yes --> D4[Handover Pack & Log Distribution]
        D3 -- No --> D5[Adjust Items / Escalate]
        D4 & D5 --> D6[Troubleshooting: Mobility Issues, Long Lines, Wrong Pack]
    end

    subgraph FollowUp [SOCIAL SERVICES<br/>Follow-Up & Reporting]
        direction LR
        E1[Conduct Satisfaction Survey]
        --> E2[Inspect: Review Responses]
        --> E3{Further Support Needed?}
        E3 -- Yes --> E4[Provide Additional Referral/Service]
        E3 -- No --> E5[Close Case & Log Feedback]
        E4 & E5 --> E6[Troubleshooting: Incomplete Survey, Complaints]
    end

    subgraph Outputs [OUTPUTS]
        direction LR
        O1[Food Packs Distributed]
        O2[Updated Inventory Records]
        O3[Usage Statistics for Donors]
        O4[Client Feedback & Satisfaction Data]
    end

    %% Cross-lane connections
    A6 --> B1
    B6 --> C1
    C5 --> D1
    D4 --> E1
    E5 --> O1

    %% Styling (optional but nice)
    classDef action fill:#e3f2fd,stroke:#1565c0,stroke-width:2px
    classDef inspect fill:#fff3e0,stroke:#ef6c00,stroke-width:2px
    classDef decision fill:#f3e5f5,stroke:#6a1b9a,stroke-width:2px
    classDef trouble fill:#ffebee,stroke:#c62828,stroke-width:2px
    classDef output fill:#e8f5e8,stroke:#2e7d32,stroke-width:2px

    class A1,A4,A5,A6,B1,B4,B5,B6,C1,C2,C5,C6,D1,D4,D5,E1,E4,E5 action
    class A2,B2,C3,D2,E2 inspect
    class A3,B3,C4,D3,E3 decision
    class A7,B7,C7,D6,E6 trouble
    class O1,O2,O3,O4 output
