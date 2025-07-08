# Dynamic Pricing for Urban Parking Lots  
**Summer Analytics 2025 – Capstone Project**  
Hosted by: Consulting & Analytics Club × Pathway  

---

## Project Overview

Urban parking lots face inconsistent demand throughout the day. Static pricing leads to overcrowding during peak hours and underutilization during low demand.

This project presents a real-time dynamic pricing system for 14 urban parking spaces using data-driven logic and live simulation. The pricing engine is designed to respond intelligently to demand, traffic, and special conditions — with a focus on smooth and explainable pricing behavior.
---

## Objective

- Build a real-time pricing engine that adjusts prices based on:
  - Occupancy rate
  - Queue length
  - Traffic congestion level
  - Type of incoming vehicle
  - Special event or holiday indicators
- Begin with a base price of $10
- Ensure all price variations are:
  - Smooth
  - Bounded between $5 and $20
  - Justifiable and interpretable
- Visualize real-time pricing using interactive Bokeh plots

---

## Models Implemented

### Model 1: Linear Occupancy-Based Pricing

A simple reference model where prices increase proportionally with lot occupancy.

**Formula**:  
`Price_t+1 = Price_t + α × (Occupancy / Capacity)`

---

### Model 2: Demand-Based Pricing

A smarter model incorporating multiple real-time signals:

**Demand Function**:

Demand =
α × (Occupancy / Capacity) +
β × QueueLength -
γ × TrafficLevel +
δ × IsSpecialDay +
ε × VehicleTypeWeight

yaml
Copy
Edit

**Weights Used**:  
- α = 1  
- β = 1.5  
- γ = 0.8  
- δ = 2  
- ε = 1.2

**Final Price Calculation**:  
`Price = BasePrice × (1 + 0.5 × tanh(Demand / 10))`  
Prices are clipped to remain within [$5, $20].

---

## Dataset Summary

- 73 days of data across 14 parking spaces
- Sampled every 30 minutes (18 time points/day)
- Features:
  - Location: Latitude, Longitude
  - Capacity, Occupancy, QueueLength
  - VehicleType: car, bike, truck
  - TrafficConditionNearby
  - IsSpecialDay (binary)
  - Timestamps (LastUpdatedDate + Time)

---

## Technologies Used

| Tool           | Purpose                            |
|----------------|-------------------------------------|
| Pandas         | Data manipulation and preprocessing |
| NumPy          | Demand computation and normalization|
| Bokeh          | Interactive real-time price plotting|
| Panel          | Live embedding in Colab             |
| Pathway (logic)| Structured simulation architecture  |
| Google Colab   | Execution environment               |

---

## How It Works

1. Load and preprocess the dataset  
2. Encode categorical features (vehicle type, traffic)  
3. Initialize base price for each lot  
4. At each timestamp:
   - Calculate demand score using Model 2
   - Compute updated price using `tanh`-based logic
   - Stream the price into the live plot

---

## Visualization

The real-time pricing of one parking lot is visualized using Bokeh:

**Plot Title**: Real-Time Parking Price (Lot 1)  
- X-axis: Timestamps  
- Y-axis: Price ($)  
- Shows smooth, upward pricing trend as demand rises through the morning

A sample screenshot is provided in `plot.png`.

---

## Folder Structure

DynamicPricing/
├── dynamic_pricing.ipynb # Colab notebook with all code and output
├── final_report.pdf # Project report including all models and graphs
├── plot.png # Sample real-time Bokeh output
├── dataset.csv # Input dataset (if permitted to share)
└── README.md # Project summary

yaml
Copy
Edit

---

## Running the Project

1. Open the notebook in https://colab.research.google.com/drive/10ohP1_Vb248CljL_A-l8XCsDqHgpK0Kx?usp=sharing
2. Upload `dataset.csv` to the Colab session
3. Run all cells sequentially
4. Scroll to the final section to view the real-time price graph

---

## Results and Takeaways

- Pricing transitions are smooth and justifiable
- Real-time response to demand factors was successfully simulated
- Pricing remains bounded and interpretable at all times
- The system can be extended with competitive logic and rerouting

---
## Acknowledgements

This project was developed as part of the Summer Analytics 2025 capstone hosted by the Consulting & Analytics Club, in collaboration with Pathway.
You can connect me on linkedin : Rachitn24
