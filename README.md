# 🗺️ Zoning Champion Dashboard — Tableau Analytics Portfolio

> **Operational zoning analytics system** for merchant activation, warehouse supply chain mapping, and field sales performance tracking across 7 regional territories in Indonesia.

---

## 📌 Project Overview

This project presents an end-to-end **Zoning Champion Dashboard** built in **Tableau**, designed to support a B2B distribution platform's field operations team in managing merchant zones, monitoring KPI performance, and enabling data-driven decisions at the squad level.

The system integrates merchant master data, warehouse supply chain mapping, baseline benchmarking, and real-time operational field views — all linked across a unified geographic zoning framework.

| Attribute | Detail |
|---|---|
| **Tool** | Tableau |
| **Domain** | Sales Operations / Field Analytics |
| **Scope** | 7 Regions · 40+ Squads · Nationwide (Indonesia) |
| **Role** | Data Analyst |
| **Key Metric Types** | Merchant Activation, GMV, BTOK Traffic, Subscription Status, HVM |

---

## 🧩 Dashboard Architecture

The system is composed of **5 interconnected dashboard layers**, each serving a distinct operational purpose:

```
┌─────────────────────────────────────────────────────┐
│           ZONING CHAMPION DASHBOARD SYSTEM          │
│                                                     │
│  [1] Base Zoning Champion       ← Strategic Setup   │
│         ↓                                           │
│  [2] Warehouse Zone Champion    ← Supply Mapping    │
│         ↓                                           │
│  [3] List Merchant Zoning       ← Master Data       │
│         ↓                                           │
│  [4] Zoning Merchant (Map)      ← Field Operations  │
│         ↓                                           │
│  [5] Increment Base vs Actual   ← Performance Eval  │
└─────────────────────────────────────────────────────┘
```

---

## 📊 Dashboard Breakdown

### 1. Base Zoning Champion
**Purpose:** Establishes the baseline snapshot for each zone before the program runs.

- Displays total supplier count by coverage area (Lokal vs Nasional, Regular vs CBD)
- Tracks baseline Merchant Active and HVM (High Value Merchant) count per squad
- Covers full geographic hierarchy: Provinsi → Kabupaten → Kecamatan → Kelurahan
- Serves as the **benchmark reference** for all subsequent performance comparisons

**Key Columns:** `Region`, `Squad`, `PIC`, `KELURAHAN`, `Total Supplier`, `Merchant Active (Base)`, `Merchant HVM (Base)`

---

### 2. List Warehouse Zone Champion
**Purpose:** Maps which warehouse serves which zone, and which suppliers are assigned per area.

- Breaks down supplier assignment by kelurahan with type classification: `Lokal Regular`, `Nasional CBD`, `Nasional Regular`
- Includes GMV and traffic performance columns per warehouse: `GMV BTOK ALL`, `Traffic BTOK ALL`, `GMV Bundling`, `Traffic Bundling`
- Enables supply chain auditing and coverage gap identification

**Key Columns:** `Region`, `Squad`, `Kelurahan`, `Warehouse`, `Supplier Name`, `Type Supplier`, `GMV BTOK`, `Traffic`

---

### 3. List Merchant Zoning
**Purpose:** Master data registry of all merchants assigned within the zoning system.

- Each merchant is tagged with business category, registration date, geographic zone, and region cluster (CLM)
- Enables coverage validation and onboarding tracking
- Serves as a cross-reference layer for operational and performance dashboards

**Key Columns:** `account_id`, `merchant_id`, `merch_name`, `business_category`, `register_date`, `region (CLM)`, `KABUPATEN`, `KECAMATAN`, `KELURAHAN`

---

### 4. Zoning Merchant (Interactive Map)
**Purpose:** Operational field view for Sales Leaders (SL) to prioritize merchant visits.

- Built on **Mapbox** geographic rendering within Tableau
- Color-coded by merchant type: `Merchant Basic` vs `Subs Active`
- Icon layers for supplier type: `Null`, `Indomarco`, `Lokal Regular`, `Nasional Regular`
- Summary table shows BTOK status (Never BTOK), subscription breakdown (Never Subscribed / Subs Active / Subs Expired), and HVM flag per kelurahan
- Bottom detail table enables merchant-level drill-down with full KPI context

**Key Columns:** `KECAMATAN`, `KELURAHAN`, `Total Merchant Active`, `BTOK Status`, `Subs Status`, `Type Merchant`, `HVM`, `BTOK Traffic`, `Cash GMV`

---

