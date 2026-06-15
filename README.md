# 🚚 Delivery ETA Intelligence Dashboard

## Overview

Delivery ETA Intelligence Dashboard is an end-to-end logistics analytics and machine learning platform designed to improve delivery time prediction, identify network bottlenecks, analyze transportation strategies, and leverage graph-based intelligence for logistics optimization.

The project combines:

* Machine Learning for ETA prediction
* Network Science for logistics graph analysis
* Business Analytics for operational decision-making
* Graph Embeddings (Node2Vec) for graph-enhanced ETA prediction
* Interactive Streamlit Dashboard for visualization and monitoring

---

## Problem Statement

Logistics operations often face:

* Inaccurate ETA predictions
* Bottleneck hubs causing network congestion
* Delayed corridors impacting SLA compliance
* Inefficient transportation mode selection
* Limited visibility into network-wide performance

This project addresses these challenges using predictive analytics and graph intelligence.

---

## Dataset

The dataset contains shipment-level information including:

* Source Hub
* Destination Hub
* Actual Delivery Time
* OSRM Estimated Time
* Distance Information
* Corridor Information
* Transportation Type (FTL / Carting)
* Operational Timestamps

After feature engineering, the dataset contains:

* Hub-level features
* Corridor-level features
* Historical delay metrics
* Transportation features
* Graph embedding features

---

# Project Architecture

```text
Raw Logistics Data
        │
        ▼
Data Cleaning & Quality Checks
        │
        ▼
Feature Engineering
        │
        ▼
Network Graph Construction
        │
        ▼
Network Analytics & Bottleneck Detection
        │
        ├────────────► FTL vs Carting Framework
        │
        ├────────────► ETA Prediction Models
        │
        └────────────► Node2Vec Graph Embeddings
                                │
                                ▼
                    Graph-Enhanced ETA Prediction
                                │
                                ▼
                     Streamlit Intelligence Dashboard
```

---

# Project Structure

```text
delivery-eta-intelligence/

├── data/
│   ├── raw/
│   └── processed/
│       ├── delivery_data_clean.csv
│       ├── delivery_data_features.csv
│       └── delivery_data_node2vec.csv
│
├── models/
│   ├── final_eta_model.pkl
│   └── label_encoders.pkl
│
├── notebooks/
│   ├── 01_eda_and_quality_checks.ipynb
│   ├── 02_eda_feature_engineering.ipynb
│   ├── 03_model_building.ipynb
│   ├── 04_model_selection_and_final_model.ipynb
│   ├── 05_network_analytics_and_dashboard_prep.ipynb
│   ├── 06_network_graph_analytics.ipynb
│   ├── 07_ftl_vs_carting_decision_framework.ipynb
│   ├── 08_graph_enhanced_eta_model.ipynb
│   └── 09_node2vec_graph_enhanced_eta.ipynb
│
├── reports/
│   ├── bottleneck_corridors.csv
│   ├── degree_centrality_hubs.csv
│   ├── betweenness_centrality_hubs.csv
│   ├── delay_hotspots.csv
│   ├── hub_delay_hotspots.csv
│   ├── model_comparison.csv
│   ├── network_summary.csv
│   ├── top_source_hubs.csv
│   ├── top_destination_hubs.csv
│   ├── ftl_vs_carting_summary.csv
│   └── ftl_carting_decision_framework.csv
│
├── dashboard/
│   └── app.py
│
├── README.md
└── requirements.txt
```

---

# Feature Engineering

Key engineered features include:

* Corridor Volume
* Source Hub Volume
* Destination Hub Volume
* Historical Corridor Delay
* Historical Delay Ratio
* Trip Segments
* Trip Total Distance
* Average Trip Speed
* Weekend Indicator
* Route Type
* Corridor-Level Aggregations

---

# Network Analytics

A directed logistics graph was constructed where:

* Nodes represent logistics hubs
* Edges represent shipment corridors
* Edge weights represent corridor traffic and delays

### Network Statistics

| Metric          | Value |
| --------------- | ----- |
| Total Hubs      | 1657  |
| Total Corridors | 2783  |

### Network Analysis Performed

* Degree Centrality
* Betweenness Centrality
* Bottleneck Detection
* Delay Hotspot Analysis
* Hub Ranking

---

# Bottleneck Analytics

The system identifies:

* High-risk hubs
* Critical network chokepoints
* Delay-prone corridors
* High SLA-risk regions

Outputs:

* Top Bottleneck Corridors
* Delay Hotspots
* High Betweenness Hubs

---

# ETA Prediction Models

Models evaluated:

* Linear Regression
* Random Forest
* XGBoost

Evaluation Metrics:

* MAE
* RMSE
* R² Score

Best traditional model:

**XGBoost**

---

# Graph-Enhanced ETA Prediction

To capture network structure information, Node2Vec embeddings were generated using the logistics graph.

### Graph Configuration

* Nodes: 1657
* Corridors: 2783
* Embedding Dimensions: 32
* Source Embeddings: 32 Features
* Destination Embeddings: 32 Features

Total Graph Features Added:

```text
64 Node2Vec Embedding Features
```

---

## Baseline vs Graph-Enhanced Benchmark

| Metric              | Baseline XGBoost | Node2Vec + XGBoost |
| ------------------- | ---------------: | -----------------: |
| MAE                 |            5.399 |              5.177 |
| RMSE                |           21.858 |             21.272 |
| R²                  |         0.998669 |           0.998739 |
| Within 15% Accuracy |          99.535% |            99.610% |

### Result

The Node2Vec-enhanced model achieved measurable improvements across all evaluation metrics, demonstrating that logistics network topology provides useful information for ETA prediction.

---

# FTL vs Carting Decision Framework

A transportation strategy framework was developed to compare:

### Carting

* Local distribution
* Urban deliveries
* Last-mile operations

### FTL (Full Truck Load)

* Long-haul transport
* High-volume corridors
* Inter-city logistics

### Recommended Rules

| Condition            | Recommended Mode |
| -------------------- | ---------------- |
| Distance < 50 km     | Carting          |
| Distance > 150 km    | FTL              |
| High Volume Corridor | FTL              |
| Urban Distribution   | Carting          |
| Last Mile Delivery   | Carting          |

---

# Streamlit Dashboard

The interactive dashboard provides:

### Overview

* Logistics Network Summary
* Best Model Information

### Hub Analytics

* Top Source Hubs
* Top Destination Hubs

### Bottleneck Analytics

* Bottleneck Corridors
* Delay Analysis

### Network Analytics

* Degree Centrality
* Betweenness Centrality

### Model Performance

* ETA Prediction Model Comparison

### Graph Enhanced ETA

* Baseline vs Node2Vec Benchmark
* Graph Advantage Metrics

### Transportation Strategy

* FTL vs Carting Analysis
* Decision Framework

---

# Technologies Used

* Python
* Pandas
* NumPy
* Scikit-Learn
* XGBoost
* NetworkX
* Node2Vec
* Streamlit
* Matplotlib
* Plotly

---

# Key Outcomes

✅ Built a graph-aware logistics intelligence platform

✅ Predicted delivery ETAs using machine learning

✅ Identified critical network bottlenecks

✅ Developed FTL vs Carting decision framework

✅ Generated Node2Vec graph embeddings

✅ Demonstrated measurable graph advantage in ETA prediction

✅ Built an interactive Streamlit dashboard

---

## Authors

**Manideep, Sravya, Khushi**

Logistics Intelligence • Machine Learning • Network Analytics • Graph-Based ETA Prediction
