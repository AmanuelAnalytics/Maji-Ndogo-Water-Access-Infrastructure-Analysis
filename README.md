# Maji Ndogo Water Access & Infrastructure Analysis

## About the Data

This project is based on the `md_water_services` database, a comprehensive dataset that captures the state of water access, quality, and infrastructure across multiple towns and provinces. It includes over **60,000** unique water source records and draws from structured field visits, surveyor assessments, and citizen-reported feedback.

### Key Tables in the Dataset

- **`location`** – Geographic and administrative information (town, province, area type: Urban/Rural)
- **`water_source`** – Type of water source (e.g., well, in-home tap, shared tap, river) and population served
- **`water_quality`** – Surveyor-assigned and auditor-verified water quality ratings
- **`visits`** – Log of site visits, including visitor identity, visit frequency, and queue duration
- **`auditor_report`** – Contains citizen feedback and independently assessed water quality
- **`employee`** – Field workers tasked with data collection
- **`well_pollution`** – Types of pollution (e.g., chemical, biological) found in wells
- **`global_water_access`** – Country-level statistics for comparative context

> 📌 **Note:** Each `tap_in_home` record represents a **cluster of ~150 households**, not a single unit.

---

## Identifying and Resolving Critical Data Errors

### 🔧 Broken Table Relationships

- Corrected a **many-to-one** relationship between `visits` and `water_quality` to enforce a **one-to-one** link, preserving the integrity of survey design.

### 🧪 Misclassified Water Quality Labels

- **Issue:** Some sources marked as "Clean" had dangerous biological contamination.
- **Fixes:**
  - Renamed misleading `Description` values (e.g., `"Clean Bacteria: E. coli"` → `"Bacteria: E. coli"`)
  - Reclassified `Results` as `"Contaminated: Biological"` where contamination exceeded safe thresholds.

---

## 📇 Employee Data Cleanup

### Email Address Standardization
Generated missing emails using:
worker.first_name.last_name@ndogowater.gov

### Phone Number Formatting
Trimmed trailing spaces from `phone_number` values to ensure compatibility with SMS systems.

---

## 🏅 Recognizing Top Field Surveyors

Using `visit` data:
- Identified top 3 field surveyors by visit count
- Retrieved names, emails, and phone numbers
- Sent recognition messages to promote integrity and morale

---

## 🔍 Integrity Check: Audit Findings

Auditors revisited **1,620** water sources and collected community feedback.

### Findings:

- **102 discrepancies** between employee vs. auditor scores
- **4 employees** had significantly higher error rates
- Same 4 employees mentioned in **negative community statements**

> 🔎 **Conclusion:** Strong pattern suggesting misconduct or poor training—recommended for further review.

---

## 💧 Water Source Analysis: Access, Burden & Inequality

### Key Insights:

- **Shared taps**: Serve **43.2%** of the population, with **~2,072 users per tap**
- **Wells**: Most common (17,383) but serve fewer people (~279 each)
- **In-home taps**: 13,121 installed, **45% broken**
- **River use**: Still serves 2.3M people—high health risk

> ⚠️ Serious access inequality—millions rely on unsafe or broken sources.

---

## ⏳ Queue Pressure: Time-Based Access Insights

### Average wait time: **123 minutes**

#### By Day:
- **Saturday:** Worst queues (246 min)
- **Sunday:** Best (82 min)
- **Monday:** Longest weekday (137 min)

#### By Hour:
- **7:00 PM:** Peak time (168 min)
- **11 AM–2 PM:** Least congested (~111 min)

> 🕒 Suggests need for **midday collection campaigns** and **staggered access** solutions.

---

## 🗺️ Mapping Infrastructure: Geographic Access Patterns

### Highlights:

- **Rural areas** have most infrastructure (esp. Akatsi, Kilimani)
- **Wells** dominate, especially in Kilimani (4,774)
- **In-home tap failures** widespread (Amanzi: 2,048 broken)
- **River use** persists in Sokoto, Kilimani, Ilanga
- **Urban gaps**: Djenne, Yaounde, and others are under-resourced

> ⚖️ Infrastructure distribution is **uneven**—rural buildout has not guaranteed reliable access.

---

## ☣️ Contaminated Wells: A Cross-Cutting Risk

- **Kilimani**: 3,731 polluted wells
- **Contamination** spans both urban and rural
- **Key towns** at risk: Harare, Amina, Mrembo, Djenne, Amanzi

> 🛑 **Regular testing and remediation needed**—pollution is widespread and systemic.

---

## ✅ Solutions & Recommendations

### 1. Emergency Water Delivery
- Deploy trucks in high-risk river-reliant towns (e.g., Sokoto)
- Drill wells as sustainable replacements

### 2. Well Decontamination
- Use **UV filters** (biological) + **RO filters** (chemical)
- Conduct **environmental audits** for pollution sources

### 3. Shared Tap Relief
- Deploy tankers during peak times (Saturday PM, Monday AM)
- Install new taps in overloaded towns (e.g., Zuri, Bello)

### 4. Repair In-Home Infrastructure
- Focus on high-density, high-failure areas (e.g., Amina, Zuri)
- Group repairs for efficiency

### 5. Expand In-Home Access
- Invest in towns with stable shared tap usage (e.g., Harare, Asmara)
- Prioritize underserved zones

### 6. Maintenance & Monitoring
- Schedule routine inspections
- Use **SMS/app-based alerts**
- Track service via public dashboards

---

## 📦 Turning Insight into Action: The `project_progress` Table

This table helps field teams take direct action. It includes:

- Address + water source details  
- Recommended fix (e.g., “Install RO filter”)  
- Fields to log progress: status, date, notes  

### Filtering Logic:
- Only includes latest-visited sites (`visit_count = 1`)
- Targets:
  - **Rivers** → Drill wells
  - **Contaminated wells** → Install filters
  - **Overburdened shared taps** → Add new taps based on wait time
  - **Broken in-home taps** → Trigger diagnostics

> 📊 **From data to deployment**—this table empowers real-world impact.

---

## 📝 License

This project is released under the [MIT License](LICENSE). You’re welcome to reuse, modify, or adapt the code and insights with attribution.

---

## ✉️ Contact

For questions, collaboration, or access to additional data layers, feel free to reach out via [GitHub]([https://github.com/](https://github.com/AmanuelAnalytics)) or email.


