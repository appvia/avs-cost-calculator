# VMware to Azure VMware Solution Migration ROI Calculator

## Overview

This web-based calculator provides a comprehensive Total Cost of Ownership (TCO) and Return on Investment (ROI) analysis for migrating from on-premises VMware infrastructure to Azure VMware Solution (AVS). The calculator uses established financial methodologies to evaluate migration benefits, costs, and modernization opportunities.

## Key Features

- **Two cost calculation methods**: Fixed annual cost or detailed breakdown
- **Hardware refresh planning**: Automatically factors in refresh cycles and timing
- **Modernization analysis**: Evaluates savings from moving to native Azure services
- **Financial metrics**: ROI, NPV, and accurate payback period calculations
- **Comprehensive documentation**: Built-in methodology and formula explanations

## Calculator Structure

The calculator is organized into six main tabs:

### 1. Current Environment Tab

**Purpose**: Capture baseline costs of your existing on-premises VMware environment.

#### Cost Calculation Methods

**Fixed Annual Cost Method:**
- **Input**: Total Annual On-Premises Cost (£)
- **Why**: Simplified approach using a single cost figure
- **Formula**: `On-Premises Annual Cost = Fixed Annual Cost`
- **Hardware Estimation**: `Hardware Portion = 50% of Fixed Cost` (for refresh calculations)

**Detailed Cost Breakdown Method:**
- **Infrastructure Costs (Annual)**:
  - `Hardware Depreciation/Lease (£)` - Server hardware costs including depreciation
  - `VMware Licensing (£)` - vSphere, vCenter, vSAN, NSX licensing and support
  - `Storage Hardware (£)` - SAN, NAS, direct-attached storage costs
  - `Network Equipment (£)` - Switches, routers, firewalls, load balancers
  - `Backup Hardware/Software (£)` - Backup solutions and offsite storage
  - `Support Contracts (£)` - Hardware and software maintenance contracts

- **Facilities & Operations (Annual)**:
  - `Data Centre Space (£)` - Rack space, colocation, facility costs
  - `Power & Cooling (£)` - Electricity, UPS, HVAC costs
  - `Staff Costs (£)` - IT personnel managing VMware infrastructure
  - `Internet/Connectivity (£)` - ISP, MPLS, dedicated line costs

**Formula**: 
```
On-Premises Annual Cost = Infrastructure + Operations
Infrastructure = Hardware + VMware Licensing + Storage + Network + Backup + Support
Operations = Data Centre + Power/Cooling + Staff + Connectivity
Hardware Portion = Hardware + Storage + Network Equipment
```

#### Hardware Refresh Planning

- **Hardware Purchase Date** - When current hardware was acquired
- **Hardware Refresh Cycle (Years)** - Typical refresh frequency (3-5 years)
- **Refresh Cost Multiplier** - Cost increase for newer technology (e.g., 1.15 = 15% increase)
- **Percentage to Refresh (%)** - What portion needs refreshing

**Formulas**:
```
Current Age = (Today - Purchase Date) / 365.25 days
Next Refresh Year = Ceiling(Current Age / Cycle) × Cycle
Refresh Cost = Hardware Portion × Cost Multiplier × (Refresh % / 100)
```

#### Environment Details

- **Number of VMs** - Total virtual machines
- **Total vCPUs** - Virtual CPU cores allocated
- **Total RAM (GB)** - Memory allocated across VMs
- **Total Storage (TB)** - Storage consumed by VMs

### 2. Azure VMware Solution Tab

**Purpose**: Configure Azure VMware Solution costs and services.

#### AVS Configuration

- **AVS Node Type** - Choose from AV36, AV36P, or AV52 based on performance needs
- **Number of AVS Nodes** - Minimum 3 nodes required, size for capacity + 25% headroom
- **Reserved Instance Term** - Pay-as-you-go, 1-year, or 3-year reserved instances
- **Azure Hybrid Benefit** - Use existing Windows/SQL licenses for additional savings

**Node Costs (Monthly, GBP)**:
- AV36: £7,000 (PAYG), £5,600 (1-year), £4,200 (3-year)
- AV36P: £9,350 (PAYG), £7,480 (1-year), £5,610 (3-year)  
- AV52: £14,000 (PAYG), £11,200 (1-year), £8,400 (3-year)

**Formulas**:
```
Monthly AVS Cost = Node Cost × Number of Nodes × Pricing Tier
Azure Hybrid Benefit = 40% savings on compute portion
Total Monthly Azure Cost = AVS Nodes + Additional Services
```

#### Additional Azure Services (Monthly)

- **ExpressRoute (£)** - Dedicated private connection to Azure
- **Azure Backup (£)** - Backup service costs based on data volume
- **Data Transfer (£)** - Outbound traffic, VPN, cross-region charges
- **Monitoring & Management (£)** - Azure Monitor, Log Analytics, Security Center
- **Additional Storage (£)** - Extra storage beyond AVS nodes
- **Security Services (£)** - Azure Security Center, Sentinel, Key Vault

### 3. Modernisation Tab

**Purpose**: Identify workloads that can move to native Azure services instead of AVS.

#### Application Modernisation

- **VMs Moving to Azure VMs (%)** - Percentage moving to native Azure compute
- **Applications to PaaS (Count)** - Apps moving to App Service, Functions
- **Databases to Managed Services (Count)** - DBs moving to Azure SQL, MySQL, etc.
- **File Servers to Azure Files (Count)** - File servers replaced by Azure Files

#### Modernisation Impact

- **AVS Node Reduction (Count)** - Nodes eliminated through modernisation
- **VMware License Reduction (%)** - Licensing cost reduction
- **Modernisation Timeline (Months)** - Time to complete modernisation
- **Modernisation Investment (£)** - One-time modernisation costs

