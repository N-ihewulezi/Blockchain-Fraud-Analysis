# Uncovering Fraud Networks in a Blockchain Payment System

**Author:** Nkechi Ihewulezi  
**Dataset:** Elliptic Bitcoin Transaction Dataset  
**Tools:** Python · NetworkX · Plotly · D3.js · Pandas · PyVis

---

## Project Overview

A regulatory body raised concerns about a cluster of Bitcoin transactions 
linked to potential illicit activity. This project analyses 203,769 
real-world Bitcoin transactions using graph analytics to map the network, 
identify structural hubs, detect suspicious flow patterns, and produce a 
defensible compliance report.

---

## Key Findings

| Finding | Detail |
|---|---|
| Subgraph analysed | 8,021 nodes · 9,428 edges |
| Illicit nodes identified | 127 confirmed |
| Fan-out pattern flags | 6 nodes (up to 472 destinations in one step) |
| Layering pattern flags | 2 nodes (94–98 sources → 15 destinations) |
| Dual-pattern nodes | 2 (highest priority for SAR filing) |

> Transaction 2984918 received funds from a single source and 
> dispersed to **472 destinations simultaneously** — the most 
> extreme structuring pattern in the dataset.

---

## Network Visualisation

![Network Graph](visuals/network_visualization.png)

*Gold nodes = top 10 by composite risk score · 
Red = illicit · Green = licit · Grey = unknown*

---

## Dashboard Preview

![Dashboard](visuals/dashboard_preview.png)

**[View Interactive Dashboard](dashboard/blockchain_fraud_dashboard.html)**  
*(Download and open in any browser — no server required)*

---

## Methodology

### 1. Data Preparation
- Merged 3 source files (203,769 transactions, 234,355 edges)
- Zero missing values, zero duplicates, zero orphaned edges
- Retained unknown-labelled nodes — structural position is itself 
  an analytical signal

### 2. Network Construction
- Built a weighted directed graph using NetworkX
- Identified 49 weakly connected components
- Combined betweenness centrality (as specified) with degree 
  centrality supplementation to produce a robust 8,021-node subgraph
- Computed in-degree, out-degree, betweenness, and PageRank 
  for every node

### 3. Composite Risk Score
Risk = 0.35 × out-degree + 0.25 × in-degree +
0.25 × PageRank  + 0.15 × betweenness
Weights reflect compliance priorities — fan-out behaviour 
carries the highest signal for structuring detection.

### 4. Fraud Pattern Detection
- **Layering:** nodes with 5+ sources AND 5+ destinations
- **Fan-out:** nodes with 15+ unique destinations
- All flagged nodes cross-referenced against class labels

### 5. Deliverables
- Jupyter Notebook (fully executed)
- Interactive HTML dashboard
- Compliance report (non-technical, NFIU-ready)
- Cleaned dataset

---

## Dataset

The Elliptic Bitcoin Transaction Dataset is a real-world graph 
dataset used in published academic research.  
Available on Kaggle: [Elliptic Data Set](https://www.kaggle.com/ellipticco/elliptic-data-set)

---

## Repository Structure
├── notebooks/     # Fully executed Jupyter notebook
├── dashboard/     # Self-contained interactive HTML dashboard
├── reports/       # Compliance report PDF
├── data/processed/# Cleaned and pattern CSV outputs
└── visuals/       # Network graph and dashboard screenshots

---

## Skills Demonstrated

`Graph Analytics` `Fraud Detection` `NetworkX` `Plotly` 
`D3.js` `Compliance Reporting` `Python` `Data Visualisation` 
`AML Typologies` `Bitcoin / Blockchain`
