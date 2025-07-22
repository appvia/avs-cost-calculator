# VMware to Azure VMware Solution Migration ROI Calculator

## Overview

This web-based calculator provides a comprehensive Total Cost of Ownership (TCO) and Return on Investment (ROI) analysis for migrating from on-premises VMware infrastructure to Azure VMware Solution (AVS). The calculator uses established financial methodologies to evaluate migration benefits, costs, and modernization opportunities.

## Key Features

- **Enhanced node type support**: Choose from AV36, AV36P, AV52, and AV64 based on workload requirements
- **Two cost calculation methods**: Fixed annual cost or detailed breakdown
- **VMware license inflation modeling**: Accounts for Broadcom-driven VMware cost increases
- **Hardware refresh planning**: Automatically factors in refresh cycles and timing
- **Optional modernization analysis**: Evaluates savings from moving to native Azure services (defaults to £0)
- **Simplified core migration costs**: Focus on assessment, professional services, downtime, and service transition
- **Streamlined partner funding**: Microsoft migration funding, Azure credits, and additional incentives
- **Detailed calculation breakdowns**: Step-by-step explanation of all calculations
- **Simplified financial metrics**: ROI, payback period, and total cost savings
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

- **AVS Node Type** - Choose from AV36, AV36P, AV52, or AV64 based on performance needs
- **Number of AVS Nodes** - Minimum 3 nodes required, size for capacity + 25% headroom
- **Reserved Instance Term** - Pay-as-you-go, 1-year, or 3-year reserved instances
- **Azure Hybrid Benefit** - Use existing Windows/SQL licenses for additional savings

**Node Type Characteristics:**
- **AV36**: Balanced compute and memory, ideal for general workloads
- **AV36P**: Enhanced memory (768GB vs 576GB), perfect for memory-intensive applications
- **AV52**: High-performance with maximum memory (1536GB) and storage (30.72TB), suitable for demanding workloads
- **AV64**: CPU-optimized with 64 cores but lower memory (512GB), ideal for compute-intensive applications

**Node Costs (Monthly, GBP)**:
- AV36: £7,000 (PAYG), £5,600 (1-year), £4,200 (3-year) - 36 cores, 576GB RAM, 15.36TB vSAN
- AV36P: £9,350 (PAYG), £7,480 (1-year), £5,610 (3-year) - 36 cores, 768GB RAM, 15.36TB vSAN
- AV52: £14,000 (PAYG), £11,200 (1-year), £8,400 (3-year) - 52 cores, 1536GB RAM, 30.72TB vSAN
- AV64: £11,200 (PAYG), £8,960 (1-year), £6,720 (3-year) - 64 cores, 512GB RAM, 15.36TB vSAN

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

**Note**: All modernisation values default to £0, making this section completely optional. Only configure if planning to modernise workloads to native Azure services.

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

**Purpose**: Capture one-time migration investment costs and partner funding.

#### One-Time Migration Costs

- **Assessment & Planning (£)** - Discovery, workshops, architecture design
- **Professional Services (£)** - Microsoft/partner services for migration execution
- **Downtime/Business Impact (£)** - Cost of business disruption during migration
- **Service Transition Cost (£)** - Optional costs for service transition and operational readiness
- **Contingency (%)** - Buffer for unexpected costs (typically 10-20%)

#### Cloud Partner Funding & Incentives

- **Microsoft Partner Migration Funding (£)** - Migration funding provided by Microsoft to qualified partners (typically £10,000-£50,000+)
- **Azure Consumption Credits (£)** - Azure credits to offset initial consumption costs (often £5,000-£25,000)
- **Additional Partner Incentives (£)** - Other partner incentives such as go-to-market funding and marketing co-op (default £0)

**Formulas**:
```
Base Migration Costs = Assessment + Professional Services + Downtime + Service Transition
Gross Migration Investment = (Base Migration Costs × (1 + Contingency%)) + Modernisation Investment
Total Partner Funding = Migration Funding + Azure Credits + Additional Incentives
Net Migration Investment = Max(0, Gross Investment - Partner Funding)
```

