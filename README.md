# Incident Management System
### Multi-Tenant Real-Time Reporting & Advanced Analytics Platform

This project is a cloud-based Incident Management System built using:

- AWS RDS (MySQL)
- ASP.NET Core MVC
- Angular
- AWS Infrastructure

The platform enables real-time incident reporting, classification, tracking, and analytics across organizations.

I participated in the overall system architecture design and independently designed and implemented the **End-to-End Analytics Dashboard**.

---

## 📌 System Overview

The system is designed to:

- Capture incidents in real time (e.g., COVID, shooting, flu, threat cases)
- Classify incidents using hierarchical Issue Types
- Enforce role-based access control (RBAC)
- Notify relevant stakeholders immediately
- Track incident lifecycle and resolution status
- Provide multi-dimensional analytics dashboards

Each incident is:

1. Reported and classified (IssueType hierarchy)
2. Managed based on Role and Organization
3. Tracked through status changes
4. Included in aggregated analytics views

---

## 🏗 Architecture

### Infrastructure
- AWS RDS (MySQL)
- Multi-tenant architecture (orgId-based separation)
- Cloud deployment

### Backend
- ASP.NET Core MVC
- RESTful API layer
- Role-based authorization
- Incident lifecycle management

### Frontend
- Angular
- Role-aware UI rendering
- Interactive dashboards
- Map-based visualization

### [Data Architecture](data-engineering.md)
---

## 🧩 Core Domain Model

Main entities:

- Organization (Multi-tenant root)
- User / Role / UserType
- Incident (Core entity)
- IssueType (Hierarchical classification)
- Site / Location
- SelfReport

Supports:

- Hierarchical IssueType (parent-child structure)
- Multi-role governance
- Organization-level isolation
- Status-based incident tracking

---

# 📊 Production Analytics Dashboard (My Ownership)

I independently designed and implemented the entire analytics layer.

### Data Flow

```
MySQL (Analytics Views)
        ↓
ASP.NET Core REST API
        ↓
Angular Dashboard
        ↓
Interactive Graph & Map Visualization
```

---

## 🔎 Analytics Capabilities

### 1️⃣ Case Per Issue Type
- Time range filtering
- IssueType aggregation
- Bar + Donut visualization
- Total case counters

**Purpose:** Identify dominant incident categories and trend shifts.

---

### 2️⃣ Case Per Location
- Site-level aggregation
- IssueType + Time filtering
- Comparative distribution

**Purpose:** Detect high-risk locations and spatial concentration.

---

### 3️⃣ Case Per Reporter Info
- Reporter-based aggregation
- Behavioral pattern visibility
- Role-aware filtering

**Purpose:** Analyze reporting patterns and system signals.

---

### 4️⃣ Risk / Threat Assessment Analytics
- Threat level segmentation (Low / Medium / High)
- Temporal distribution analysis
- Risk trend visualization

**Purpose:** Monitor severity escalation patterns.

---

### 5️⃣ Case Trend Analysis
- Monthly / quarterly aggregation
- Status-based filtering (New / In Progress / Closed)
- Longitudinal trend tracking

**Purpose:** Evaluate operational workload and resolution velocity.

---

### 6️⃣ Spatial Intelligence (Map Visualization)
- Interactive map
- Clustered incident markers
- Top 10 affected sites
- Geographic distribution analytics

**Purpose:** Enable geographic risk monitoring and resource planning.

---

# 🛠 Database-Level Analytics Engineering

All analytics are powered by optimized MySQL Views designed for:

- GROUP BY aggregations
- Indexed date filtering
- Conditional aggregation
- orgId-based partition logic
- Pre-aggregated summary datasets

Design goals:

- Minimize API-level computation
- Reduce dashboard latency
- Support multi-dimensional filtering
- Maintain scalability

---

# 🔐 Role-Based Analytics

Analytics layer enforces:

- Organization isolation
- Role-based access control
- Sensitive data filtering
- Reporter visibility rules

---

# 🎯 My Contribution

### System-Level Participation
- Contributed to core domain modeling
- Participated in Incident / IssueType schema design
- Collaborated on RBAC integration

### Sole Ownership (Analytics Layer)
- Designed analytics data model
- Created DB-level analytic views
- Implemented REST analytics APIs
- Built Angular dashboard UI
- Implemented filtering & drill-down logic
- Integrated map-based visualization
- Maintain and evolve analytics architecture

---

# 🚀 Engineering Highlights

- Multi-tenant SaaS architecture
- Hierarchical IssueType modeling
- Real-time operational tracking
- Database-driven analytics optimization
- Spatial data visualization
- Role-aware dashboard exposure
- Full-stack analytics pipeline ownership

---

# 📈 Project Impact

This system enables organizations to:

- Rapidly report critical incidents
- Monitor risk distribution in real time
- Track resolution workflows
- Analyze historical trends
- Improve response efficiency through data visibility

The analytics dashboard transforms operational incident data into actionable intelligence.
