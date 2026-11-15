# Awesome-Manufacturing-Execution-Production-Planning

# Awesome Manufacturing Execution & Production Planning

> A curated list of top Manufacturing Execution and Production Planning platforms — both SaaS/Hosted commercial MES/ERP solutions and open-source alternatives for scheduling work orders, tracking shop floor execution, and managing production inventory.
> 🌟 Star this repo if you find it useful! 🌟

---

## 📋 Table of Contents

- [SaaS / Hosted Platforms](#-saas--hosted-platforms)
  - [Katana Cloud Manufacturing](#katana-cloud-manufacturing)
  - [Plex Systems (Rockwell Automation)](#plex-systems-rockwell-automation)
  - [Siemens Opcenter](#siemens-opcenter)
  - [SAP Digital Manufacturing](#sap-digital-manufacturing)
  - [DELMIA Apriso](#delmia-apriso)
  - [MRPeasy](#mrpeasy)
- [Open-Source Software](#-open-source-software)
  - [FactorySemantics MES](#factorysemantics-mes)
  - [Lekin](#lekin)
  - [Open MRP](#open-mrp)

---

## 🟦 SaaS / Hosted Platforms

Commercial, cloud-hosted Manufacturing Execution and Production Planning platforms. These are not open-source but are included as reference points for feature comparison.

### Katana Cloud Manufacturing
**Type:** SMB-focused manufacturing and inventory management
Katana provides a lighter-weight alternative to full ERP manufacturing modules, with bill of materials building, production operations, work order scheduling, and real-time material availability updates . Its **Shop Floor App** gives operators a task-level view of what to make next and lets them log progress directly from production . It connects natively to QuickBooks Online and Xero for accounting, and to Shopify, Amazon, and WooCommerce for sales channels . **Trade-off:** It is not a full financial ERP—it acts as a manufacturing and inventory layer alongside existing accounting software, with ERP connectivity to NetSuite and similar systems requiring third-party integration platforms . Pricing starts around $299/month .
**Best for:** Small to mid-sized manufacturers wanting a fast-to-adopt production and inventory layer on top of existing accounting software, accepting the narrower financial scope.

### Plex Systems (Rockwell Automation)
**Type:** Cloud MES/MOM with ERP connectivity
Plex provides a cloud-native Manufacturing Execution System with a unified platform covering production finite scheduling, closed-loop quality management, inventory tracking, and real-time machine data collection . The **finite scheduling engine** determines which jobs go to which work centers based on resource availability . It is designed to connect the plant floor with corporate ERP, dispatching plan changes directly to the floor scheduler . Plex reports 8B+ transactions per day and a 96% gross renewal rate, and was named a Leader in the Gartner Magic Quadrant for MES . **Trade-off:** It is an enterprise platform with pricing to match—starting around $3,000/month .
**Best for:** Mid-market to enterprise manufacturers needing a unified cloud MES with strong ERP integration and finite scheduling.

### Siemens Opcenter
**Type:** Enterprise MES with digital twin integration
Siemens Opcenter Execution provides comprehensive MES capabilities including optimized sequencing, resource allocation, production tracking with forward/backward traceability, equipment and personnel performance tracking, and real-time performance analysis . It was named a Leader in the IDC MarketScape for Manufacturing Execution Systems 2024-2025 . It integrates with the broader Siemens digital enterprise portfolio, providing a digital twin of the plant floor . **Trade-off:** It is a heavy enterprise platform (one open-source project notes that Opcenter represents "thousands of engineer-years" of development) with implementation complexity to match .
**Best for:** Large enterprises already in the Siemens ecosystem needing deep MES capabilities and digital twin integration.

### SAP Digital Manufacturing
**Type:** Cloud MOM on SAP BTP
SAP Digital Manufacturing is a Manufacturing Operations Management platform built on SAP Business Technology Platform, with AI-driven KPIs, closed-loop scheduling, resource orchestration, and production execution capabilities . It integrates with SAP SuccessFactors for skills and certification tracking, and with SAP Analytics Cloud for self-service reporting . It supports S88 and S95 production models .
**Best for:** SAP-centric enterprises wanting MOM capabilities natively integrated with the SAP ecosystem.

### DELMIA Apriso
**Type:** Global MOM with low-code flexibility
DELMIA Apriso unifies production, quality, maintenance, inventory, and personnel management in a single platform, with a **low-code environment** that allows process adaptation without extensive custom coding . It provides real-time visibility across multi-site manufacturing, with traceability from raw materials to finished goods. The virtual twin technology allows simulation of production scenarios. Many customers report going live in under 90 days .
**Best for:** Multi-site manufacturers needing global standardization with local flexibility, particularly in aerospace, life sciences, and F&B.

### MRPeasy
**Type:** Cloud MRP/MES for small manufacturers
MRPeasy provides production planning, material requirements planning (MRP I and MRP II with finite capacity), shop floor reporting, and inventory control in a cloud platform accessible via web and iOS/Android apps . It includes Gantt charts, drag-and-drop rescheduling, BOM management with multi-level support, and standard accounting modules . It is ISO 27001 certified and integrates with QuickBooks, Shopify, and HubSpot . **Trade-off:** It is positioned for smaller manufacturers—the feature depth is less than enterprise MES platforms.
**Best for:** Small manufacturers wanting comprehensive MRP and shop floor reporting at an accessible price point.

---

## 🟩 Open-Source Software

Self-hosted, community-driven Manufacturing Execution and Production Planning tools. The open-source ecosystem is **nascent and fragmented**, with most projects either early-stage or focused on specific layers of the production planning stack.

### FactorySemantics MES
**Stack:** Python / SQLite / OPC UA / MCP | **License:** Apache-2.0
FactorySemantics MES is an open-source Manufacturing Execution System built on a **kernel + modules** architecture, with a focus on standards compliance and agent-native operation . Key characteristics:
- **Production core**: Production orders and routings, PLC/OPC UA/Kepware connectivity, downtime tracking and OEE 
- **Quality module**: Inspections, holds, NCR, SPC, gauge and calibration management 
- **Scheduling**: Finite-capacity scheduling 
- **Maintenance**: Preventive maintenance 
- **Traceability**: Genealogy and traceability 
- **ERP integration**: ERPNext, B2MML-flavoured file, REST 
- **Agent-native**: Every function callable via REST and MCP, with read tools free and command tools supporting `dry_run` and approval gates. Every action lands in an append-only audit spine 
- **Runs anywhere**: SQLite on a laptop → Docker Compose in a plant → fleet of nodes with a console. Operator UI is plain HTML/JS with no build step 

The project is explicitly honest about scope: "Opcenter is thousands of engineer-years. The path here is not cloning it — it's shipping the 20% of each module that covers 80% of a small-to-mid plant, correctly and honestly, module by module, with agents as the force multiplier" . It uses ISA-95 nouns, PackML for machine states, and ISO 22400 for KPIs, with B2MML only at the ERP border .
**Best for:** Small to mid-sized plants wanting a self-hosted MES with standards-based architecture, OPC UA connectivity, and AI agent integration via MCP, accepting the early-stage module depth.

### Lekin
**Stack:** Python | **License:** Open Source (PyPI)
Lekin is a **flexible job shop scheduler library** named after the classic scheduling system, positioned as a core function in Advanced Planning and Scheduler (APS) for optimizing material and capacity allocation . Key characteristics:
- **Multiple solving strategies**: Continuous Time Planning (CTP), Construction Heuristics, Meta-heuristics (Genetic Algorithm, Simulated Annealing), Reinforcement Learning, and Operations Research methods 
- **Extensible architecture**: Custom solvers and constraints via `BaseConstraint` subclassing 
- **Performance metrics and visualization**: `scheduler.draw()` generates Gantt-style output 
- **Real-world integration**: Designed to integrate with MES to deploy production plans on the shop floor, and with ERP for demand/inventory/production exchange 

**Important status:** The package documentation explicitly states **"DEVELOPING - NOT FINISHED AND DON'T USE IT NOW!"** . It is a research and demo tool rather than a production-ready scheduler.
**Best for:** Researchers and developers exploring job shop scheduling algorithms, not for production deployment in its current state.

### Open MRP
**Stack:** Go / MySQL / PostgreSQL | **License:** Open Source (Go package)
Open MRP is an open-source Material Requirements Planning system with a **core service** (MySQL) and an **agent service** (PostgreSQL), with Stripe integration for subscription billing in the seed data . Key characteristics:
- **Local development**: `make local-db` spins up both databases with seed data and optional Stripe test subscription 
- **Kubernetes-ready**: Tilt/minikube configuration provided 
- **Agent tooling**: Agents can invoke api-gateway endpoints flagged `AgentTool: true` via an internal listener 
- **Pattern-based architecture**: Documented patterns in `AGENTS.md` and `docs/patterns/` are the normative spec for the codebase 

**Trade-off:** The available documentation focuses on development setup and architecture rather than end-user manufacturing features—it appears to be an early-stage project building toward a full MRP system.
**Best for:** Developers wanting a Go-based MRP foundation with agent tooling, accepting early-stage feature maturity.

---

## 📊 Comparison at a Glance

| Software | License | Stack | Production Orders | Finite Scheduling | OEE/Downtime | Self-Hosted | Best For |
|----------|---------|-------|-------------------|-------------------|--------------|-------------|----------|
| **Katana** | Proprietary | Cloud | ✅ | (Check) | ❌ | ❌ | SMB manufacturing layer |
| **Plex** | Proprietary | Cloud | ✅ | ✅ | ✅ | ❌ | Enterprise cloud MES |
| **Siemens Opcenter** | Proprietary | On-prem/Cloud | ✅ | ✅ | ✅ | (On-prem) | Large enterprise MES |
| **SAP Digital Manufacturing** | Proprietary | Cloud (BTP) | ✅ | ✅ Closed-loop | ✅ | ❌ | SAP ecosystem MOM |
| **DELMIA Apriso** | Proprietary | Cloud/On-prem | ✅ | (Check) | ✅ | (On-prem) | Multi-site global MOM |
| **MRPeasy** | Proprietary | Cloud | ✅ | ✅ Finite capacity | (Check) | ❌ | Small manufacturer MRP/MES |
| **FactorySemantics** | Apache-2.0 | Python/SQLite | ✅ | ✅ | ✅ | ✅ | Standards-based OSS MES |
| **Lekin** | Open Source | Python | ❌ (Scheduler) | ✅ Algorithms | ❌ | ✅ (Library) | Job shop scheduling research |

---

## 🤝 Contributing

Contributions are welcome! If you know of an open-source Manufacturing Execution or Production Planning tool that should be listed here, please open a pull request with:

- Project name and URL
- Brief description (1–2 sentences)
- Stack and license
- Why it stands out

Please ensure the project is actively maintained (releases within the last 12 months) and genuinely open-source.

**Note on the open-source ecosystem:** The open-source landscape for **Manufacturing Execution Systems** is **extremely limited** compared to commercial platforms. **FactorySemantics MES** is the most complete open-source effort, providing a standards-based (ISA-95, PackML, ISO 22400) MES with OPC UA connectivity, OEE tracking, and AI agent integration via MCP, explicitly targeting the 80/20 of small-to-mid plant needs rather than cloning Opcenter . **Lekin** addresses the scheduling algorithm layer but is explicitly not production-ready . **Open MRP** is an early-stage Go-based MRP foundation with agent tooling . No open-source project replicates the full breadth of Plex, Opcenter, or DELMIA Apriso—commercial platforms remain the only viable option for enterprise-scale manufacturing execution.

---

## 📄 License

This list is released under CC0 1.0 Universal (Public Domain). The software projects listed retain their respective licenses.

---

⭐ **If this list helped you discover a useful tool, please star the repo!** ⭐