#### Migration Timeline

- **Migration Timeline (Months)** - Time to complete initial AVS migration

### 5. Documentation Tab

**Purpose**: Comprehensive explanation of calculation methodology, formulas, and assumptions.

#### Core Financial Formulas

**Return on Investment (ROI)**:
```
ROI = [(Total Savings - Total Investment) / Total Investment] × 100

Where:
- Total Savings = Sum of annual cost savings over analysis period
- Total Investment = Net migration costs after partner funding
```

**Payback Period**:
```
Payback Period = Time when Cumulative Savings ≥ Total Investment
Simple calculation showing when investment will be recovered through cost savings
```

**Total Cost Savings**:
```
Total Savings = Σ(t=1 to n) [Annual Savings in Year t]
Sum of all cost savings over analysis period, accounting for growth and modernisation
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

**Purpose**: Configure financial analysis parameters and display comprehensive financial analysis results and breakdowns.

#### Financial Analysis Parameters

- **Analysis Period (Years)** - Time horizon for ROI analysis (typically 3-5 years)
- **Annual Growth Rate (%)** - Expected IT cost inflation (typically 3-5%)
- **VMware License Inflation (%)** - Annual VMware license cost increases if staying on-premises (typically 5-15% due to Broadcom acquisition)

#### Key Metrics Displayed

- **Return on Investment (ROI)** - Percentage return on migration investment
- **Payback Period** - Time to recover initial investment through savings
- **Total Cost Savings** - Sum of all cost savings over analysis period
- **Gross Investment** - Total upfront costs before partner funding
- **Partner Funding** - Total funding and incentives received
- **Net Investment** - Actual customer investment after partner funding
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

**Detailed Calculation Breakdown**:
- Step-by-step calculation methodology
- Base cost calculations with method explanations
- Azure VMware Solution cost breakdown with node specifications
- Migration investment calculations including partner funding
- Growth rate applications and VMware license inflation impact
- Complete ROI and payback period calculation formulas

## Key Assumptions

1. **Fixed Cost Method**: Hardware represents 50% of total costs, VMware licensing represents 20%
2. **Staff Reduction**: 30% reduction in staff costs with Azure (breakdown method)
3. **Growth Rates**: General inflation applied to infrastructure and operational costs
4. **VMware License Inflation**: Higher inflation rate applied specifically to VMware licensing costs (typically 5-15% annually)
5. **Hardware Refresh**: Occurs when equipment reaches refresh cycle age
6. **Modernisation**: Savings begin after modernisation timeline
7. **Currency**: All costs in GBP (£)

## Limitations

- Does not include intangible benefits (agility, innovation, scalability)
- Azure pricing is estimated and may vary by region and contract terms
- Assumes steady-state operations after migration completion
- Does not account for business disruption during migration
- Hardware refresh timing assumes uniform equipment age

## Usage Instructions

1. **Start with Current Environment**: Choose cost calculation method and enter baseline costs
2. **Configure Azure Solution**: Size AVS environment and select node type and pricing options
3. **Plan Modernisation (Optional)**: Identify workloads for native Azure services (all defaults to £0)
4. **Estimate Migration Costs**: Focus on core costs - assessment, professional services, downtime, and optional service transition
5. **Review Documentation**: Understand methodology and assumptions
6. **Set Analysis Parameters**: Configure financial analysis parameters (analysis period, growth rate, VMware license inflation)
7. **Calculate ROI**: Generate comprehensive financial analysis

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

All formulas follow practical IT investment analysis principles:
- ROI calculation follows standard investment analysis methodology
- Payback period uses simple cumulative cash flows for clarity
- Growth rates applied using compound interest formulas
- VMware license inflation accounts for real-world Broadcom pricing changes
- Detailed calculation breakdowns provide full transparency
- Simplified approach focuses on practical migration decisions

## Support and Maintenance

This calculator provides a framework for migration cost analysis. Users should:
- Validate Azure pricing with current Microsoft pricing sheets
- Adjust assumptions based on specific organizational factors
- Consult with Azure specialists for complex migration scenarios
- Update calculations as business requirements change 