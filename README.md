# 🥿 SAP S/4HANA MM Implementation Project
### RR Footwear Pvt Ltd (RRPL) — End-to-End Materials Management

![SAP](https://img.shields.io/badge/SAP-S%2F4HANA-0FAAFF?style=for-the-badge&logo=sap&logoColor=white)
![Module](https://img.shields.io/badge/Module-Materials%20Management-green?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-In%20Progress-orange?style=for-the-badge)
![P2P Cycles](https://img.shields.io/badge/P2P%20Cycles-3%20Completed-blue?style=for-the-badge)

---

## 🏢 Company Overview

| Field | Details |
|-------|---------|
| **Company Name** | RR Pvt Ltd |
| **Company Code** | RRPL |
| **Industry** | Footwear Manufacturing & Distribution |
| **Headquarters** | Pathanamthitta, Kerala — 689649 |
| **Currency** | INR (Indian Rupee) |
| **Fiscal Year** | April to March (Indian Standard) |
| **SAP System** | S/4HANA (S4RD14) |

---

## 🏭 Plant Structure

| Plant Code | Plant Name | Location | Specialization |
|-----------|-----------|----------|---------------|
| **RR01** | RR Manufacturing PTA | Pathanamthitta, Kerala | General Footwear — Main Plant |
| **RR02** | RR Manufacturing Kochi | Kochi, Kerala | Specialty Shoes — Secondary Plant |

---

## 📦 Material Master Summary

| Material | Description | Type | UoM | Price (₹) | Plant |
|---------|-------------|------|-----|-----------|-------|
| RRRM001 | Leather Sheets — Upper Material | ROH | M2 | 850 | RR01 & RR02 |
| RRRM002 | Rubber Compound — Sole Material | ROH | KG | 220 | RR01 & RR02 |
| RRRM003 | EVA Foam — Insole Material | ROH | M2 | 180 | RR01 & RR02 |
| RRRM004 | Thread & Adhesive — Stitching | ROH | KG | 95 | RR01 & RR02 |
| RRPM001 | Shoe Box — Standard Packing | VERP | EA | 25 | RR01 & RR02 |
| RRPM002 | Tissue Paper Wrap — Inner Packaging | VERP | EA | 5 | RR01 & RR02 |
| RRPM003 | Poly Bag — Outer Package | VERP | EA | 3 | RR01 & RR02 |
| RRFG001 | Men's Formal Shoes — Black Leather | FERT | PAI | 1,800 | RR01 Only |
| RRFG002 | Women's Sandals — Casual Wear | FERT | PAI | 950 | RR01 Only |
| RRFG003 | Sports Shoes — Running Series | FERT | PAI | 2,400 | RR02 Only |
| RRMRO01 | Cutting Blades — Industrial Grade | HIBE | EA | 45 | RR01 & RR02 |
| RRMRO02 | Machine Oil — Industrial Lubricant | HIBE | LT | 120 | RR01 & RR02 |
| RRMRO03 | Safety Gloves — Industrial PPE | HIBE | PAI | 65 | RR01 & RR02 |
| RRMU001 | Leather Upper — Semi Finished | HALB | EA | 320 | RR01 Only |

> **Total: 14 Unique Materials | RR01: 13 Materials | RR02: 11 Materials**

---

## 🏪 Vendor Master

| Vendor Code | Vendor Name | Location | Materials Supplied |
|------------|------------|----------|-------------------|
| RRV001 | Kerala Leather Suppliers | Kannur, Kerala | RRRM001 |
| RRV002 | South Indian Rubber Co | — | RRRM002 |
| RRV003 | EVA Foam Industries | Coimbatore | RRRM003 |
| RRV004 | Thread & Adhesive Suppliers | — | RRRM004 |
| RRV005 | Packaging Suppliers | — | RRPM001, RRPM002, RRPM003 |
| RRV006 | Leather Upper Subcon | — | RRMU001 |
| RRV007 | Industrial Tools India | Bangalore | RRMRO01, RRMRO03 |
| RRV008 | Industrial Lubricants Co | — | RRMRO02 |
| RRV009 | Kerala Rubber Suppliers | Kottayam, Kerala | RRRM002 (RFQ Vendor) |

---

## 🔄 Procure-to-Pay (P2P) Cycles Completed

### ✅ Cycle 1 — Basic P2P (Plant RR01)

| Step | T-Code | Document | Details |
|------|--------|---------|---------|
| Purchase Requisition | ME51N | PR 102 | RRRM001, 100 M2, RR01 |
| Purchase Order | ME21N | **PO 102** | RRV001 — Kerala Leather Suppliers |
| Goods Receipt | MIGO | **Mat Doc 700198** | 100 M2, RM01, Mvt Type 101 |
| Invoice Verification | MIRO | **Invoice 5105600827** | ₹83,300 INR |

---

### ✅ Cycle 2 — Basic P2P with Source Determination (Plant RR02)

| Step | T-Code | Document | Details |
|------|--------|---------|---------|
| Purchase Requisition | ME52N | PR 102 | RRRM001, 100 M2, RR02 — Source Det. |
| Purchase Order | ME21N | **PO 104** | RRV001 — Kerala Leather Suppliers |
| Goods Receipt | MIGO | **Mat Doc 700204** | 100 M2, RM02, Kochi Plant |
| Invoice Verification | MIRO | **Invoice 5105600828** | ₹85,000 INR |

---

### ✅ Cycle 3 — P2P with RFQ & Quotation (Plant RR01)

| Step | T-Code | Document | Details |
|------|--------|---------|---------|
| Purchase Requisition | ME51N | PR | RRRM002, 200 KG, RR01 |
| RFQ — Vendor 1 | ME41 | **RFQ 7000000555** | Sent to RRV002 |
| RFQ — Vendor 2 | ME41 | **RFQ 7000000556** | Sent to RRV009 |
| Maintain Quotations | ME47 | Both RFQs | RRV002: ₹220/KG \| RRV009: ₹210/KG |
| Price Comparison | ME49 | Comparison List | **RRV009 — Rank 1 @ 98% (WINNER)** |
| Reject Quotation | ME47 | RFQ 7000000555 | RRV002 Rejected ❌ |
| Purchase Order | ME21N | **PO 105** | RRV009 — Kerala Rubber Suppliers |
| Goods Receipt | MIGO | **Mat Doc 700206** | 200 KG, RM01, Mvt Type 101 |
| Invoice Verification | MIRO | **Invoice 5105600829** | ₹42,000 INR |

---

## ⚙️ Enterprise Structure Configuration

```
RRPL (Company Code)
├── Controlling Area: RRPL
├── Tax Procedure: RRTX (Tax Code R0 — 5% Input Tax)
├── Purchasing Org: RRPO (RR Central Org)
│   ├── Purchasing Group: RR1 (RR Raw Mat Buyer)
│   └── Purchasing Group: RR2 (RR Pkg Consumables Buyer)
├── Plant: RR01 (RR Manufacturing Pathanamthitta)
│   ├── Storage Location: RM01 — Raw Material Store
│   ├── Storage Location: FG01 — Finished Goods Store
│   └── Storage Location: SC01 — Scrap Store
└── Plant: RR02 (RR Manufacturing Kochi)
    ├── Storage Location: RM02 — Raw Material Store
    └── Storage Location: FG02 — Finished Goods Store
```

---

## 🔧 T-Codes Reference

| T-Code | Description | Category |
|--------|-------------|----------|
| SPRO | SAP Configuration | Basis |
| MM01 | Create Material Master | Master Data |
| BP | Business Partner / Vendor Creation | Master Data |
| ME11 | Create Purchase Info Record | Master Data |
| ME01 | Maintain Source List | Master Data |
| ME51N | Create Purchase Requisition | P2P |
| ME21N | Create Purchase Order | P2P |
| ME41 | Create Request for Quotation | P2P - RFQ |
| ME47 | Maintain Quotation | P2P - RFQ |
| ME49 | Price Comparison | P2P - RFQ |
| MIGO | Goods Receipt | P2P |
| MIRO | Enter Incoming Invoice | P2P |
| MMBE | Stock Overview | Reporting |
| MB51 | Material Document List | Reporting |
| ME2M | Purchase Orders by Material | Reporting |
| ME23N | Display Purchase Order | Reporting |

---

## 📁 Repository Structure

```
sap-mm-s4hana_implementation-project/
│
├── 📄 README.md
├── 📄 LICENSE
│
├── 📂 Documentation/
│   └── RR_Footwear_SAP_MM_Project.docx    ← Full project document with screenshots
│
├── 📂 Master_Data/
│   ├── Material_Master.xlsx
│   ├── Vendor_Master.xlsx
│   ├── PIR.xlsx
│   └── Source_List.xlsx
│
└── 📂 Project_Plan/
    └── basic.xlsx
```

---

## 🗺️ Project Roadmap

- [x] Enterprise Structure Configuration
- [x] Material Ledger Configuration
- [x] Tax Procedure & Tax Code
- [x] Material Master Creation (14 Materials)
- [x] Vendor / BP Master Creation (9 Vendors)
- [x] Purchase Info Records (PIR)
- [x] Source List Configuration
- [x] P2P Cycle 1 — Basic (RR01)
- [x] P2P Cycle 2 — Basic with Source Determination (RR02)
- [x] P2P Cycle 3 — RFQ & Quotation Process
- [ ] P2P with Consignment Process
- [ ] P2P with Subcontracting
- [ ] Stock Transfer (RR01 → RR02)
- [ ] Physical Inventory
- [ ] Reporting & Analytics

---

## 🛠️ Tech Stack

![SAP S/4HANA](https://img.shields.io/badge/SAP%20S%2F4HANA-2023-0FAAFF?style=flat-square&logo=sap)
![Module](https://img.shields.io/badge/MM-Materials%20Management-brightgreen?style=flat-square)
![FI](https://img.shields.io/badge/FI-Financial%20Accounting-blue?style=flat-square)
![CO](https://img.shields.io/badge/CO-Controlling-orange?style=flat-square)

---

## 👤 Author

**Rahul R Nair**
- GitHub: [@rahulrnair862](https://github.com/rahulrnair862)
- Project: SAP S/4HANA MM Implementation

---

> *This project is for learning and portfolio purposes — demonstrating end-to-end SAP MM implementation skills.*