### 5. Resume Increment Zoning — Base vs Actual
**Purpose:** Core performance evaluation dashboard — compares baseline to actual results across all KPI dimensions.

- Percentage delta (▲) columns highlight growth or decline per squad
- Negative values (red) indicate underperforming zones that need immediate intervention
- Covers the full performance funnel from merchant activation through to revenue contribution

**KPIs Tracked:**

| Category | Metrics |
|---|---|
| **Merchant Activation** | Merchant Active ▲, Merchant HVM ▲ |
| **Transaction** | BTOK Traffic ▲, GMV ▲, Cash GMV ▲, Cashless GMV ▲ |
| **Payment Method** | Cash Traffic ▲, Cashless Traffic ▲, Total Traffic ▲ |
| **Subscription** | Never Subscribed ▲, Subs Active ▲, Subs Expired ▲ |

---

## 💡 Business Insights

### Problem Statements Addressed

1. **Low visibility into merchant coverage per zone** — Without a structured zoning system, it was unclear which merchants were active, where they were located, and which warehouse served them. This dashboard creates a clear operational structure.

2. **Difficulty measuring program impact quantitatively** — The Base vs Actual dashboard (dashboards 3 & 5) enables direct comparison between pre-program baseline and post-implementation actuals, giving management clear evidence of whether the zoning program is working.

3. **SL prioritization challenges in the field** — The interactive map dashboard (dashboard 4) helps field SLs visually identify which merchants haven't subscribed, have never placed a BTOK order, or are flagged as HVM — enabling prioritized visit planning.

4. **Data fragmentation across merchant, supplier, and geography** — The five dashboards create a connected data pipeline from Merchant → Zone → Warehouse → Supplier → Performance, consolidating previously siloed data.

5. **Lack of PIC-level accountability** — Every row carries `Squad`, `PIC`, and `Region` identifiers, enabling management to track individual accountabilities and address performance gaps at the person level.

### Key Analytical Findings

- **Merchant activation rates** varied significantly across regions, with some squads showing >50% decline from baseline — indicating either data quality issues or on-ground execution gaps
- **HVM concentration** was uneven, with certain kecamatan carrying disproportionate GMV weight — suggesting priority resource allocation opportunities
- **Never Subscribed merchants** represented a high-opportunity segment visible across multiple zones in the Medan Outer and Surabaya Outer squads
- **Subscription churn** (Subs Expired ▲) was a recurring pattern in Region 6 (Sumatera), highlighting potential for targeted reactivation campaigns
- **Cashless payment adoption** showed upward trends in urban-dense zones while cash remained dominant in peri-urban areas — useful for payment partnership planning

---

## 🛠️ Tools & Tech Stack

| Layer | Tool |
|---|---|
| **Dashboard & Visualization** | Tableau Desktop / Tableau Server |
| **Geographic Mapping** | Mapbox (integrated via Tableau) |
| **Data Source** | Structured relational tables (merchant, warehouse, zone, performance) |
| **Geographic Hierarchy** | Kelurahan → Kecamatan → Kabupaten → Provinsi → Region |

---

## 📁 Repository Structure

```
zoning-champion-dashboard/
│
├── README.md                          ← You are here
│
├── screenshots/
│   ├── 01_base_zoning_champion.png
│   ├── 02_warehouse_zone_champion.png
│   ├── 03_list_merchant_zoning.png
│   ├── 04_zoning_merchant_map.png
│   └── 05_increment_base_vs_actual.png
│
└── docs/
    └── dashboard_overview.md          ← Extended documentation (optional)
```

---

## 🚀 How to Use / Reproduce

1. **Clone this repository**
   ```bash
   git clone https://github.com/YOUR_USERNAME/zoning-champion-dashboard.git
   ```

2. **Open Tableau** and connect to your data source (merchant, warehouse, zone tables)

3. **Follow the dashboard layer sequence:**
   - Start with Base Zoning Champion to establish your baseline
   - Assign warehouses via Warehouse Zone Champion
   - Register merchants in List Merchant Zoning
   - Monitor daily operations via the Zoning Merchant map
   - Review program performance weekly via the Increment dashboard

4. **Filter by Region or Squad** to drill into specific territory performance

---

## 👤 Author

**[Your Name]**
Data Analyst | Sales & Field Operations Analytics

- 📧 your.email@email.com
- 💼 [LinkedIn](https://linkedin.com/in/yourprofile)
- 🐙 [GitHub](https://github.com/yourusername)

---

## 📄 License

This project is for portfolio and educational purposes. Data shown is anonymized/representative.

---

*Built with Tableau · Powered by field operations data · Designed for actionable decision-making*