#### Native Azure Service Costs (Monthly)

- **Azure VMs Cost (£)** - Native Azure compute costs
- **PaaS Services Cost (£)** - App Service, Functions costs
- **Managed Database Cost (£)** - Azure SQL, managed database costs
- **Azure Storage Cost (£)** - Files, Blob storage costs

**Formulas**:
```
Modernisation Start Year = Ceiling(Timeline in Months / 12)
Node Savings = Nodes Saved × Node Cost Per Year
Modernisation Savings = Node Savings - Native Azure Service Costs
```

### 4. Migration Costs Tab

**Purpose**: Capture one-time migration investment and analysis parameters.

#### One-Time Migration Costs

- **Assessment & Planning (£)** - Discovery, workshops, architecture design
- **Migration Tools & Services (£)** - Azure Migrate, HCX licensing, replication tools
- **Professional Services (£)** - Microsoft/partner services for migration execution
- **Training & Certification (£)** - Azure training for IT staff
- **Downtime/Business Impact (£)** - Cost of business disruption during migration
- **Contingency (%)** - Buffer for unexpected costs (typically 10-20%)

**Formula**:
```
Total Migration Investment = (Base Migration Costs × (1 + Contingency%)) + Modernisation Investment
```

#### Timeline & Analysis Parameters

- **Analysis Period (Years)** - Time horizon for ROI analysis (typically 3-5 years)
- **Discount Rate (%)** - Company cost of capital for NPV calculations (typically 6-10%)
- **Annual Growth Rate (%)** - Expected IT cost inflation (typically 3-5%)
- **Migration Timeline (Months)** - Time to complete initial AVS migration

### 5. Documentation Tab

**Purpose**: Comprehensive explanation of calculation methodology, formulas, and assumptions.

#### Core Financial Formulas

**Return on Investment (ROI)**:
```
ROI = [(Total Benefits - Total Investment) / Total Investment] × 100

Where:
- Total Benefits = Sum of annual cost savings over analysis period
- Total Investment = Migration costs + Modernisation investment + Contingency
```

**Net Present Value (NPV)**:
```
NPV = Σ(t=1 to n) [CFt / (1 + r)^t] - Initial Investment

Where:
- CFt = Cash flow (cost savings) in year t
- r = Discount rate (company's cost of capital)
- t = Year number
- n = Analysis period in years
```

**Payback Period**:
```
Payback Period = Time when Cumulative Discounted Cash Flows ≥ Initial Investment
Uses linear interpolation within payback year for precision
```

#### Growth and Timing Calculations

**Annual Cost Growth**:
```
Cost in Year t = Base Cost × (1 + Growth Rate)^(t-1)
```

**Hardware Refresh Timing**:
```
Hardware Age = (Current Date - Purchase Date) / 365.25
Next Refresh = Ceiling(Hardware Age / Refresh Cycle) × Refresh Cycle
Years Until Refresh = Next Refresh - Hardware Age
```

### 6. ROI Analysis Tab

**Purpose**: Display comprehensive financial analysis results and breakdowns.

#### Key Metrics Displayed

- **Return on Investment (ROI)** - Percentage return on migration investment
- **Net Present Value (NPV)** - Present value of future savings minus investment
- **Payback Period** - Time to recover initial investment through savings
- **Total Investment** - Complete upfront costs including contingency
- **Total Benefits** - Sum of cost savings over analysis period
- **Modernisation Savings** - Additional savings from native Azure services

#### Detailed Breakdowns

**Annual Cost Comparison Table**:
- Year-by-year comparison of on-premises vs Azure costs
- Hardware refresh costs highlighted when they occur
- Modernisation savings shown after modernisation timeline
- Cumulative savings tracking

**Cost Breakdown Summary**:
- Category-by-category comparison of cost structures
- Difference calculations showing savings/costs per category

## Key Assumptions

1. **Fixed Cost Method**: Hardware represents 50% of total costs
2. **Staff Reduction**: 30% reduction in staff costs with Azure (breakdown method)
3. **Growth Rates**: Applied equally to on-premises and Azure costs
4. **Hardware Refresh**: Occurs when equipment reaches refresh cycle age
5. **Modernisation**: Savings begin after modernisation timeline
6. **Currency**: All costs in GBP (£)

## Limitations

- Does not include intangible benefits (agility, innovation, scalability)
- Azure pricing is estimated and may vary by region and contract terms
- Assumes steady-state operations after migration completion
- Does not account for business disruption during migration
- Hardware refresh timing assumes uniform equipment age

## Usage Instructions

1. **Start with Current Environment**: Choose cost calculation method and enter baseline costs
2. **Configure Azure Solution**: Size AVS environment and select pricing options
3. **Plan Modernisation**: Identify workloads for native Azure services
4. **Estimate Migration Costs**: Include all one-time investment costs
5. **Review Documentation**: Understand methodology and assumptions
6. **Calculate ROI**: Generate comprehensive financial analysis

## Technical Requirements

- Modern web browser with JavaScript enabled
- No server-side dependencies required
- Single HTML file for easy deployment and sharing

## File Structure

```
├── index.html          # Complete calculator application
└── README.md          # This documentation file
```

## Mathematical Validation

All formulas follow established financial analysis principles:
- NPV uses proper discounting with time value of money
- ROI calculation follows standard investment analysis methodology
- Payback period uses cumulative discounted cash flows for accuracy
- Growth rates applied using compound interest formulas

## Support and Maintenance

This calculator provides a framework for migration cost analysis. Users should:
- Validate Azure pricing with current Microsoft pricing sheets
- Adjust assumptions based on specific organizational factors
- Consult with Azure specialists for complex migration scenarios
- Update calculations as business requirements change 