# diagramaProcesos
```mermaid
flowchart LR
    %% ==========================================
    %% Estilos de las Líneas de Metro (Colores)
    %% ==========================================
    classDef crm fill:#2E7D32,stroke:#1B5E20,stroke-width:2px,color:#fff
    classDef sales fill:#F57C00,stroke:#E65100,stroke-width:2px,color:#fff
    classDef purchasing fill:#0288D1,stroke:#01579B,stroke-width:2px,color:#fff
    classDef service fill:#FBC02D,stroke:#F57F17,stroke-width:2px,color:#000
    classDef inventory fill:#616161,stroke:#212121,stroke-width:2px,color:#fff
    classDef production fill:#4A148C,stroke:#311B92,stroke-width:2px,color:#fff
    classDef finance fill:#D32F2F,stroke:#B71C1C,stroke-width:2px,color:#fff
    classDef reporting fill:#AB47BC,stroke:#4A148C,stroke-width:2px,color:#fff

    %% ==========================================
    %% Línea CRM / SRM (Verde)
    %% ==========================================
    subgraph CRM_SRM ["CRM / SRM"]
        direction TB
        ACT(("Activities"))
        CUST(("Customer"))
        LEAD(("Lead"))
        SUPP(("Supplier"))
        BPM(("Business Partner<br/>Master"))
        
        ACT --- CUST --- LEAD --- SUPP --- BPM
    end

    %% ==========================================
    %% Línea Service (Amarillo)
    %% ==========================================
    subgraph SERVICE ["Service"]
        CEC(("Customer<br/>Equipment Card"))
        SC(("Service Call"))
        SCT(("Service Contract"))
        SB(("Service Billing"))

        CEC ==> SC ==> SCT ==> SB
    end

    %% ==========================================
    %% Línea Sales (Naranja)
    %% ==========================================
    subgraph SALES ["Sales"]
        OPP(("Opportunity"))
        PRC(("Pricing"))
        SQ(("Sales Quotation"))
        SO(("Sales Order"))
        DN(("Delivery Note"))
        ARI(("AR Invoice"))
        IP(("Incoming Payments"))

        OPP ==> PRC ==> SQ ==> SO ==> DN ==> ARI ==> IP
    end

    %% ==========================================
    %% Línea Purchasing (Azul)
    %% ==========================================
    subgraph PURCHASING ["Purchasing"]
        PR(("Purchase Request"))
        PQ(("Purchase Quotation"))
        PO(("Purchase Order"))
        GRPO(("Goods Receipt PO"))
        API(("AP Invoice"))
        OP(("Outgoing Payments"))

        PR ==> PQ ==> PO ==> GRPO ==> API ==> OP
    end

    %% ==========================================
    %% Línea Production (Morado Oscuro)
    %% ==========================================
    subgraph PRODUCTION ["Production"]
        BOM(("Bill of Materials"))
        MRP(("Material Requirements<br/>Planning"))
        SRC(("Sourcing"))
        PROD(("Production Order"))
        ITP(("Issue to Production"))
        RFP(("Receipt from Production"))

        BOM ==> MRP ==> SRC ==> PROD ==> ITP ==> RFP
    end

    %% ==========================================
    %% Línea Inventory (Gris)
    %% ==========================================
    subgraph INVENTORY ["Inventory"]
        IM(("Item Master"))
        WM(("Warehouse<br/>Management"))
        DP(("Demand Planning"))

        IM --- WM
    end

    %% ==========================================
    %% Línea Finance (Rojo)
    %% ==========================================
    subgraph FINANCE ["Finance"]
        COA(("Chart of Accounts"))
        GLA(("General Ledger<br/>Accounts"))
        GLD(("G/L Account<br/>Determination"))
        CA(("Cost Accounting"))
        JE(("Journal Entries"))
        APAR(("AP / AR"))
        CM(("Cash Management"))
        REC(("Reconciliation"))
        FR(("Financial Reporting"))

        COA ==> GLA ==> GLD ==> CA ==> JE ==> APAR ==> CM ==> REC ==> FR
    end

    %% ==========================================
    %% Línea Reporting (Rosa / Magenta)
    %% ==========================================
    subgraph REPORTING ["Reporting"]
        BR(("Backorder<br/>Reporting"))
        IAR(("Inventory Audit<br/>Report"))
        ABR(("Account Balances<br/>Report"))
        PR_REP(("Product Reporting"))

        BR ==> IAR ==> ABR ==> PR_REP
    end

    %% ==========================================
    %% Interconexiones entre procesos
    %% ==========================================
    CUST ==> OPP
    CUST -.-> CEC
    LEAD -.-> OPP
    SUPP -.-> PR
    IM --- PRC
    WM --- SO
    SO --- PO
    PO --- PROD
    PROD --- DP
    BOM -.-> DP
    SB -.-> ARI
    PROD -.-> BR
    APAR -.-> ARI
    CM -.-> IP
    CM -.-> OP
    RFP ==> PR_REP

    %% ==========================================
    %% Asignación de Clases
    %% ==========================================
    class ACT,CUST,LEAD,SUPP,BPM crm
    class OPP,PRC,SQ,SO,DN,ARI,IP sales
    class PR,PQ,PO,GRPO,API,OP purchasing
    class CEC,SC,SCT,SB service
    class IM,WM,DP inventory
    class BOM,MRP,SRC,PROD,ITP,RFP production
flowchart LR
   
    class COA,GLA,GLD,CA,JE,APAR,CM,REC,FR finance
    class BR,IAR,ABR,PR_REP reporting
```


